---
title: "JAUNTY and automount the SD card on the eeePC"
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by azanutta on 2009-04-16
i only want to know if anybody has the same issue as me:

at every boot of my eeepc with jaunty and openbox, if i start nautilus i don't see any SD card even if it's inserted... and the ACPI scripts (by elmurato, for controlling bluetooth, cam, sd, wifi) are setted on "enable SD"
i'm sure that these scripts are not the problem, because
toggling off and back on the scripts or manually removing the sd an pluggin it back in, results in displaying and successfully mounting....
i don't know if it's a jaunty bug or else... sad
____________________________________________________________________________
eeePc 1000h - ubuntu 9.04 - .29.1e kernel - Openbox WM - elmurato SCRIPTS Eeeeasy JAUNTY - SDHC 4 Gb - wacom bamboo fun tablet

EDIT: checked my /etc/fstab that appears:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc  defaults                    0  0  
# / was on /dev/sda2 during installation
UUID=c76484d0-cb58-4b70-833b-d5d9fef94f9a  /              ext4  relatime,errors=remount-ro  0  1  
# /home was on /dev/sda6 during installation
UUID=58522a7f-dfad-4847-9201-18cc70cec187  /home          ext3  relatime                    0  2  
# /media/fatimm was on /dev/sda7 during installation
UUID=4939-54B2                             /media/fatimm  vfat  utf8,umask=007,gid=46       0  1  
# none was on /dev/sda5 during installation
UUID=298e0bdf-ef73-451d-a753-e65662be3b7a  none           swap  sw                          0  0  
[B]/dev/sdb1                                  /media/sdb1    vfat  users,user                  0  0  
[/B]

so it seems that the line with the automonting of the sd is present... =(

---

### Post by jfernyhough on 2009-04-16
Remove the line for the card reader from your fstab and it will automount. 

Because the system is looking for a card at boot, and not finding one, it will not automount.

Otherwise, leave a card in permanently and it will appear at /media/sdb1 - assuming it's formatted as FAT.

###

I'm not sure what the scripts are there to do - my 701 works perfectly with a stock Jaunty UNR. :D

---

### Post by sgosnell on 2009-04-16
It's the same with my 900.  The cards automount, and I have no need for any scripts.

---

### Post by azanutta on 2009-04-17
> **jfernyhough said:**
> Remove the line for the card reader from your fstab and it will automount. 

Because the system is looking for a card at boot, and not finding one, it will not automount.

Otherwise, leave a card in permanently and it will appear at /media/sdb1 - assuming it's formatted as FAT.

###

I'm not sure what the scripts are there to do - my 701 works perfectly with a stock Jaunty UNR. :D

so i have to remove the entire line from fstab?!?!?!?
how does the system know how to mount if it isn't in fstab?!?!?
:o
well...
i'll try right now...

anyway my sd is always permanently in... and it will not be automounted

---

### Post by danwood76 on 2009-04-17
It uses hal.
How does it know to mount a CD when its inserted or a USB disk?

---

### Post by azanutta on 2009-04-17
removed... still no luck...
behaviour correct as always if i unplug and replug...
still nothing displayed in any file manager if i boot the pc with the sd inserted... =(

---

