---
title: "How to upgrade kernel on a live Ubuntu 24.04.1 LTS system ?"
date: 2024-11-10
forum: Installation &amp; Upgrades
---

### Post by georgesgiralt on 2024-11-10
Hi Guys,
I'm making an USB stick with 24.04.1 LTS on it. 
To make it I used Rufus and made a persistent partition quite big (around 7 GB). As I plan to use this live system to repair/maintain  a lot of computers I will have access to, I installed some tools, made all the updates.
But the kernel is still set to the vmlinuz-6.8.0-41-generic  the iso was made with.
Of course, my casper-rw partition hold the new vmlinuz-6.8.0-48-generic kernel but I can't update/made the initramfs I need and copy them into the casper directory used for kernels when booting.
So I would be delighted to get all help and leads I can get to make this possible. 
Thank you very much for your help ! 

P.S. : I need the latest kernel in order to test/make work very recent computers which will benefit from these updates.
Edit : I forgot to tell you something... 
Previously, before Noble, I used the command live-update-initramfs to create the corresponding initramfs and it worked ... 
But now, it is not : 
```
root@ubuntu:~# live-update-initramfs --help
Command 'live-update-initramfs' not found, but can be installed with:
apt install live-tools
root@ubuntu:~# apt install live-tools
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Suggested packages:
  debian-installer-launcher
The following NEW packages will be installed:
  live-tools
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 0 B/26.3 kB of archives.
After this operation, 108 kB of additional disk space will be used.
(Reading database ... 261972 files and directories currently installed.)
Preparing to unpack .../live-tools_1%3a20190831.1_all.deb ...
dpkg-divert: error: 'diversion of /usr/sbin/update-initramfs to /usr/sbin/update-initramfs.orig.initramfs-tools by live-tools' clashes with 'local diversion of /usr/sbin/update-initramfs to /usr/sbin/update-initramfs.distrib'
dpkg: error processing archive /var/cache/apt/archives/live-tools_1%3a20190831.1_all.deb (--unpack):
 new live-tools package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/live-tools_1%3a20190831.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:~# 
```

---

