---
title: "Automount USB broke with upgrade"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by CazperII on 2008-05-04
I've found several threads concerning automount problems but after hours of searching I haven't found any that solved my problem.

To summerize my problem:

After upgrading from 7.10 to 8.04 automounting of USB-sticks and external HD's is broken. The icons don't show up on the desktop. 

An example output of dmesg when inserting a USB-stick: 

```
[ 2230.468032] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 2230.468108] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 5235.156625] usb 6-1: USB disconnect, address 6
[ 5237.733601] usb 6-1: new high speed USB device using ehci_hcd and address 7
[ 5237.807359] usb 6-1: configuration #1 chosen from 1 choice
[ 5237.808103] scsi8 : SCSI emulation for USB Mass Storage devices
[ 5237.808569] usb-storage: device found at 7
[ 5237.808576] usb-storage: waiting for device to settle before scanning
[ 5240.682048] usb-storage: device scan complete
[ 5240.683967] scsi 8:0:0:0: Direct-Access     JetFlash TS512MJF2A/120   8.07 PQ: 0 ANSI: 2
[ 5240.688530] sd 8:0:0:0: [sdb] 1003520 512-byte hardware sectors (514 MB)
[ 5240.689286] sd 8:0:0:0: [sdb] Write Protect is off
[ 5240.689293] sd 8:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 5240.689298] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 5240.692254] sd 8:0:0:0: [sdb] 1003520 512-byte hardware sectors (514 MB)
[ 5240.693027] sd 8:0:0:0: [sdb] Write Protect is off
[ 5240.693034] sd 8:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 5240.693038] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 5240.693045]  sdb: sdb1
[ 5240.694250] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[ 5240.694323] sd 8:0:0:0: Attached scsi generic sg2 type 0

```

So obviously the USB-drive is recognised and is given the /dev/sdb1 device node. Manually mounting in command line also works. 

The USB-drive also shows up in Places -> Computer menu of Gnome. But when I doublclick on it a box appears with the message: Unable to mount location unable to mount file.

I know HAL is supposed to mount the drive with the gnome-mount command. So I tried this manually in a console with the debug option on and this is the output: 

```
gnome-mount -vbd /dev/sdb1
gnome-mount 0.8
** (gnome-mount:3393): DEBUG: Mounting /org/freedesktop/Hal/devices/volume_uuid_58B6_0B11
** (gnome-mount:3393): DEBUG: read default option 'shortname=mixed' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:3393): DEBUG: read default option 'uid=' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:3393): DEBUG: read default option 'utf8' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:3393): DEBUG: read default option 'umask=077' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:3393): DEBUG: read default option 'exec' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:3393): DEBUG: read default option 'flush' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:3393): DEBUG: Mounting /org/freedesktop/Hal/devices/volume_uuid_58B6_0B11 with mount_point='SASSIE', fstype='', num_options=6
** (gnome-mount:3393): DEBUG:   option='shortname=mixed'
** (gnome-mount:3393): DEBUG:   option='uid=1000'
** (gnome-mount:3393): DEBUG:   option='utf8'
** (gnome-mount:3393): DEBUG:   option='umask=077'
** (gnome-mount:3393): DEBUG:   option='exec'
** (gnome-mount:3393): DEBUG:   option='flush'
Mounted /dev/sdb1 at "/media/SASSIE"

```
The USB-stick is then mounted an shows up on the Desktop. So the problem lies elsewhere. 

I tried reinstalling HAL but still no cigar. 

The usefree option in gconf is not there so that can't be the problem either. 

I'm at the end of my imagination on how to tackle this problem, so I'm turning to the community for help.

---

### Post by gtamboise on 2008-05-06
I am facing a somewhat similar problem, that I reported as bug [226585]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/226585").
If multiple users use my workstation, the first one can use USB devices just fine but automount is broken for the second one. I have noticed yesterday that it goes beyond USB mass storage, as even my scanner is impacted.

---

### Post by CazperII on 2008-05-06
At first my USB printer (Samsung ML2010) also wouldn't work, but after reinstalling the driver I was able to print fine. I have no scanner available here, so testing isn't possible. 

I just tested a SD-card, wich also automounted in Gutsy but doesn't anymore in Hardy. This excludes a problem with the USB (storage) driver and implies a HAL/DBUS/Gnome-mount problem.

Maybe it's indeed time to post a bug report.

---

### Post by somis on 2008-06-03
since update from 7.10 to 8.04 dont works samsung ML-2015. any sugesstions?

SD card slot didn't work since i had 7.10, but worked with windows, when i had it.

---

### Post by toster13 on 2008-06-05
**to CazperII** I had some strange problem and after googling I found the answer in the SUSE forum. I got this problem after using gparted.
Try this 
```
sudo rm /etc/hal/fdi/policy/gparted-disable-automount.fdi
```

Original topics
[http://www.suseforums.net/index.php?showtopic=49820]("http://www.suseforums.net/index.php?showtopic=49820")
[http://forums.suselinuxsupport.de/lofiversion/index.php/t64108.html]("http://forums.suselinuxsupport.de/lofiversion/index.php/t64108.html")

---

### Post by Mamsaac on 2008-06-12
I have exactly the same problem as topic creator (it is the same... as well, USB and SD cards don't automount, but one can do it manually). Last solution does not work. In fact, the file does not even exist.

It's becoming irritating not to have usb automounting, if anyone has a solution (I've been trying everything lately) I would appreciate it.

---

### Post by hg21 on 2008-10-28
I have this problem in kubuntu. 

I can correct it by going to KDE control centre ( kcontrol)->Desktop->Behaviour, then ticking the "show icons on desktop" box, then opening the Device Icons tab and ticking suitable boxes. 

UNFORTUNATELY this also clutters the desktop with icons for every file in my home directory. Haven't found a way round that yet.

LATER EDIT:-

Thanks to Alec on the KDE list, I can now get rid of the  clutter.

Create a new hidden folder in the home directory (call it ".Desktop"), and then go to KControl Center > System Administration > Paths, change "Desktop Path" to "/home/me/.Desktop" and click Apply. When it asks you if you want files moved, click Cancel.

---

