---
title: "apt upgrade breaks the nvidia drivers"
date: 2021-02-15
forum: Installation &amp; Upgrades
---

### Post by vincentberenz on 2021-02-15
Hi all

After a fresh installation of ubuntu 20.04, the nvidia drivers are installed and are working fine, i.e. nvidia-smi prints:

    NVIDIA-SMI 460.32.03    Driver Version: 460.32.03    CUDA Version: 11.2

(note: I did not install the nvidia drivers. ubuntu installer seems to have done it itself).

460 seems to be indeed the recommended drivers (according to nvidia-detector).

After calling

    apt update
    apt upgrade

and rebooting, nvidia-smi fails:

    NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

Reinstalling the nvidia drivers did not help. I tried several versions.

What would be the best way to handle this ? Should I "configure" apt upgrade to never upgrade nvidia drivers ? (if such a thing can be done)


---

update:

I reinstalled, this time 18.04. The drivers were not installed at startup.
After installation, I installed (with aptitude) the drivers 460 and rebooted. 

The same error occured when calling nvidia-smi:
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

I uninstalled the drivers and installed version 430 (version selected randomly, I confess). Same result after reboot.

---

### Post by grahammechanical on 2021-02-15
When we install Ubuntu and tick the box to install third part software then third party video drivers are installed. That is how you got the Nvidia drivers in the first place along with Nvidia System Management Interface (nvidia-smi)

[https://developer.nvidia.com/nvidia-system-management-interface](https://developer.nvidia.com/nvidia-system-management-interface)

I am guessing that it is separate from the Nvidia driver which should still be working. The documentation for nvidia-smi is very long. It may contain a command for reinstalling nvidia-smi or resetting it.

[http://developer.download.nvidia.com/compute/DCGM/docs/nvidia-smi-367.38.pdf](http://developer.download.nvidia.com/compute/DCGM/docs/nvidia-smi-367.38.pdf)

Regards

---

### Post by mIk3_08 on 2021-02-15
[Click Here]("https://www.itzgeek.com/post/how-to-install-nvidia-drivers-on-ubuntu-20-04-ubuntu-18-04.html") it might help you.

---

