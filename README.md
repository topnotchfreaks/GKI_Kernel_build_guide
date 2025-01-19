Stuff to prepare:
1. VPS servers or use gitpod with free plan (need github account to create account on gitpod)
2. PC or laptop to build locally or to control the VPS


Local build:
- Use linux (ubuntu,debian or arch)
- At least 4 core/4 threads processor with 8GB ram (16 or more recommended)
- 20-50GB swap to speed up build
- Good stable Internet (at least 10mbps)
- 70GB storage (SSD recommended)


Build Guide:
1. Install repo and rsync 

    UBUNTU/DEBIAN:
    ```
    sudo apt update && sudo apt install repo rsync -y
    ```
    ARCH:
    ```
    sudo pacman -Sy
    ```
    ```
    sudo pacman -S rsync repo
    ```

3. Clone manifest repo using
    ```
    repo init -u https://github.com/topnotchfreaks/clo_kernel_manifest -b guide --depth=1 
    ```
    ```
    repo sync -j8
    ```
    ***Note: --depth=1 is used to save up storage. this is perfect if you just want to build and not changing anything.***

4. Open the kernel_platform directory
    ```
    cd kernel_platform
    ```

6. Build using
    ```
    LTO=thin BUILD_CONFIG=msm-kernel/build.config.gki.aarch64 build/build.sh > logs.txt
    ```
    ***Note: you can costumize LTO with thin or full. use full if you have beefy pc specs or good vps. > symbol is used to pipe the build logs to desired file. in this context is logs.txt (easier to notice error if theres some)***

7. Collect the Kernel "Image" file
    ```
    cd out/dist
    ```
    ***Note: Kernel files Usually named "Image" inside dist directory***

8. Import Image to anykernel3 zip and flash!!
