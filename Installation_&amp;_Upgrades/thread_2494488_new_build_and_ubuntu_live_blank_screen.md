---
title: "new build and ubuntu live blank screen"
date: 2024-01-18
forum: Installation &amp; Upgrades
---

### Post by wolfyy on 2024-01-18
I have a new build:
seasonic focus gold 550W PSU
ASUS tuf gaming A520M plus II MB
ryzen 5 4500
corsair vengeance LPX 2x16GB DDR4
and nvidia 980 GTX


and the system does not work. MB bios is the latest version, when i try to run ubuntu 23.10 live all it shows is blank screen in both modes.

i tried it this way:
Some computer's hardware may have problems with some of the Desktop drivers. You can fix this by typing e at the Try Ubuntu without installing option from the initial black screen menu. Then replace the words quiet splash with nomodeset. Then hit F10 to boot.

and i get back: 
Booting a command list
EFI stub: loaded initrd from linux_efi_initrd_media_guid device path
EFI stub: measured initrd data into PCR 9
EFI Stub: uefi secure boot is enabled


i tried to disable secure boot but also no luck.

---

### Post by ajgreeny on 2024-01-18
I have never used an nvidia graphic card  but I think that is an old model and I wonder if there is an nvidia driver for it any more as I believe older cards are no longer supported by nvidia though may still work using the OS  nouveau driver.

To difficult to search on a small Android screen and keyboard so I'll leave it with you.

---

### Post by wolfyy on 2024-01-18
i think i did everything correct but also chainging to nouveau did not work, i get the same error,

so most probably the problem is in graphic card?

---

### Post by #&amp;thj^% on 2024-01-18
I see that card working with driver-460
```
apt list nvidia* | grep 460

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

nvidia-compute-utils-450/noble 460.91.03-0ubuntu1 amd64
nvidia-compute-utils-455/noble 460.91.03-0ubuntu1 amd64
nvidia-compute-utils-460-server/noble 470.223.02-0ubuntu1 amd64
nvidia-compute-utils-460/noble 470.223.02-0ubuntu1 amd64
nvidia-dkms-450/noble 460.91.03-0ubuntu1 amd64
nvidia-dkms-455/noble 460.91.03-0ubuntu1 amd64
nvidia-dkms-460-server/noble 470.223.02-0ubuntu1 amd64
nvidia-dkms-460/noble 470.223.02-0ubuntu1 amd64
nvidia-driver-450/noble 460.91.03-0ubuntu1 amd64
nvidia-driver-455/noble 460.91.03-0ubuntu1 amd64
nvidia-driver-460-server/noble 470.223.02-0ubuntu1 amd64
nvidia-driver-460/noble 470.223.02-0ubuntu1 amd64
nvidia-fabricmanager-460/noble 470.223.02-0ubuntu1 amd64
nvidia-fabricmanager-dev-460/noble 470.223.02-0ubuntu1 amd64
nvidia-headless-450/noble 460.91.03-0ubuntu1 amd64
nvidia-headless-455/noble 460.91.03-0ubuntu1 amd64
nvidia-headless-460-server/noble 470.223.02-0ubuntu1 amd64
nvidia-headless-460/noble 470.223.02-0ubuntu1 amd64
nvidia-headless-no-dkms-450/noble 460.91.03-0ubuntu1 amd64
nvidia-headless-no-dkms-455/noble 460.91.03-0ubuntu1 amd64
nvidia-headless-no-dkms-460-server/noble 470.223.02-0ubuntu1 amd64
nvidia-headless-no-dkms-460/noble 470.223.02-0ubuntu1 amd64
nvidia-kernel-common-450/noble 460.91.03-0ubuntu1 amd64
nvidia-kernel-common-455/noble 460.91.03-0ubuntu1 amd64
nvidia-kernel-common-460-server/noble 470.223.02-0ubuntu1 amd64
nvidia-kernel-common-460/noble 470.223.02-0ubuntu1 amd64
nvidia-kernel-source-450/noble 460.91.03-0ubuntu1 amd64
nvidia-kernel-source-455/noble 460.91.03-0ubuntu1 amd64
nvidia-kernel-source-460-server/noble 470.223.02-0ubuntu1 amd64
nvidia-kernel-source-460/noble 470.223.02-0ubuntu1 amd64
nvidia-utils-450/noble 460.91.03-0ubuntu1 amd64
nvidia-utils-455/noble 460.91.03-0ubuntu1 amd64
nvidia-utils-460-server/noble 470.223.02-0ubuntu1 amd64
nvidia-utils-460/noble 470.223.02-0ubuntu1 amd64

```
Probably a bit better with the PPA 
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
```

EDIT Also are you trying to boot with nvidia card connected? If you have a CPU with Video as well pugin in to that first.

---

### Post by oldfred on 2024-01-18
Are you able to boot to recovery mode? It defaults to nomodeset.
But if only one install, you have to press escape key right after UEFI/BIOS screen to get grub menu.

Once you install nVidia driver from Ubuntu's repository you must not use nomodeset or you get conflicts.
And if you change nVidia driver's you have to purge old one before install of new one.

Install instructions
[https://ubuntu.com/server/docs/nvidia-drivers-installation](https://ubuntu.com/server/docs/nvidia-drivers-installation)
Ubuntu 22.04 LTS Changes Default For NVIDIA Driver Back To Using X.Org Rather Than Wayland
[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-22.04-NVIDIA-XOrg-Back](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-22.04-NVIDIA-XOrg-Back)

When you booted live installer, did it not work?
And then you have to choose Safe Graphics to get it to work and as part of install choose to install the restricted extras to get the correct proprietary nVidia driver installed as part of install.

---

### Post by MAFoElffen on 2024-01-18
I see that supported by NVidia 535.154.05: [http://us.download.nvidia.com/XFree86/Linux-x86_64/535.154.05/README/supportedchips.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/535.154.05/README/supportedchips.html) (halfway down the list...)

Then: [https://www.asus.com/support/FAQ/1049829/](https://www.asus.com/support/FAQ/1049829/)

---

