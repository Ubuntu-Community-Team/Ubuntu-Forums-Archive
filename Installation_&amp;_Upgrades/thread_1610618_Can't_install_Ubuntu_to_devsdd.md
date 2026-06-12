---
title: "Can't install Ubuntu to /dev/sdd"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by MetaPhaze82 on 2010-10-31
Been trying all day long to install Ubuntu x64 on my Desktop. I have a P6X58D mobo with Mavell 9123 controller and an Intel Controller for RAID.
 
The Intel controller is set to RAID-0 for my Win7 setup, but my linux setup is suppost to run off my Marvell 9123 controller set to IDE mode only, with one drive. The controller doesn't even reconize RAID in any form or fasion.
 
Any way I finally got GPART to see the 120GB SATA drived connected to the Marvell controller. I was able to format it so I can have a /swap /root /home. But I still can't see the drive in the Ubuntu installer.
 
Can *ANYONE* Help? I've been through IRChat and no one seems to have an idea.

---

### Post by ronparent on 2010-10-31
Which distro are you working with? Have you tried installing from a live cd session after verifying that gparted see the drive before entering the install?

---

### Post by MetaPhaze82 on 2010-10-31
> **ronparent said:**
> Which distro are you working with? Have you tried installing from a live cd session after verifying that gparted see the drive before entering the install?
 
I am working with 10.10 Ubuntu distro. I created a USB stick install per Ubuntu's instructions.
 
I have in fact loaded up USB stick, gone to INSTALL to hard disk. Waited till it did not find /dev/sdd, then go to GPART to verify the drive and partitions are there, and the Ubunutu installer still does not find the device.

---

### Post by ronparent on 2010-10-31
Have you also tried to install by selecting the manual partitioning option. If gparted sees the drive in a live cd it should also see it whent the installer is run.

---

### Post by MetaPhaze82 on 2010-10-31
> **ronparent said:**
> Have you also tried to install by selecting the manual partitioning option. If gparted sees the drive in a live cd it should also see it whent the installer is run.
 
I had my third cup of Ubuntu, and yes...If I used auto install it would destory my RAID Volume.
 
And of course if GPART sees it IT SHOULD see it in the Ubuntu Installer, but it doesn't.
 
Seems I have the same issue that others had in 9.04 Jaunty with Marvell 9123 controller that was resolved.
 
10.04 gives the same issues. Was this actually not resolved?

---

### Post by ronparent on 2010-10-31
Do you have a non-raid intel sata port? Also, even if you have drives on that controller set up in raid, It doesn't necessarily mean a non-raid drive can't also be plugged into that controller. I have that situation on a promise raid set with a blu ray drive also plugged into that chip set.

---

### Post by MetaPhaze82 on 2010-11-01
> **ronparent said:**
> Do you have a non-raid intel sata port? Also, even if you have drives on that controller set up in raid, It doesn't necessarily mean a non-raid drive can't also be plugged into that controller. I have that situation on a promise raid set with a blu ray drive also plugged into that chip set.
 
Here is what I have DISK1 DISK2 in to a Intel 10CH chipset controller, built and reconized as one VOLUME, VOL=DESKTOP.
 
I have another SATA drive 120GB Seagate drive connected in to another controller Marvell 9123 controller, set to IDE or ACHI seems to make no diff.
 
Ubunutu and GPART woudln't see the drive nor the controller at first. Some messing with BIOS settings I got GPART to see the drive on the MARV Controller. I formatted the drive with /*root, /swap, /home....
 
But Ubuntu installer can not see this drive even though GPART can now...

---

### Post by MetaPhaze82 on 2010-11-01
Still can't find a solution. I searched the boards and found that my board (P6X58D Premium) appears to be supported. No luck on my end though.

---

### Post by oldfred on 2010-11-01
Was sdd ever part of the RAID? RAID leaves meta data that confuse things.

DO NOT run this on any drive you want to keep RAID on:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sdd
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

