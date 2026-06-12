---
title: "Install 11.04 server from USB; fails, can't mount /cdrom"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by Alan_graham on 2011-06-17
I'm trying to install ubuntu 11.04 server onto a box that used to run Debian.  I've (yesterday) installed ubuntu desktop successfully onto the box from USB, but I decided that ubuntu server would be a better option.  

The box doesn't have a cdrom drive installed.

The creation of the usb stick from the ubuntu server disk image worked fine as far as i can tell, and the boot from USB starts fine, but the install fails at the step titled "Detect and mount CD-ROM".  If I skip the step, the next step fails trying to mount the debconf configuration file from file:///carom/pressed/ubuntu-server.seed.  I guess that's no surprise...

Is there a change I need to make to the iso to make it try to mount the USB image to /cdrom?  Or is there a change to make the install script look at the USB mount point?

Or (and I'm hoping this is the one), is there a command line option I need to give the install at the first step that will make everything automagically work?  :)

Alan

---

### Post by mpegg on 2011-12-24
I am currently stuck with this same problem.

when i unplugged the usb stick from the usb3 port then put it back in a usb2 port the cdrom was detected and installation continues...

---

### Post by darkod on 2011-12-24
If you have enough free space on the usb to copy the ISO file (leaving the install files that are currently there), I have used these instructions to install server from usb on a server with no cd-rom:

When you get the screen with  “Load CD-ROM driver from removable media?” press ALT-F2 to get a console and enter these commands:

mkdir /mnt/usb /mnt/iso
mount –t vfat /dev/<usb drive partition device file> /mnt/usb
mount –t iso9660 –o loop /mnt/usb/<iso file> /mnt/iso

ALT-F1 to return to installation dialog and answer as follows:
Load CD-ROM driver from removable media? <No> 
Manually select CD-ROM module and device> <Yes>
Module needed for accessing the CD-ROM: none
Device file for accessing the CD-ROM: /dev/loop0

---

### Post by Tw1sty on 2012-06-15
I am installing 12.04 server and found that even after mounting the iso to /mnt/iso I could not proceed with the installation.

So what I did instead was 

mount –t iso9660 –o ro /dev/loop0 /cdrom

and that worked a treat.

---

### Post by Tw1sty on 2012-06-15
or  a slightly different way from the top

mkdir /mnt/usb

mount -t vfat /dev/sba /mnt/usb   <-change sba to your usb device
mount –t iso9660 –o ro /mnt/usb/iso.iso /cdrom  <-change iso.iso to your iso file

then go back into setup DO NOT try and mount the cdrom in setup, as you have already mounted it - just proceed to the next step.

---

### Post by darkod on 2012-06-15
> **Tw1sty said:**
> or  a slightly different way from the top

mkdir /mnt/usb

mount -t vfat [COLOR=Red]/dev/sba [/COLOR]/mnt/usb   <-change sba to your usb device
mount –t iso9660 –o ro /mnt/usb/iso.iso /cdrom  <-change iso.iso to your iso file

then go back into setup DO NOT try and mount the cdrom in setup, as you have already mounted it - just proceed to the next step.

Shouldn't that be /dev/sda1 as an example? It needs to have the partition number too, not just the device if I'm not mistaken.

And the sba -> sda is just a typo, the devices are named sdX.

---

