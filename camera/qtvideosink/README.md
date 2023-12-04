# Camera-qtvideosink

## Platform setup

### Hardware requirements
- 1x AM62P SK EVM or AM62x SK EVM
- 1x OV5640 Camera (PCam or Technexion)
- 1x 32GB SD Card

### Setup

- Flash the SD Card with the latest tisdk-default-image using balena-etcher
- Add the following line to the uEnv.txt in the boot partition with the following
    - If using Technexion camera module
        ```sh
            name_overlays=k3-am62x-sk-csi2-tevi-ov5640.dtbo
        ```
    - If using Pcam camera module
        ```sh
            name_overlays=k3-am62x-sk-csi2-ov5640.dtbo
        ```
- Boot

## Setup host env
- Download and install AM62x or AM62P Linux SDK which provides QT libraries and cross compilation tools
[TI AM62x Processor SDK - 09.00](https://www.ti.com/tool/download/PROCESSOR-SDK-LINUX-AM62X)

- Source the environment-setup script
    ```sh
    source <linux-sdk>/linux-devkit/environment-setup
    ```

## Clone the app sources and build
```sh
git clone https://github.com/sskartheekadivi/qt-snippets.git
cd qt-snippets/camera/qtvideosink/

# Build
mkdir build ; cd build
qmake .. ; make
```

Copy the generated camera-qtvideosink binary to AM62x or AM62P and run by doing ..
```sh
<path-to-app>/camera-qtvideosink
```

