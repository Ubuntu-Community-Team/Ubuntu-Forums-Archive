---
title: "Recovering Ubuntu after Windows installation"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by jet-san on 2010-08-22
Hello

I have just reinstalled my Win XP and cannot run Ubuntu.
I found few ([1]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"),[2]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/"),[3]("http://shibuvarkala.blogspot.com/2009/07/howto-restore-ubuntu-after-windows.html")) pages with help about GRUB list.
First I tried number 2 & 3 (very short), but it did not work at all.
When I am trying to fix it using instructions from help.ubuntu.com I have one error.

```
ubuntu@ubuntu:~$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)
```
I was pretty sure I have Grub2 (yes, I have grub.cfg file in boot/grub);

```
ubuntu@ubuntu:~$ mount | tail -1 
/dev/sda6 on /media/c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2 type ext4 (rw,nosuid,nodev,uhelper=devkit)
```
so far so good;

```
ubuntu@ubuntu:~$ ls //media/c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2/boot
abi-2.6.31-14-generic         memtest86+.bin
abi-2.6.31-22-generic         System.map-2.6.31-14-generic
config-2.6.31-14-generic      System.map-2.6.31-22-generic
config-2.6.31-22-generic      vmcoreinfo-2.6.31-14-generic
grub                          vmcoreinfo-2.6.31-22-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-22-generic  vmlinuz-2.6.31-22-generic

```
it is similar to the code in instructions, right?

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2 /dev/sda6
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly
```
houston we have a problem<?>

Anyone able to help me out?


Regards
Jet

---

### Post by Rubi1200 on 2010-08-22
The correct way to get this working is explained in this link:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by jet-san on 2010-08-26
Thanks a lot!
Method 1 works!

Regards
Jet

---

