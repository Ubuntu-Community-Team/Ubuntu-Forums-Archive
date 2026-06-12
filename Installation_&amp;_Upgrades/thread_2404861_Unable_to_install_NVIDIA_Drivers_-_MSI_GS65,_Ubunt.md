---
title: "Unable to install NVIDIA Drivers - MSI GS65, Ubuntu 16.04"
date: 2018-10-29
forum: Installation &amp; Upgrades
---

### Post by cmr1094 on 2018-10-29
Trying to install NVIDIA drivers for a native Ubuntu 16.04.5 installation on a new MSI GS65 laptop (specs: Intel 8th-gen i7-8750H, 32GB RAM, NVIDIA GTX 1070). The NVIDIA drvers do not appear to be functioning, nor can I make use of the laptop's dedicated GPU. Details below:


First step I took after receiving the laptop was to wipe all Windows hardrive partitions using GParted. Went into BIOS, disabled Fast Boot and Secure Boot, as well as ensured booting into UEFI mode. Then booted to live Ubuntu 16.04 USB and proceeded with installation, which, despite a few minor hiccups, went fine (For anyone who reaches this page during an Ubuntu installation on the same or a similar machine: follow the solution here ([https://askubuntu.com/questions/861743/installation-of-ubuntu-16-04-from-a-usb-drive-freezes](https://askubuntu.com/questions/861743/installation-of-ubuntu-16-04-from-a-usb-drive-freezes)) to prevent hanging installation, as well as the solution here ([https://askubuntu.com/questions/1016903/alienware-17-r4-ubuntu-16-04-wifi-driver](https://askubuntu.com/questions/1016903/alienware-17-r4-ubuntu-16-04-wifi-driver)) to enable networking via the built-in network card). 


After installing Ubuntu I attempted to install Nvidia drivers. First used 


    ```
sudo add-apt-repository ppa:graphics-drivers
```




Followed by


    ```
sudo apt-get update
```




First tried a NVIDIA driver I've confirmed to be functional with another MSI laptop I recently configured, 384:


    ```
sudo apt-get install nvidia-384
```




The driver installation completed, but with some errors indicating possible missing firmware (more on that below). For now, I assumed NVIDIA installed correctly and rebooted.


Upon reboot, I tried running 


    ```
nvidia-settings
```




And am met with the following error message:


    ```
ERROR: Unable to load info from any available system
```




Tried running nvidia-smi -> command not found. Ran `lsmod | grep nvidia`, nothing (also nothing when ran `lsmod | grep nouveau`).  Tried opening NVIDIA XServer Settings from the GUI applications manager, no response. Prime-select, however, appeared to be installed. Running `sudo prime-select nvidia` produced 


```
    Info: the current GL alternatives in use are: ['mesa', 'nvidia-384-prime']
    Info: the current EGL alternatives in use are: ['mesa-egl', 'nvidia-384-prime']
    Info: selecting nvidia-384 for the nvidia profile
    update-alternatives: using /usr/lib/nvidia-384/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in manual mode
    update-alternatives: using /usr/lib/nvidia-384/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in manual mode
    update-alternatives: using /usr/lib/nvidia-384/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in manual mode
    update-alternatives: using /usr/lib/nvidia-384/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in manual mode
```




Then tried to run `glxgears` but was met with the following error message:


```
    X Error of failed request:  BadValue (integer parameter out of range for operation)
      Major opcode of failed request:  155 (GLX)
      Minor opcode of failed request:  3 (X_GLXCreateContext)
      Value in failed request:  0x0
      Serial number of failed request:  23
      Current serial number in output stream:  24
```




Running `sudo prime-select intel` produced


```
    Info: the current GL alternatives in use are: ['nvidia-384', 'nvidia-384']
    Info: the current EGL alternatives in use are: ['nvidia-384', 'nvidia-384']
    Info: selecting nvidia-384-prime for the intel profile
    update-alternatives: using /usr/lib/nvidia-384-prime/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in manual mode
    update-alternatives: using /usr/lib/nvidia-384-prime/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in manual mode
    update-alternatives: using /usr/lib/nvidia-384-prime/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in manual mode
    update-alternatives: using /usr/lib/nvidia-384-prime/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in manual mode
```




`glxgears` then ran successfully, without errors.


Upon reaching this point I looked back into the missing firmware warnings I mentioned earlier. After searching I found that someone else had also experienced the same issue here ([https://askubuntu.com/questions/832524/updated-kernel-to-4-8-now-missing-firmware-warnings](https://askubuntu.com/questions/832524/updated-kernel-to-4-8-now-missing-firmware-warnings)) and followed the steps provided to manually install the missing firmware. Uninstalled NVIDIA via `sudo apt-get purge nvidia*`, rebooted, reinstalled NVIDIA, and rebooted. Installation then continued without any warnings, but there was no change from what I had seen before.


I then considered updating the kernel. I installed UKUU and, after addressing the bug and solution explained here ([https://askubuntu.com/questions/1030043/unable-to-upgrade-kernel-after-4-16-3](https://askubuntu.com/questions/1030043/unable-to-upgrade-kernel-after-4-16-3)), installed the latest version kernel available, `4.18.15-041815-generic`. Rebooted, still no changes.


I then tried a few other NVIDIA drivers to see if there would be any difference. Uninstalled/rebooted following the procedure I described before, trying the latest driver, 410, as well as some earlier ones, such as 304, 340, 396, etc. All drivers produced the same results.


I'm out of ideas. Out of curiosity I tried wiping Ubuntu 16 and installing Ubuntu 18, however I wasn't able to proceed due to an error described by another here ([https://askubuntu.com/questions/789998/16-04-new-installation-gives-grub-efi-amd64-signed-failed-installation-target](https://askubuntu.com/questions/789998/16-04-new-installation-gives-grub-efi-amd64-signed-failed-installation-target)). Tried following the solution as well as other solutions from similar questions but wasn't successful with fixing the bug. However, having Ubuntu 16.04 installed on this laptop is a requirement, therefore I hadn't pursued Ubuntu 18 any further. 


Anyone have any suggestions?


For your info, output of some relevant commands is below:


lspci: 


```
    lspci -nnk


    00:00.0 Host bridge [0600]: Intel Corporation Device [8086:3ec4] (rev 07)
        DeviceName: Onboard - Other
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1227]
    00:01.0 PCI bridge [0604]: Intel Corporation Sky Lake PCIe Controller (x16) [8086:1901] (rev 07)
        Kernel driver in use: pcieport
    00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:3e9b]
        DeviceName: Onboard - Video
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1227]
        Kernel driver in use: i915
        Kernel modules: i915
    00:12.0 Signal processing controller [1180]: Intel Corporation Device [8086:a379] (rev 10)
        DeviceName: Onboard - Other
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1227]
        Kernel driver in use: intel_pch_thermal
        Kernel modules: intel_pch_thermal
    00:14.0 USB controller [0c03]: Intel Corporation Device [8086:a36d] (rev 10)
        DeviceName: Onboard - Other
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1227]
        Kernel driver in use: xhci_hcd
    00:14.2 RAM memory [0500]: Intel Corporation Device [8086:a36f] (rev 10)
        DeviceName: Onboard - Other
        Subsystem: Intel Corporation Device [8086:7270]
    00:14.3 Network controller [0280]: Intel Corporation Device [8086:a370] (rev 10)
        DeviceName: Onboard - Ethernet
        Subsystem: Bigfoot Networks, Inc. Device [1a56:1552]
        Kernel driver in use: iwlwifi
        Kernel modules: iwlwifi
    00:16.0 Communication controller [0780]: Intel Corporation Device [8086:a360] (rev 10)
        DeviceName: Onboard - Other
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1227]
        Kernel driver in use: mei_me
        Kernel modules: mei_me
    00:1b.0 PCI bridge [0604]: Intel Corporation Device [8086:a340] (rev f0)
        Kernel driver in use: pcieport
    00:1d.0 PCI bridge [0604]: Intel Corporation Device [8086:a330] (rev f0)
        Kernel driver in use: pcieport
    00:1d.4 PCI bridge [0604]: Intel Corporation Device [8086:a334] (rev f0)
        Kernel driver in use: pcieport
    00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:a30d] (rev 10)
        DeviceName: Onboard - Other
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1227]
    00:1f.3 Audio device [0403]: Intel Corporation Device [8086:a348] (rev 10)
        DeviceName: Onboard - Sound
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1227]
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
    00:1f.4 SMBus [0c05]: Intel Corporation Device [8086:a323] (rev 10)
        DeviceName: Onboard - Other
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1227]
        Kernel modules: i2c_i801
    00:1f.5 Serial bus controller [0c80]: Intel Corporation Device [8086:a324] (rev 10)
        DeviceName: Onboard - Other
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1227]
    01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1ba1] (rev a1)
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1227]
        Kernel modules: nvidiafb, nouveau
    3b:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd Device [144d:a808]
        Subsystem: Samsung Electronics Co Ltd Device [144d:a801]
        Kernel driver in use: nvme
    3c:00.0 Ethernet controller [0200]: Qualcomm Atheros Device [1969:e0b1] (rev 10)
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1227]
        Kernel driver in use: alx
        Kernel modules: alx
```




lshw:


```
    sudo lshw -c display


      *-display UNCLAIMED     
           description: VGA compatible controller
           product: NVIDIA Corporation
           vendor: NVIDIA Corporation
           physical id: 0
           bus info: pci@0000:01:00.0
           version: a1
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress vga_controller bus_master cap_list
           configuration: latency=0
           resources: memory:ac000000-acffffff memory:80000000-8fffffff memory:90000000-91ffffff ioport:4000(size=128) memory:ad000000-ad07ffff
      *-display
           description: VGA compatible controller
           product: Intel Corporation
           vendor: Intel Corporation
           physical id: 2
           bus info: pci@0000:00:02.0
           version: 00
           width: 64 bits
           clock: 33MHz
           capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
           configuration: driver=i915 latency=0
           resources: irq:23 memory:ab000000-abffffff memory:40000000-4fffffff ioport:5000(size=64) memory:c0000-dffff
```

---

