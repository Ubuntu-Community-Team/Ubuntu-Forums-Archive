---
title: "grub doesn't know how to boot"
date: 2014-11-20
forum: Installation &amp; Upgrades
---

### Post by Jeremy_Doucet on 2014-11-20
Okay, here's the thing. Evidently something is screwed up in my boot process.  I've attached output from (df -h,  fdisk -l,  /etc/fstab).  I was creating a live usb stick and sometthing went wrorng. Now that shows as a file system (which I need to remove by the way) and my machine won't boot into the OS.  I was at the "grub rescue" but now I've moved past that to the "grub>" menu.  Still no luck.  It seems now that the /dev/sda1 is pointing to a USB stick (Kali Live).  I'm working right now off of a 17GB Ubuntu stick to get this typed out.  The "Kali Live" is what needs to go and my machine needs to boot from the 500GB drive.  All of my data is still here but only accessible from this other Live Ubuntu OS.  Any help is appreciated.

---

### Post by oldfred on 2014-11-20
It looks like you have an LVM install with a separate /boot.

Is it a full drive encrypted LVM or just LVM?

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

May be best to see all the details. This runs all the commands you posted plus many others.
Post link to summary report. Do not run autofix until someone has reviewed your install.


 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Jeremy_Doucet on 2014-11-20
Thanks for the input. Going check those links now. Entire 500gb is encrypted by the way.

---

### Post by oldfred on 2014-11-20
For script to fully run you have to mount and give passphrase so report can include the standard info in your system. It is just system data, so nothing confidential should be shown, unless you label partitions with names you do not want others to see.

---

