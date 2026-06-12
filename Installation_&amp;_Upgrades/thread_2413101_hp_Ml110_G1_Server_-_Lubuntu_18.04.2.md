---
title: "hp Ml110 G1 Server - Lubuntu 18.04.2"
date: 2019-02-21
forum: Installation &amp; Upgrades
---

### Post by electrosteam on 2019-02-21
My Dell laptop, running Lubuntu 18.04.1, has died.
The replacement is a hp Proliant server that was retired due to corrupted Windows.
It has a DVD installed marked 'DVD+ReWritable' and 'DVD+R DL'.

Installed Redhat 9 from some old CDs to prove the machine is functioning Ok, all looks good.

The iso image of Lubuntu is 1.1 GB, but the machine lists only 'CD-ROM' in the boot selection. Alternative is Floppy, no USB mentioned.

Can I expect to make a bootable DVD and get it to boot through the DVD (listed as CD-ROM ) ?

If so, is Rufus the way forward ?
If not, what are the alternatives ?

John.

---

### Post by Autodave on 2019-02-21
Rufus should work for you.  Older machines did not have the option of booting to USB.  You may want to check and see if there is a BIOS update: that may allow you to boot to USB.

---

### Post by electrosteam on 2019-02-26
The problem was the DVD, removed the Lite-On and replaced with LG.
Now can read the iso DVD.
Did a disk check for defects - Ok.
Check memory - 6 passes no errors.
Booted with DVD, got Lubuntu opening screen and selected 'Try' - disk operates for a while then install hangs with blank screen.
Try 'Install' with same result.

Machine still boots Redhat 9 Ok.

Along the way got indications that the VIA-Rhine is missing and PCI controller has resource conflict.
These may be related, I wonder if they are the reason the server was retired.
I can image the eth0 port could be damaged by external faults.
(The boot-up messages are really helpful). 

Under Redhat 9, eth0 is not listed with 'ifconfig -a'.

What errors would cause either 'Try' or 'Install' hang part way with a blank screen ?

Have to search for more data on VIA-Rhine and the noted resource conflict.

I have got a Xubuntu iso that I will attempt to boot. 
John.

---

### Post by electrosteam on 2019-03-04
Removed a modem card and resolved the resource conflict.

Discovered the black screen responds to ALT + Fn.
F1 provides the install progress log, F2 to tty2.

Under tty2 can login as Lubuntu, password clear.
Everything tried in the command line works, but only off the DVD - even if ' Install ' selected.

Searched around and found some log files.
The installation has failed because there is no viable screen.

Using the command line, can I install a text version of Lubuntu ?

Will go back to the boot options and see if I can get a video driver to come up.
(the existing Redhat 9 installation has no video problems)

John

---

### Post by electrosteam on 2019-03-05
Booted Redhat 9 and entered 'xrandr' to get response 800x600 at 60Hz
Did a trial install with vga=671 to get data display of acceptable entries - 800x600x16 Vesa looks like a good match with entry =314 (octal?)
(note: memory says it was 314, but others please check before copying).

More searching.
Discovered reference to removing boot option 'quiet splash' and replace with nomodeset.

Entered boot options:
 - remove quiet splash,
 - replace with nomodeset,
 - added at end of line vga=314.

Selected install with a clean disk - and it worked.
Lots of harddrive activity over an extended period, several screens of interesting data displayed as the install progressed.
Seemed to include Firefox getting some data off the net.
Prompted for name of computer, operator name and password.

Requested reboot.
DVD removed and computer rebooted - to a text login screen.
Entered name and password, then black screen with just a cursor for some time, then a normal command line.
Not perfect, but it least there is now an OS on the harddrive.

Will attack again tomorrow.
John

---

### Post by electrosteam on 2019-03-06
Entered $ sudo apt-get upgrade. Completed without fault.
Entered $ sudo apt-cache -n search nouveau. Got list.
Entered $ sudo apt-get install xserver-xorg-video-nouveau. Did its job.

Entered $ startx. "Failed with System program problem detected." box displayed
No response to keys, forced power off.

Reboot. Graphics come up with "System program problem detected." box.
Low definition, but it is working.
Select Cancel.
Check /var/crash logs - seems to have been /usr/bin/light-locker.

This reply is the first activity using the gui.

Now to search for a better video  driver and/or change display settings.

John

---

