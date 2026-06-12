---
title: "Ubuntu 20.04 installation problem"
date: 2022-04-14
forum: Installation &amp; Upgrades
---

### Post by ibernato on 2022-04-14
Hi everyone,
i have an hp notebook with an CPU i7 6700HQ  and  GPU nvidia gtx 950m with 16GB RAM,
I created a bootable USB stick (GPT) with Rufus by installing Ubuntu 20.04.4 LTS.
On my notebook I have windows 10, but through gparted I have formatted the SSD. So now 500GB is unallocated and I have disabled secure boot.
To install ubuntu I had to enter acpi = off otherwise the installation process would crash suddenly [(see images)]("https://imgur.com/a/hemQhy1")[IMG]https://imgur.com/a/hemQhy1[/IMG]. Could it be that this setting causes problems? 
I proceed with the installation, but I always get a fatal error: the grub cannot be installed in dev/sda.
I tried to create partitions manually too: fat32 550MB and an ext4 /, but I always get the same error.
I tried to repair the grub with yannubuntu / boot-repair and I managed to boot the operating system, but there is a "systemd-journal" process that brings me the CPU to 95% and in 3h it wrote me 70GB of logs.

Any solution? 
[IMG]https://imgur.com/a/hemQhy1[/IMG]
Now I have reinstalled windows 10, therefore, the way I would like to follow is to install ubuntu alongside windows 10, but without all these problems

---

### Post by grahammechanical on 2022-04-14
A Windows 10 installation would need a EFI system partition (ESP) at the front the drive for Windows EFI boot files. The Ubuntu installer would put the Ubuntu EFI boot files in the same EFI partition as used by Windows. There will be no conflict.

My only drive is also SSD. It is not called sda or sd anything. Sata Drives are sda or sdb, etc. Older Solid State Drives (SSD) may be listed as sda, etc but modern SSD are Nonvolatile Memory Express (nmve) drives and are not seen as sda but nvme. 

The Ubuntu installer is programmed to install Grub in sda but we can change it. If your SSD is nvme then it will show up as nmve0 in the drop down list and the first partition will be nvme0p1.

So, the question is this: Is your SSD listed as sda or nvme0? Either way, I suggest telling the installer to install Grub not in sda but on the EFI system partition which might be sda1 or nvme0p1

Regards

---

### Post by ibernato on 2022-04-14
I have an SSD
I would have liked to have only Ubuntu as an operating system, but I just can't install the grub in my empty SSD (so without having windows). Did you by any chance see the image I linked?

---

