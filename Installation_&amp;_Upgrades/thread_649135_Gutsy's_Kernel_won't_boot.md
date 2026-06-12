---
title: "Gutsy's Kernel won't boot"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by amitabhishek on 2007-12-24
I have just installed Gutsy on my brand new Acer aspire 4520 laptop. The problem now is the kernel won't boot. It just gets struck up at the splash screen.

There was a solution here.

[http://ubuntuforums.org/showthread.php?t=282956](http://ubuntuforums.org/showthread.php?t=282956) & 
[http://www.ubuntugeek.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html](http://www.ubuntugeek.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html)

But how do I "Sudo" when the system doesn't even boot!!! Here these guys used i386 kernel to boot and issue commands. But Gutsy doesn't probably give such an option. There is only 2.6.22-14-generic & 2.6.22-14 recovery.

Kindly help!

---

### Post by tgilber1 on 2007-12-24
> **amitabhishek said:**
> I have just installed Gutsy on my brand new Acer aspire 4520 laptop. The problem now is the kernel won't boot. It just gets struck up at the splash screen.

There was a solution here.

[http://ubuntuforums.org/showthread.php?t=282956](http://ubuntuforums.org/showthread.php?t=282956) & 
[http://www.ubuntugeek.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html](http://www.ubuntugeek.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html)

But how do I "Sudo" when the system doesn't even boot!!! Here these guys used i386 kernel to boot and issue commands. But Gutsy doesn't probably give such an option. There is only 2.6.22-14-generic & 2.6.22-14 recovery.

Kindly help!

When booting the computer, a GRUB menu should appear, i.e., Hit ESC to access menu.  After pressing the ESC key, choose the recovery option of one of kernel choices.  Watch for any error messages while booting.  Hopefully, you will be able to get to the command prompt as root user.  Once you're at the root prompt, type the desired commands without the sudo, since you're logged in as root.  After fixing the problem, type exit to continue boot up to gdm.

If you get any error messages, which prevent the PC from booting up, post them here.

---

### Post by amitabhishek on 2007-12-25
sorry bro! Problem continues...

Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/827cbda3-51a0-4e5d-a399-a90cef8c5514 does not exist. Dropping to a shell !

Busybox v1 .1 .3 (Debian....)

(initramfs)_


I don't know what the heck it means...
my kernel version is 2.6.22-14-generic

---

### Post by tgilber1 on 2007-12-25
> **amitabhishek said:**
> sorry bro! Problem continues...

Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/827cbda3-51a0-4e5d-a399-a90cef8c5514 does not exist. Dropping to a shell !

Busybox v1 .1 .3 (Debian....)

(initramfs)_


I don't know what the heck it means...
my kernel version is 2.6.22-14-generic

There are different ways to call a disk during bootup, 

by directly by device (e.g., /dev/sda1)

by label (e.g., SATA-1),

by UUID (Unique Universal Identifcation - randomly generated alpha-numeric string using tune2fs)

I have been hosed with the UUID a couple of times with Ubuntu after upgrading the kernel.  I had to regenerate the UUID again to get everything to work.  However, you can boot directly to see if UUID is causing the problem.

Check to see which hard drive device and root partition your booting, i.e., the root or / directory

1.  sudo fdisk -l  # to learn device naming on linux box
2.  sudo tune2fs -l /dev/<device name> (e.g., sudo tune2fs -l /dev/sda1)  # careful with this command - can be a destructive command - check out "man tune2fs"
3.  After finding out where the root partition lies, check and make changes, if necessary to the /etc/fstab and /boot/grub/menu.lst.

With the /etc/fstab - example below has the three ways to call a disk in the fstab, label, directly via device path, and UUID.  # sign comments out line so fstab will ignore

_fstab example_
# Entry for /dev/sda2 :
#LABEL=ROOT / ext3 defaults 0 2
/dev/sda2 / ext3 defaults 0 2 
#UUID=41b5f2b5-1eb5-4436-9511-62faf14f0501 / ext3 defaults 0 2



_Excerpt from /boot/grub/menu.lst - This file is called during boot up_

NOTE:  change the root=/dev/<device path> on the kernel line, ex.  root=/dev/sda2

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/sda2 ro single
initrd          /initrd.img-2.6.22-14-generic

Lastly, the files may already be set to device path.  However, from your error message, it looks like your system is searching for the bootup disk with root partition via UUID.  Below are a couple of forums that suggest other solutions that I have not verified.

[https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256](https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256)
[http://www.linuxforums.org/forum/ubuntu-help/97726-boot-problems.html](http://www.linuxforums.org/forum/ubuntu-help/97726-boot-problems.html)

---

### Post by amitabhishek on 2007-12-25
Thanks for your help but bro tell me one basic thing. I get only basic shell prompt (busybox), is it possible to issue sudo commands?

---

### Post by tgilber1 on 2007-12-25
Restart and boot up to the Ubuntu installation disc

Select "Rescue Broken System"

Answer all the window prompts, e.g., language, keyboard type, etc.

It should eventually let you choose the root disk to boot to.  Hopefully, you should be able to get to a prompt and try some of the suggestions in my previous posts.  If you get to the prompt rather than a GUI, then you may have to remount to be able to write to the disks.  Check for remounting disc and rescue broken system howto.

---

### Post by amitabhishek on 2007-12-26
Thanks! will try it and post you accordingly.

---

### Post by 64mgb on 2007-12-27
I have a very similar problem after upgrading from Feisty to Gutsy.  I can boot into Gutsy using the 2.6.20 kernel from Feisty, but it hangs when booting using the 2.6.22 kernel.  When I boot using recovery mode, I see the same message described here...ALERT!  /dev/disk/by-uuid/xxxxxx  does not exist.

The difference is, when I look into /dev/disk there is no by-uuid folder...just a by-path folder.  What can be causing this, and how do I fix it?  When I use recovery mode with the 2.6.20 kernel and look into /dev/disk there is a by-uuid folder.

Thanks for any help.

Rich

---

### Post by 64mgb on 2007-12-27
> **64mgb said:**
> I have a very similar problem after upgrading from Feisty to Gutsy.  I can boot into Gutsy using the 2.6.20 kernel from Feisty, but it hangs when booting using the 2.6.22 kernel.  When I boot using recovery mode, I see the same message described here...ALERT!  /dev/disk/by-uuid/xxxxxx  does not exist.

The difference is, when I look into /dev/disk there is no by-uuid folder...just a by-path folder.  What can be causing this, and how do I fix it?  When I use recovery mode with the 2.6.20 kernel and look into /dev/disk there is a by-uuid folder.

Thanks for any help.

Rich

Just a little more info on my situation.  This system originally had Feisty on it and I tried to upgrade to Gutsy.  After the upgrade I couldn't boot, so I just started from scratch...wiped it out and started over.  I had to load Feisty, upgrade to Gutsy, and set the default to boot on the 2.6.20 kernel, because the Gutsy live CD would not recognize that I had a hard drive installed.  I tried both the live CD and the alternate CD.

Rich

---

### Post by 64mgb on 2007-12-27
OK...I think I finally got this resolved...I've been working on this off and on for a LONG time.  I finally decided it was something in the master boot record of the drive.  It's a Maxtor 120GB IDE drive.  I fired up my Ultimate Boot CD for Windows and ran a couple of utilities on it to erase the disk, and erase the MBR.  Lo and behold, when I inserted the 7.10 Live CD, it was finally able to see my hard drive.

It's installing 7.10 right now...I'll post again with the results of that.

Rich

---

### Post by 64mgb on 2007-12-27
Success!   It's all good now.  What a relief.

Rich

---

### Post by ImALittleTeaPot on 2007-12-28
Similar problems:[http://ubuntuforums.org/showthread.php?p=4027373#post4027373](http://ubuntuforums.org/showthread.php?p=4027373#post4027373)

how exactly did you erase the Mast Boot Record..if you don't mind telling me.

---

### Post by 64mgb on 2007-12-28
The Ultimate Boot CD for Windows has a couple of utilities for tinkering with partitions and MBRs.  I think the one I used was called MBRFix.

Rich

---

### Post by amitabhishek on 2007-12-29
Thanks a ton tgilber! My system working like an F1 car now:)

---

### Post by SameerAcharya on 2008-02-14
Hi guys,

I have had the same problem with Ubuntu 7.10 installation on Acer 4520. Iam a new user of Ubuntu. 

The installation went smooth (in safe graphics mode), but when I tried booting from the hard disk the OS just couldnt see the hard disk. It was frustrating and I spent a lot of time on it. 

Ubuntu 6.06 installation went very well and would boot properly but this couldnt see my wired network card.

I tried all options I saw on the net including changing the command line to specify root as sda1 etc, nothing worked.

The only thing worked for me was mentioning in the command parameters as** all_generic_ide**

Now Iam going to try and configure my system for sound and nvidia driver for GeForce 7000, hope it works.

---

### Post by maestrobwh1 on 2008-02-23
This has happened to me every time something regarding a kernel upgrades on my Acer Aspire notebook 3005 Lci, so I have been working with an old kernel version and just unmark any kernel items when I upgrade.  I am wondering... if I change my grub lines from root=uuid= to root=dev/sda2 (the root partition)  after upgrading but before rebooting, should this solve the problem? Or is there something inherent in the kernel itself that is looking for the uuid?

---

