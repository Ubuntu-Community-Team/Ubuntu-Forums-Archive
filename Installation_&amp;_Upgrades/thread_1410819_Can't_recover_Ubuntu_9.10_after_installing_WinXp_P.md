---
title: "Can't recover Ubuntu 9.10 after installing WinXp Pro"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by rider799 on 2010-02-19
Hello!

I can't recover Ubuntu after installing WinXp. Now i already know that Xp overwrites the MBR file and boots only itself.

I was trying to recover by this strategy(recomended) [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) with LiveCD.

I use Ubuntu 9.10 Karmic Koala - Grub2

I got stuck on this .. it shows that file /grub/core.img is unreachable

 ubuntu@ubuntu:~$ mount | tail -1
/dev/sda5 on /media/79056c34-6519-47f1-96ea-7a83ca531ccf type ext4 (rw,nosuid,nodev,uhelper=devkit)
ubuntu@ubuntu:~$ ls /media/79056c34-6519-47f1-96ea-7a83ca531ccf/boot
abi-2.6.31-14-generic         memtest86+.bin
abi-2.6.31-17-generic         System.map-2.6.31-14-generic
abi-2.6.31-19-generic         System.map-2.6.31-17-generic
config-2.6.31-14-generic      System.map-2.6.31-19-generic
config-2.6.31-17-generic      vmcoreinfo-2.6.31-14-generic
config-2.6.31-19-generic      vmcoreinfo-2.6.31-17-generic
grub                          vmcoreinfo-2.6.31-19-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-17-generic  vmlinuz-2.6.31-17-generic
initrd.img-2.6.31-19-generic  vmlinuz-2.6.31-19-generic
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/79056c34-6519-47f1-96ea-7a83ca531ccf /dev/sda5
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/79056c34-6519-47f1-96ea-7a83ca531ccf /dev/sda5 --recheck
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba10ba10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6502    52227283+   7  HPFS/NTFS
/dev/sda2            6503       25860   155493135    7  HPFS/NTFS
/dev/sda3           25861       38913   104848222+   5  Extended
/dev/sda5           25861       38539   101844036   83  Linux
/dev/sda6           38540       38913     3004123+  82  Linux swap /Solaris

Also when i checked the files on dev/sda5 on live session with LiveCD - the folders "root" and "lost+found" are unavailable "The folder contents could not be displayed. You do not have the permissions necessary to view contents of .."
maybe that's why there is not the line lost+found after command "ls /media/79056c34-6519-47f1-96ea-7a83ca531ccf/boot"

Has someone expierenced the same? 
I don't get it where is problem? I am beginner in Ubuntu and linux systems :)

On previous Ubuntu (before installing WinXp) i had a password - does it make some selfdefense when i try to install new MBR? 

I would like to have dual-boot afterwards.

I will aprreciate every help! :)

---

### Post by darkod on 2010-02-19
Forget about strategies, you only need two commands. You Linux (root) partition is /dev/sda5. Just boot live desktop again and in terminal do:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That will install grub on the MBR of /dev/sda using /dev/sda5 as root partition. Reboot and all should be fine.

After you boot the hdd ubuntu you will probably have to do

sudo update-grub

because when reformatting the windows partition it got new UUID and it won't match with the one currently in the grub config files. So don't be surprised if you can't boot windows until running that.

---

### Post by raphsabb on 2010-02-20
Thank you! I installed win7 on my laptop and the tuts from the OP were the ones I found online. I thought I was doomed cause it gave me errors no matter what I did.

---

### Post by rider799 on 2010-02-22
Thanks Darkod! It worked perfectly!! ;)

---

