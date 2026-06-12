---
title: "Removing Ubuntu 11.10 for fresh install"
date: 2012-06-02
forum: Installation &amp; Upgrades
---

### Post by Jary316 on 2012-06-02
Hi everyone,

I initially had two partitions on my hard drive, one for Windows and one for data. I installed Ubuntu 11.04 a while back and created a new partition for Ubuntu.

I updated to Ubuntu 11.10 using the automatic updater and now wish to install Ubuntu 12.04 but I am feeling I am in the need of a fresh install.

I have the bootable CD ready and my data has been backed up. I am wondering how I can uninstall Ubuntu or format my partition and then switch back to the live installation CD. Does the installation CD allows me to format my previous Ubuntu or will it only try to update please?

This is the current state of my disk:


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    34812854    17405403+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    34812855   279000854   122094000    7  HPFS/NTFS/exFAT
/dev/sda3       279000916   976771071   348885078    f  W95 Ext'd (LBA)
/dev/sda5       279000918   644686249   182842666    7  HPFS/NTFS/exFAT
/dev/sda6       644687872   968540159   161926144   83  Linux
/dev/sda7       968542208   976771071     4114432   82  Linux swap / Solaris

I believe that Ubuntu resides on /dev/sda6.

Any advice please on how I can replace my current Ubuntu for a fresh install of Ubuntu 12.04 please?

Thank you very much!
Jary

---

### Post by darkod on 2012-06-02
It's very easy but you have to use the manual install option (called Something Else). It will list all partitions on the disk.

Select /dev/sda6, click on the Change button below. Change the Use As to ext4, tick the format box, select mount point /.
Then select the /dev/sda7 partition, change the Use As to swap area. There is no mount point for swap.
Select the bootloader to go to /dev/sda.

That's it. The installer will use sda6 for / formatting it at the same time. That way all old data is gone (the previous OS).

---

### Post by Jary316 on 2012-06-02
> **darkod said:**
> It's very easy but you have to use the manual install option (called Something Else). It will list all partitions on the disk.

Select /dev/sda6, click on the Change button below. Change the Use As to ext4, tick the format box, select mount point /.
Then select the /dev/sda7 partition, change the Use As to swap area. There is no mount point for swap.
Select the bootloader to go to /dev/sda.

That's it. The installer will use sda6 for / formatting it at the same time. That way all old data is gone (the previous OS).

Awesome darkod! That sounds great and easy.

I will try that very soon! Thank you very much!

---

### Post by inashdeen on 2012-06-02
it is easy actually. once you have installed ubuntu once, never used the *install side by side to window*s option again.
in that way you will create multiple swap for no reasons.

---

### Post by Jary316 on 2012-06-02
> **inashdeen said:**
> it is easy actually. once you have installed ubuntu once, never used the *install side by side to window*s option again.
in that way you will create multiple swap for no reasons.

Thank you inashdeen. I see an option to "Erase disk and install Ubuntu". Is this the correct option please?

Thanks for your help.

---

### Post by inashdeen on 2012-06-02
WOOOW not quite. not that, the option is *"something else."*

---

### Post by Jary316 on 2012-06-02
> **inashdeen said:**
> WOOOW not quite. not that, the option is *"something else."*

I see that option! Thanks a lot inashdeen :)

---

### Post by inashdeen on 2012-06-03
Have you managed to install Ubuntu 12.04 safely ? :)

---

### Post by Jary316 on 2012-06-03
> **inashdeen said:**
> Have you managed to install Ubuntu 12.04 safely ? :)

I just did this afternoon! Thanks a lot, it works great! Thank you very much for your help inashdeen, and darkod help as well!

(I am not being able to change the status to "SOLVED" but wish to do so.)

---

### Post by darkod on 2012-06-03
The option is in Thread Tools above the first post.

Well done. :)

---

### Post by inashdeen on 2012-06-03
Congratulations :) . I wish you all the best in trying out linux. by the way, do add me on google talk and google+ at [email]inashdeen@gmail.com[/email]

Happy linuxing :)

---

