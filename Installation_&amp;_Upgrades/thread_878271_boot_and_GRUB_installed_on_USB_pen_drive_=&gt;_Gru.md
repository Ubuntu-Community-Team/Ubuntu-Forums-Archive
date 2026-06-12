---
title: "/boot and GRUB installed on USB pen drive =&gt; Grub Error 15 :("
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by mr_piouf on 2008-08-02
hi 

I am installing the latest ubuntu using RAID1, so I need to put the boot and grub appart. I decided to put them on a USB pen drive.

/ => raid1
/boot => usb pen drive

The installation goes fine but when I want to boot :

GRUB Loading stage 1.5.
GRUB Loading , please wait...
Error 15

I checked, the bootable flag is on the usb, the bios is set to boot on usb etc

I dont know what to do...

---

### Post by redraiderbum on 2008-08-02
I wouldn't make a separate /boot partition.  I have always had problems with this in ubuntu (as opposed to RHEL based distro where it is standard operating procedure).  

Why do you need to separate the boot from the raid1?  You can just do the partitioning first then install.  The Ubuntu Server disk is actually better for this.  Then once you finish the server install at the command line type:
> 
sudo apt-get ubuntu-desktop

---

### Post by mr_piouf on 2008-08-02
I am separating the /boot because I thought you coulnt boot from a raid1 array. Isnt that right ? I think I tried and had some other errors from grub. 

I use the serveur cd and install the desktop after like you said :)

---

### Post by redraiderbum on 2008-08-02
I have been booting from raid arrays for a while.  Did it work with the server install creating a raid1 for the system install and then installing the desktop after?

---

### Post by mr_piouf on 2008-08-03
Yes it works.

I am going to retry booting from the array. So if you put the whole / in the RAID1 you should be able to boot from any of the two disks composing the array right and from the md volume right ?
Grub and the mbr is on both ?

---

