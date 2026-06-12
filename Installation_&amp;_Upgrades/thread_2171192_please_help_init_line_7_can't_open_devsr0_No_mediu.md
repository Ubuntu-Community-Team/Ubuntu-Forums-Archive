---
title: "please help /init: line 7: can't open /dev/sr0: No medium found"
date: 2013-08-29
forum: Installation &amp; Upgrades
---

### Post by richard15 on 2013-08-29
I dunno what else to do. I'm trying to install ubuntu via usb on a friends computer currently running windows vista which some time ago he had gotten a virus that had caused some permanent damage to the system and recently has become non responsive half way into logging in.  Reinstalling would be an option but he does not have the cd, and the cd drive itself doesn't work for anything anymore. So thats why i figured usb install of ubuntu, until I ran into this no medium found error.  Its a pentium D 3.2ghz 4gb ram, and (no floppy).  I had used google and found posts of possible options such as making  sure floppy controler was disabled in the bios which did need to be done.  And  adding bits of code to the txt.cfg.  I've tried many to no avail.  If anyone can shed some light or if i need to supply any additional information I eagerly await any help from one of you kind strangers :D  Thank you in advance.

EDIT: I'd also like to add that some of the code adding stuff i may very well be doing wrong, or putting it on the wrong line or whatever, so i figured i'd add this so you all could see and inform me if it is correct or not. the live media path and the floppy.allowed were the 2 things i added

default live
label live
  menu label ^Run Ubuntu from this USB
  kernel /casper/vmlinuz.efi
  append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz splash --
label live-install
  menu label ^Install Ubuntu on a Hard Disk
  kernel /casper/vmlinuz.efi
  append boot=casper cdrom-detect/try-usb=true only-ubiquity initrd=/casper/initrd.lz live-media-path=/casper floppy.allowed_drive_mask=0 splash ignore_uuid --
label memtest
  menu label Test ^memory
  kernel /install/mt86plus
label hd
  menu label ^Boot from first hard disk
  localboot 0x80

---

### Post by richard15 on 2013-08-29
For Schlitz and liqueurs I decided to take his cd drive out since its next to worthless anyways.  Voila!!! It no longer gives that error. However....... after a minute or so it brings me to a prompt labled initramfs with a error saying it couldn't find a live file system.   It feels like I'm getting closer but for argument sake i'm pretty much a noob when it comes to troubleshooting anything ubuntu related. I have my own ubuntu system but it installed just fine and only thing i've had to do was learn to navigate the system.

---

### Post by ubfan1 on 2013-08-29
I've never had to make changes to the txt.cfg file, but I have had problems with "no medium" with a laptop missing a cdrom drive. But I also has complaints about no /dev/sdb  (which should have been the usb media) as well as sr0.  I'd go back to the original file.  What I did not not necessarily good or without consequences, but it did get the disks re-numerated and allow the startup to proceed-- I yanked and replaced the usb when I got the error.  I figured I had a flakey USB controller (on my third motherboard, and that's a symptom of the controller going).  Install proceeded normally, nothing else was odd.

---

### Post by SeijiSensei on 2013-08-30
Just to ask a dumb question, but you did tell the BIOS to use the USB drive as the boot medium, not the CD or floppy, right?

---