### Post by tea for one on 2024-11-10
Here's an alternative to explore:-
> If you have installed additional kernels in the virtual environment, they will be listed on the Kernel Tab. You can chose to use one of these as the boot kernel for your new live ISO.
Full information here [https://github.com/PJ-Singh-001/Cubic](https://github.com/PJ-Singh-001/Cubic)

---

### Post by oldfred on 2024-11-10
Why not a full install to USB flash drive. Then you can add/update everything.
I have many USB flash drives, but now use an external SSD as so much faster and easier to use. Almost as fast as an internal SSD.

I started with  a USB to M.2 adapter for smaller M.2 SATA SSD that was in my desktop when I updated to a larger NVMe M.2 SSD. Worked so well, I do not plan purchase of any more flash drives as I already have many.

---

### Post by georgesgiralt on 2024-11-10
Thank you for your answer, Tea for One, but the proposed lead will help me make a *new* live ISO, not install a new kernel into my *live* installation (which is heavily modified post installation onto the USB stick). And as I plan to keep this usb stck for some time (at least for the duration of the LTS life, I will have to update kernel often during that period of time... 
Have a nice and bright day !

---

### Post by georgesgiralt on 2024-11-10
Well, OldFred, I used this approach (using, too, an M.2 SSD, SATA version ) but the live USB stick with it's persistent partition has the advantage of being very small and can be used as a "normal" USB stick when not at home because of it's vfat partition.... 
Can you teach a new trick to an old dog ? 
Thank you anyway.
P.S. : have you heard about "live-toram" which is part of the live-tools package and allows you to install the live system onto RAM and be free from the USB stick ?  I also forgot to add that a recent USB 3.2 16GB stick is reasonably fast and quite convenient to use. You should try it. 
Enjoy your day !

---

### Post by oldfred on 2024-11-11
Have not booted ISO from flash drive for a long time.
I use grub2's loopmount to directly boot ISO and have used the toram parameter. You just need enough RAM to support size of ISO.
I then have ISOs on almost all drives & external devices, along with full install on most. I do not think any still have standard Ubuntu as lighterweight flavors work better on smaller devices or low end systems.


I have 3 256GB flash drives and have noticed one is faster than others. But my desktop's USB ports all are USB 3.1.

And 2 128s, 3 64s, 4 32s, and even had full install on one of my 16GB. Lived near Microcenter store and behind counter were the flash drives. Just about could not get out of store without adding another flash drive as price lower or capacity higher.
Several older USB2, too small for much, but found I could fit rEFInd on my first flash drive that is only 256MB.

---

### Post by ubfan1 on 2024-11-11
If your live usb boots an ISO, I don't know an easy solution (respin?). But if the USB was created by extracting the ISO contents to a FAT filesystem (not the persistent fs, the root fs), you might be able to replace the vmlinuz and intrd with the new ones. However, I don't know what comes built into the supplied vmlinuz, so check (nm?) and compare to the proposed replacement.

---

### Post by georgesgiralt on 2024-11-11
Hello Ubfan1,
Previously, I used the live-update-initramfs to create the proper initramfs for the new installed kernel then I copied it and le kernel into the casper directory, at initrd and vmliuz respectively. Of course, as this partition is mounted readonly under /cdrom, I have to make it under another OS (preferably Linux in order to mount the casper-rw to get the file I need) to copy them. 
But, I need to make the initramfs under the live system otherwise the initramfs is unusable not having the proper paths and modules included... 
So I need the live-tools in the live system ;-)

---

### Post by tea for one on 2024-11-11
> **georgesgiralt said:**
> I'm making an USB stick with 24.04.1 LTS on it.
> **georgesgiralt said:**
> P.S. : I need the latest kernel in order to test/make work very recent computers which will benefit from these updates.
Just to offer another perspective.........
Instead of creating one USB stick with one ISO to provide universal repair options, how about one USB stick with multiple ISO images.
More flexibility guaranteed, even inc. Windows ISO.
[https://www.ventoy.net/en/doc_start.html](https://www.ventoy.net/en/doc_start.html)
Here is my list of ISO images
```
redact@gmktec:/media/redact/Ventoy$  ls
 boron-1-240123-amd64.hybrid.iso
 clonezilla-live-20240408-noble-amd64.iso
 efi-shell.img
 lubuntu-24.10-desktop-amd64.iso
 refind-flashdrive-0.14.0.2.img
 ubuntu-24.04.1-desktop-amd64.iso
 ubuntu-24.10-desktop-amd64.iso
 Win11_24H2_EnglishInternational_x64.iso
redact@gmktec:/media/redact/Ventoy$ 
```

---

### Post by georgesgiralt on 2024-11-11
Hi Tea For One,
My problem does not lie with other variant of Linux on a USB stick, it is to have a stick with the latest kernel available on it in order to try and check if this particular new hardware is/will be working under  a Linux brand (here Ubuntu). 
So whatever ISO I use, I will have to update the kernel or reinstall the new iso with the new kernel (if I create it using Cubic, for example), but this solution is a PITA because I also customise a lot my USB stick after I put the ISO onto it.

---

### Post by grahammechanical on 2024-11-12
I must be missing something.

Ubuntu 24.10 is using Linux 6.11 kernel. There is an ISO image for Ubuntu 24.10. There is not a newer kernel in Ubuntu. Linux kernel 6.12 is still a release candidate but progress has been delayed until December. So, even if someone was to use the methods used by those in the Development Version section of this forum to install release candidate kernels we would get a 6.12 kernel but it would be several days old and still underdeveloped.

[https://www.kernel.org/](https://www.kernel.org/)

[https://kernel.ubuntu.com/mainline/](https://kernel.ubuntu.com/mainline/)

It is a long list. Scroll down to the bottom. Linux 6.11 is the latest stable kernel from Ubuntu.

Edit: Another thought has occurred to me. If it is hardware compatibility that we are wanting to test then the Hardware Enablement Stack is important and its connection to the Linux Firmware package. It is the Linux Firmware package that contains the hardware drivers.

[https://launchpad.net/ubuntu/+source/linux-firmware](https://launchpad.net/ubuntu/+source/linux-firmware)

Regards

---

