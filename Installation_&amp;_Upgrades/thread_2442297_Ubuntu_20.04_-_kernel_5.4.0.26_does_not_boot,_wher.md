---
title: "Ubuntu 20.04 - kernel 5.4.0.26 does not boot, whereas 5.0.0.23 boots successfuly"
date: 2020-05-02
forum: Installation &amp; Upgrades
---

### Post by santhoshjudej on 2020-05-02
Hello all,

I recently upgraded to Ubuntu 20.04 from Ubuntu 18.04. 
But the new kernel 5.4.0.26 does not boot. It gets stuck on loading initramfs.

The old kernel 5.0.0.23 boots normally. 
I have searched a lot of forums for solutions but none seem to work for me. 
I am running Dell Inspiron 15 series with AMD A9 processor.  

Any help is greatly appreciated.

---

### Post by Impavidus on 2020-05-02
I'm not sure where to start troubleshooting this, but there are a few things that strike me as odd.

The upgrade from 18.04 to 20.04 will be opened in late July or early August, so you ran an experimental upgrade. OK, many people do and usually it works.

Kernel 5.0 is old. Ubuntu 18.04 should use either kernel 4.15 or 5.3. 5.0 was the kernel belonging to Ubuntu 19.04 and was used in Ubuntu 18.04.3, but should have upgraded automatically to 5.3 in January. 5.0.0-23 wasn't even the last 5.0 kernel released for 18.04. You can only release-upgrade an Ubuntu system when it's fully upgraded (but that doesn't require you to remove the 5.0 kernel), so this tells me you had some problems with your 18.04 system before the upgrade.

A few questions that might help:
Can you boot a 20.04 live disk? Which kernels have you installed?```
dpkg --list | grep linux-image
ls /boot
```

It's best not to release-upgrade a damaged system. It makes problems worse. Fresh installs solve problems. Fixing an upgrade gone wrong is usually not worth the effort. Better to fresh install. Fresh install means booting a live disk, which will use the 5.4 kernel.

---

### Post by santhoshjudej on 2020-05-02
Thanks Impavidus for your reply

> so this tells me you had some problems with your 18.04 system before the upgrade.

You're right about this. After a kernel update in 18.04 system, the same issue started happening. So i had to go back to 5.0 which was working fine on 18.04 and recently I upgraded to 

> "Which kernels have you installed?

The output of the dpkg --list | grep linux-image

```
ii  linux-image-5.0.0-23-generic                  5.0.0-23.24~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.3.0-19-generic                  5.3.0-19.20~18.04.2+2                      amd64        Signed kernel image generic
rc  linux-image-5.3.0-26-generic                  5.3.0-26.28~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.3.0-28-generic                  5.3.0-28.30~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.3.0-40-generic                  5.3.0-40.32~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.3.0-42-generic                  5.3.0-42.34~18.04.1                        amd64        Signed kernel image generic
ii  linux-image-5.4.0-26-generic                  5.4.0-26.30                                amd64        Signed kernel image generic
ii  linux-image-5.4.0-28-generic                  5.4.0-28.32                                amd64        Signed kernel image generic
ii  linux-image-generic                           5.4.0.28.33                                amd64        Generic Linux kernel image
rc  linux-image-unsigned-5.3.0-42-generic         5.3.0-42.34~18.04.1                        amd64        Linux kernel image for version 5.3.0 on 64 bit x86 SMP

```

and ls /boot

```
-rw-r--r-- 1 root root   224446 Jul 29  2019 config-5.0.0-23-generic
-rw-r--r-- 1 root root   237718 Apr 20 22:03 config-5.4.0-26-generic
-rw-r--r-- 1 root root   237718 Apr 22 19:38 config-5.4.0-28-generic
drwx------ 5 root root     4096 Jan  1  1970 efi
drwxr-xr-x 5 root root     4096 May  2 09:42 grub
lrwxrwxrwx 1 root root       27 May  2 08:51 initrd.img -> initrd.img-5.4.0-28-generic
-rw-r--r-- 1 root root 42302114 Apr 24 02:41 initrd.img-5.0.0-23-generic
-rw-r--r-- 1 root root 46464717 May  2 09:41 initrd.img-5.4.0-26-generic
-rw-r--r-- 1 root root 46464719 May  2 09:39 initrd.img-5.4.0-28-generic
lrwxrwxrwx 1 root root       27 May  2 08:51 initrd.img.old -> initrd.img-5.4.0-26-generic
-rw-r--r-- 1 root root   182704 Feb 14 04:39 memtest86+.bin
-rw-r--r-- 1 root root   184380 Feb 14 04:39 memtest86+.elf
-rw-r--r-- 1 root root   184884 Feb 14 04:39 memtest86+_multiboot.bin
-rw------- 1 root root  4289273 Jul 29  2019 System.map-5.0.0-23-generic
-rw------- 1 root root  4736015 Apr 20 22:03 System.map-5.4.0-26-generic
-rw------- 1 root root  4736015 Apr 22 19:38 System.map-5.4.0-28-generic
lrwxrwxrwx 1 root root       24 May  2 08:51 vmlinuz -> vmlinuz-5.4.0-28-generic
-rw-r--r-- 1 root root  8707832 Mar 23 19:32 vmlinuz-5.0.0-23-generic
-rw------- 1 root root 11657976 Apr 20 22:11 vmlinuz-5.4.0-26-generic
-rw------- 1 root root 11657976 Apr 22 20:13 vmlinuz-5.4.0-28-generic
lrwxrwxrwx 1 root root       24 May  2 08:51 vmlinuz.old -> vmlinuz-5.4.0-26-generic
```

I am able to run 20.04 live from my pen drive.

Everything works normally in the live session.

> Fixing an upgrade gone wrong is usually not worth the effort. Better to  fresh install. Fresh install means booting a live disk, which will use  the 5.4 kernel.                 

I understand what you say. If you recommend a fresh install I will go ahead with that. I used Synaptic Package Manager to install apps. Is there a way to save a list of all the apps installed presently and install them directly after the fresh install of 20.04. 

I really appreciate your help.

---

### Post by jihantoro on 2020-05-02
bro, i really had same problem like yours, mine DELL INSPIRON 17, another person with DELL Laptop had same problem too : 

- [https://www.dell.com/community/Linux-Developer-Systems/Dell-OEM-support-ubuntu-20-04-lts/td-p/7503684](https://www.dell.com/community/Linux-Developer-Systems/Dell-OEM-support-ubuntu-20-04-lts/td-p/7503684)
- [https://askubuntu.com/questions/1234480/fresh-ubuntu-20-04-installation-wont-boot-after-grub-and-stuck-in-boot-loop](https://askubuntu.com/questions/1234480/fresh-ubuntu-20-04-installation-wont-boot-after-grub-and-stuck-in-boot-loop)

---

### Post by Impavidus on 2020-05-03
> **santhoshjudej said:**
> 
I understand what you say. If you recommend a fresh install I will go ahead with that. I used Synaptic Package Manager to install apps. Is there a way to save a list of all the apps installed presently and install them directly after the fresh install of 20.04. 


There is, see this post by TheFu: [https://ubuntuforums.org/showthread.php?t=2436821&p=13932360#post13932360](https://ubuntuforums.org/showthread.php?t=2436821&p=13932360#post13932360)
In short, to create the list of manually installed packages and save it in a file named "apt-mark.manual":```
apt-mark showmanual >apt-mark.manual
```
To use this list to install the packages after installing the OS:```
sudo apt-mark manual $(cat apt-mark.manual)
sudo apt-get -u dselect-upgrade
```

It would be nice to know what actually went wrong, but as you can run the livedisk it appears that the 5.4 kernel does work on your hardware. For some reason, something went wrong when installing any kernel past 5.0

---

### Post by santhoshjudej on 2020-05-04
Hello Impavidus. 

I did a clean install of Ubuntu 20.04 from a live USB.

But the USB was not booting from UEFI mode but only from the Legacy mode. Therefore 'Try Ubuntu without installing' and 'Install Ubuntu' options also came up only in the Legacy mode. I didn't realize this, when I mentioned to you that the Live USB works. IT WORKS ONLY FROM LEGACY MODE NOT UEFI

But I have windows 10 with a UEFI boot manager and after I installed Ubuntu 20.04 from the Legacy settings, it was not displaying the usual grub menu, but was displaying a 'grub' command prompt. 

However, Ubuntu 20.04 has been installed properly and boots normally when I change the setting in BIOS to Legacy.
And Windows 10 boots normally when I change the setting in BIOS to UEFI

So I had UEFI Windows and Legacy Ubuntu.

I have updated the BIOS to the latest version available for my system.
I used Rufus 3.10 from windows 10 to create the Ubuntu 20.04 bootable media. I explicitly set GPT partition table and UEFI for the live usb.

But the live usb of 20.04 won't boot in the UEFI mode at all. I tried the options given suggested, like turning off 'FASTBOOT' turning of 'SecureBoot' but nothing helps.

Just to check, I created a live usb of ubuntu 18.04.3 that I had with GPT partition table and UEFI using Rufus 3.10. 
This live usb booted from UEFI settings and I made a fresh install of 18.04 again. 
This displays the grub menu on boot and shows the Windows option too.

By the way, the kernel is 5.0.0.23 in this install.

```
santhosh@santhosh-dell:~$ uname -r
5.0.0-23-generic

```

and 

```

santhosh@santhosh-dell:~$ ls -l /boot
total 52748
-rw-r--r-- 1 root root   224446 Jul 29  2019 config-5.0.0-23-generic
drwx------ 5 root root     4096 Jan  1  1970 efi
drwxr-xr-x 5 root root     4096 May  4 09:42 grub
-rw-r--r-- 1 root root 40210466 May  4 09:46 initrd.img-5.0.0-23-generic
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw------- 1 root root  4289273 Jul 29  2019 System.map-5.0.0-23-generic
-rw-r--r-- 1 root root  8707832 May  4 09:24 vmlinuz-5.0.0-23-generic

```

 This is a fresh install of 18.04. 

So I am guessing that since both Live usb of 20.04 and the upgraded 18.04 to 20.04 both with kernel 5.4x are not booting, it could be related to the UEFI settings of my computer. Can you help me resolve this? I would really like to have a fresh 20.04 installed in UEFI alongside my windows 10. As I mentioned earlier, my BIOS is the latest version for my system.

I thank you in advance for your time and help.

---

### Post by Impavidus on 2020-05-04
All your output makes sense, except that I've got no idea why kernel 5.0 boots fine in UEFI mode, but 5.3 and later only boot in legacy mode. The only thing that seems logical is secure boot settings, but you tried that. I hope somebody has a different suggestion.

In the meantime, Ubuntu 18.04 with the 4.15 kernel is still supported.

---

### Post by jjj-9819-jjj on 2020-05-04
[https://ubuntuforums.org/showthread.php?t=2442511](https://ubuntuforums.org/showthread.php?t=2442511) may help.

---

### Post by CelticWarrior on 2020-05-04
> **jjj-9819-jjj said:**
> [https://ubuntuforums.org/showthread.php?t=2442511](https://ubuntuforums.org/showthread.php?t=2442511) may help.

No, it doesn't help. It has nothing to do with this situation.
I explained what you need to know in your own thread.

---

### Post by ActionParsnip on 2020-05-04
[code]
sudo dpkg -P `dpkg --list | grep linux-image | grep ^rc | awk {'print $2'}`

Should clean up the ones starting with "rc" which have been removed but have residual configs on the system

---

### Post by santhoshjudej on 2020-05-05
Now I have installed 18.04 fresh. So there is only kernel 5.0.0.23 and nothing else

---

### Post by Impavidus on 2020-05-05
Kernel 5.0 is no longer supported. Maybe you can downgrade to kernel 4.15 by installing the package linux-generic. Use the grub menu to boot the 4.15 kernel. If it works, you can remove linux-generic-hwe-18.04 and autoremove, so that the 5.0 kernel is gone and you don't get the 5.3 kernels any more when installing updates. Of course, this won't help you get on 20.04, but at least it will get you a working and supported kernel (assuming that 4.15 works).

I understand that when you upgraded your kernel to 5.3 (Ubuntu 18.04.4) or 5.4 (Ubuntu 20.04) in UEFI mode, booting got stuck on loading unitramfs. And when you tried booting the 20.04 live disk in UEFI mode, it got stuck even before that, as you didn't see the grub menu with "Try without installing" and "Install Ubuntu". So that may be a separate issue. And in legacy mode everything works. Sometimes it helps if you use a different tool to create the live disk. I've had most success creating live usbs on Ubuntu using [mkusb]("https://help.ubuntu.com/community/mkusb"), creating a live-only disk, no persistence.

It would help if you can find any more information on why you can't boot the 5.4 kernel in UEFI mode, if you want to create a bug report that's of any use to the devs. Detailed hardware info would help too.

---

