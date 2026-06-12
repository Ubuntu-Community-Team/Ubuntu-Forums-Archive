---
title: "URGENT.  After upgraded no 10.04 in menu"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by vzhen on 2010-05-01
I upgraded 9.04 to 9.10 to 10.04.
During the upgrading i chose all "using local .....setting" exp menu.list .....


After upgraded and reboot, it using grub loader 1.5 and only display 
-9.04  kernel 2.6.28
-9.04 kernel 2.6.28 recovery
-Windows xp

NO 10.04 at all

If i choose 9.04 kernel 2.6.28 to boot. It hang in startup with black screen (freeze)

What can i do ?

Window XP = no problem

----------------------------------------------------------------------------------------------------------
FIXED

1. Boot into the live CD
2. Chroot into the real system:
      2.1 Find which partition the real system is installed on with **sudo fdisk -l**
      2.2 Make a directory to mount it at with **sudo mkdir -p /mnt/computer**
      2.3 Change to that directory with **cd /mnt/computer/**
      2.4 Mount it with **sudo mount /dev/sda? /mnt/computer/**
      2.5 Link /dev/ and /proc/ with **sudo mount --bind /dev/sda? /mnt/computer/dev/**
      2.6 **sudo mount --       bind /proc/sda? /mnt/computer/proc/**
      2.7 Change root with sudo **chroot /mnt/computer/**
3. Update grub2 with **update-grub2**

OR use

**oldfred solution at #6** 

DONE

Thanks all the replies

---

### Post by oldfred on 2010-05-01
See the comments here. It detected that you had customized your menu.lst and cannot in all cases convert everything.

[http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)

If sudo update-grub does not work, you will have to manually add new entries for the new kernels.

---

### Post by vzhen on 2010-05-01
Hi, Thanks for your reply

Can u show me how to perform this under live cd since i missed the step during upgrade

Using live cd to boot in is the only way i can use.

Thank you

---

### Post by Penguin Guy on 2010-05-01
> **vzhen said:**
> Hi, Thanks for your reply

Can u show me how to perform this under live cd since i missed the step during upgrade

Using live cd to boot in is the only way i can use.

Thank you

[LIST=1]
[*]Boot into the live CD
[*]Chroot into the real system:
[LIST=1]
[*]Find which partition the real system is installed on with [FONT="Courier New"]sudo fdisk -l[/FONT]
[*]Make a directory to mount it at with [FONT="Courier New"]sudo mkdir -p /mnt/computer[/FONT]
[*]Change to that directory with [FONT="Courier New"]cd /mnt/computer/[/FONT]
[*]Mount it with [FONT="Courier New"]sudo mount /dev/sd**??** /mnt/computer/[/FONT]
[*]Link [FONT="Courier New"]/dev/[/FONT] and [FONT="Courier New"]/proc/[/FONT] with [FONT="Courier New"]sudo mount -B /dev/ /mnt/computer/dev/[/FONT] & [FONT="Courier New"]sudo mount -B /proc/ /mnt/computer/proc/[/FONT]
[*]Change root with [FONT="Courier New"]sudo chroot /mnt/computer/[/FONT]
[/LIST]
[*]Update grub2 with [FONT="Courier New"]update-grub2[/FONT]
[/LIST]

**Steps 2.1 & 2.4:** If you can't figure out which partition Ubuntu is installed to, then post the results of [FONT="Courier New"]sudo fdisk -l[/FONT] back here and I'll update the instructions for you.

---

### Post by vzhen on 2010-05-01
Thanks again

This is my sudo fdisk -l

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1912    15358108+  83  Linux
/dev/sda2   *        1913        3647    13936387+   7  HPFS/NTFS
/dev/sda3            3648       14593    87923745    5  Extended
/dev/sda5            3648        3890     1951866   82  Linux swap / Solaris
/dev/sda6            3891        4133     1951866   82  Linux swap / Solaris
/dev/sda7            4134       14593    84019918+  83  Linux

---

### Post by oldfred on 2010-05-01
Penguin Guy's post is for grub2 and chrooting into it.

I think you can just edit menu.lst from the liveCD. You will have to drill down to /??/boot/grub. I do not remember if /?? is /media and your install or whatever the liveCD adds to the beginning of the mount. You are showing two linux partitions, do you have two installs? You need to edit the correct one that has grub in the MBR.

Copy one of your current entries and update UUIDs and kernel versions to the new ones.

To see UUIDs
sudo blkid

Kernels will be in /boot so you can copy the names.

---

### Post by Penguin Guy on 2010-05-01
> **oldfred said:**
> Penguin Guy's post is for grub2 and chrooting into it.

I think you can just edit menu.lst from the liveCD.
Sorry about that, I didn't read the original post properly and just assumed that he would be using Grub2.

---

### Post by vzhen on 2010-05-02
Hi,  This is fixed.
I will re-write the instruction in my 1st posted.

---

