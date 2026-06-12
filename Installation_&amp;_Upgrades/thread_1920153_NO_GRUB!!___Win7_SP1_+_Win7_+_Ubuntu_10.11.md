---
title: "NO GRUB!!   Win7 SP1 + Win7 + Ubuntu 10.11"
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by xaos713 on 2012-02-04
**I need help!!** I have tried **everything** to solve it, but **nothing works!!**

I want to setup a system with **2x Win7** and **1x Ubuntu 10.11**, all x64.
I have **one HD** with **5 partitions**:

**sda:**

**sda1** - 100 MB - *PRIMARY* - reserved for **Windows Boot**, created by Windows
**sda2** - 120 GB - *PRIMARY* - **Windows 7 SP1**
**sda3** - 120 GB - *PRIMARY* - **Windows 7 w/o SP1**
**sda4** - EXTENDED
 ~ **sda5** - 025 GB - *LOGICAL* - **Ubuntu 10.11**
 ~ **sda6** - 006 GB - *LOGICAL* - **Swap**
 ~ **sda7** - 100 GB - *LOGICAL* - **/Home**

What I did was:
1. Installed **Win7** on **sda3**
2. Installed **Win7** on **sda2**
3. Installed **Ubuntu 10.11** on **sda5**

I've installed **GRUB2** on **sda2**.
When I boot there is **no GRUB**, only the **Windows Boot Manager**.

I've tried **Rescatux-CD** and **Super Grub2 Disk**. Rescatux doesn't start - all I get is the **unetbootin** menu. No matter what I select, there is a black screen for a sec and then I get back to the unetbootin menu.

Super Grub2 Disk starts, but when I select the option to reinstall GRUB (no matter if AUTO or MANUELLY) I get the prompt: "selectfile /grub/stage1 /boot/grub/stage1". I can imagine that means that I have to select wether I use a Linux boot partition or not, the problem is: I can't select anything, I can't type anything, in fact theres nothing I can do but reboot.

So I've reinstalled Ubuntu, this time selecting **sda1** for GRUB. And in fact there was GRUB after booting with one(!) "Windows (Loader)" at the end. Choosing this option: black screen and back to GRUB. Seems logical because sda1 is the Windows boot partition and by installing GRUB there, it overwrote the Windows loader.

So I recovered **MBA** and **root** with the Windows Install CD and got the Windows Boot Manager back. Obviously GRUB was gone, so I re-re-installed Ubuntu after deleting all partitions except sda1-3 for windows and creating sda3-7, whith GRUB on sda2. Again: Windows Boot Loader, **NO GRUB!!**


I need **2x Windows**, one with SP1 for Adobe, and one without SP1 for MS Robotics. And of course I want to use **Ubuntu** for the rest.


I am tired.

I am frustrated.

I don't know what to do anymore.


**PLEASE HELP ME!!**

---

### Post by darkod on 2012-02-04
Grub2 is not meant to be installed ON A PARTITION. By selecting sda5, sda1, etc, you are selecting the partitions, not the MBR of the disk.

The MBR of the disk is /dev/sda, without any number.

That's where you should install grub2.

Since you already have ubuntu installed, you don't need to do another install. But you might need to repair windows boot files if you still have grub installed on sds1. Windows doesn't like grub installed on its partition.

So, first repair any windows boot files that might be missing. Check if the computer boots fine giving you the windows bootloader with both options for your two win7 installs. Don't worry about ubuntu at this moment.

After you get win7 boot sorted out, and if your ubuntu root partition is still sda5, just boot with the ubuntu cd in live mode and in terminal do:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Note that in the mount command you use sda5 to mount the partition, but in the grub-install you use /dev/sda as the destination to install, the MBR.

That's it.

And for the future, you usually don't need any more tools except your ubuntu cd. Super Grub Disk can complicate things more, depending on your setup.

---

### Post by xaos713 on 2012-02-05
Thank you for the fast answer. Will do as you suggested and post the results later.

---

### Post by oldfred on 2012-02-06
If you want grub to have menu items for both Windows you have to install Windows separately. It normally moves the boot files from the first install to the second. Then in Windows you choose which Windows to boot. But since second install has no boot files grub cannot boot it directly. You may not have to reinstall, but move boot flag and repair each separately to make it bootable.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

