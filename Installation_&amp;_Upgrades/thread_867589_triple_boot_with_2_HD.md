---
title: "triple boot with 2 HD"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by squir on 2008-07-23
I have 2 SATA 150GB HD.  I divided them into partitions 40/40/10/30/30 and formatted to NTFS.  I put WinXP on C on first HD with only first HD connected.  Then disconnected HD and connected 2nd HD installing Vista enterprise on C.  Next connected both HD and tried installing ubuntu 8.04.  I had to install manually to get it to install on Disk 2 on last partition but instructed to put swap on first HD on partition with only 10GB.  I requested ext 3 journaling file system and put mount point /

When it finished installing it notified “unable to install GRUB in (hd0). Executing grub-install (hd0) failed.  This is a fatal error.  Internal error. Failed to initialize HAL.”  Now the swap partition is hidden. 

Now it boots directly to winxp without asking.  
1-	Please tell me if there is a way to correct the GRUB and how to do it in detail. 
2-	If I must I will reinstall vista and try again with ubuntu but how can I get the swap partition back that it setup and hid. How do I let GRUB install to MBR.  Please be specific for a newbie.
Thanks to all

---

### Post by logos34 on 2008-07-23
This thread may help you solve the problem:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by squir on 2008-07-23
If possible I would like to correct or reinstall the grub.
Can anyone help with that?

---

### Post by logos34 on 2008-07-23
> **squir said:**
> If possible I would like to correct or reinstall the grub.
Can anyone help with that?

see link in my sig

Otherwise mount your root partition on the live cd and post your **/boot/grub/menu.lst** and

**sudo fdisk -l**

---

