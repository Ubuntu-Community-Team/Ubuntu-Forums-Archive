---
title: "Ubuntu 10.04.3 LTS. Need LVM help."
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by pchokola on 2011-08-29
I originally tried setting up LVM with the desktop version of Ubuntu, but LVM was not available, so it was recommended to use the server version. However I am having problems setting it up. I am trying to set up the following while in the installation program of Ubuntu Server 10.04.3 LTS.
 
1) /boot ext4 standard partition. I have no problem setting this up.
 
2) Then the following I want as logical volumes under LVM
 
/home ext4
swap swap
/ ext4
 
So,
1) I set up a physical volume big enough to hold /home, swap and /.
2) Then I made a logical volume for each named lv_home, lv_swap and lv_root on the physical volume.
3) However, when I hit continue to go to the next step it says that no / partition has been created. But there is no way to format the logical volumes and add the filesystems for home, swap and / before going to the next step.
 
So, what am I missing? Is there perhaps guide for this?

---

### Post by pchokola on 2011-08-30
SOLVED.
 
I found the following tutorial; although it is for LVM on 11.04, with the addition of encryption, it pointed to the solution.
 
[http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/](http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/)
 
The problem is that it is necessary to scroll the screen upward in order to view the logical volumes that were created, at which point they can be selected and the filesystems added.

---

