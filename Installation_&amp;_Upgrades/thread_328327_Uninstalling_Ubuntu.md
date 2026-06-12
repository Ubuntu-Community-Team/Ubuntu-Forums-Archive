---
title: "Uninstalling Ubuntu"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by dmb83fan41 on 2006-12-30
Hello all!  Well my problem deals with Ubuntu and Windows XP.  I have been running Ubuntu for about a month now on my Toshiba notebook and finally decided to go back to XP (realized there were two many XP programs I still need).  So I figured if I simply went ahead and stuck my full recovery cds in and booted off them it would erase Ubuntu and Windows XP would be my new OS.  Everything seem to being going fine, well after going through the 3 recovery cds and rebooting I get a screen that simply says the following; 

GRUB loading Stage1.5

GRUB loading, please wait...
Error 71

Being a newbie with Linux and computing in general I have no idea what this means.  I'm a little worried.  Is my notebook ruined?  I need the help of someone fast.  Please, I know if anyone can help me it's one of you guys :) This is all the further I can go.  I have no idea what else to do.  I have tried to doing some google searches, but I really don't understand what all they mean and they all seem to be different answers.  

Thanks for any help!!

---

### Post by d3v1ant_0n3 on 2006-12-30
Assuming you are going for a full reinstall (ie wiping Windows and Ubuntu and starting from scratch):

Load up the Ubuntu Live CD, and run Gparted (gnome partition editor) from the System> Administration menu.

Delete all your partitions, and format the drive as NTFS.

Reboot with your Windows install cds and all should work as intended.

---

### Post by dmb83fan41 on 2006-12-30
I will give that a try right now.

Thanks!!

---

### Post by dmb83fan41 on 2006-12-30
One other question with gparted...how long will the entire process take?  Just curious, its been running for about an hour here.

Thanks everyone!!

---

### Post by bigken on 2006-12-30
if you have a windows cd rom boot from it and go to recovery console type
fixmbr enter then fixboot enter then exit when the pc reboots your into windows 
if you dont have a xp cd see if you can borrow one

---

### Post by dmb83fan41 on 2006-12-31
> **bigken said:**
> if you have a windows cd rom boot from it and go to recovery console type
fixmbr enter then fixboot enter then exit when the pc reboots your into windows 
if you dont have a xp cd see if you can borrow one

Ok so after I type fixmbr, I should get an output that says caution doing this will wirte a new MBR.  Is this where I hit "Y"?  

My entire screen reads the following:
**Caution**

This computer appears to have a non-standard or invalid master boot record.

FIXMBR may damge you partition tables if you proceed.

This could cause all the partition on the current hard disk to become inaccessible.

If you are not having problems accessing your drive, do not continue.

Are you sure you want to write a new MBR?

Thanks for any help!!!

---

### Post by dmb83fan41 on 2006-12-31
Just wanted to say everything worked out just great!  I was able to get XP back on.  Thank you for your help guys!!

---

### Post by bigken on 2006-12-31
happy you got it sorted :D

---

