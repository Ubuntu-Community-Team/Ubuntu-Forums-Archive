---
title: "Ubuntu 7.04 GRUB issue"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by nightsbird on 2007-05-30
I installed  7.04 amd64 version last night. I have it installing to a SATA drive and the only PATA drives are dvd players. I have it setup up to still use the windows xp bootloader same as ive done on my laptop. Let me start by saying laptop works perfect. After much effort I got it booted up without a hitch and it was running fine. when it performed an update and updated the kernel on reboot all I get is


GRUB_  

the underscore is just blinking please help.

Jeff

---

### Post by floke on 2007-05-30
Looks like you got zapped by the crappy 20-16 kernel update :(
One thing that the new kernel has tended to do is to rename your hard drives, so it might be pointing in the wrong place (don't know why it isn't starting up though!).
You could try editing your menu.lst file via a live cd and see if you can fix it that way.

Good luck.

** EDIT ** Didn't see bit about Windows bootloader - in which case I have no idea what to do.

---

### Post by dabl on 2007-05-30
> **nightsbird said:**
> 
the underscore is just blinking please help.


Press Alt-F1, you may get a text login prompt.  If not, try Ctrl-Alt-F1.  If you get the prompt, you can log in to your system.  If you get that far, you need to reconfigure xorg.conf to get a GUI.

```
sudo dpkg-reconfigure xserver-xorg
```to start the xserver configuration script.

On the first screen, when it asks you to autodetect, tell it "no", and on the second screen tell it "VESA".  Then you can accept defaults through keyboard and mouse, unless you have something non-standard.  On the monitor, pick a resolution you can live with for awhile, and the refresh range that is suitable for your CRT or LCD. At the end of the script, it will dump you back to the text prompt.  Type ```
startx
``` and you should get a GUI, in which to search for a better driver for your graphics chip.

:)

---

### Post by awaldram on 2007-05-30
This NOT related to the kernel whats happened is when the kernel updated grub was updated at the end this has re-written you MBR on you Hard disk to point to Linux.

Unfortenatly you dont have grub working like this as your using Windows Boot loader hence you get the start message from Grub then it stops.

You need to run a windows recovery to re-write the MBR with WIndows files not linux files.

---

### Post by awaldram on 2007-05-30
Sorry cant be more helpful but havn't run dual boot like that for 8 years or more 

Stopped just for this reason but I used to get Li from lilo as I didn't use grub then.

I used to find it much safer to run Windows from the grub/lilo menu as Windows would find it very difficult to re-write the MBR   during a patch round.

But these days dont do windows at all on my home machines.

---

### Post by awaldram on 2007-05-30
dont know if its still true but 

fdisk /mbr

may save the day for you (used to work but this was years ago)

---

### Post by nightsbird on 2007-05-30
wow that was fast response. Windows still loads fine. I will try the alt f1 idea

i know from previous ubuntu installs it has root=/dev/hda2 etc.

i had it booting to root=/dev/sda3 but now in
the menu.lst it shows

root=UUID= and what looks like a MD5 hash

is that how its supposed to look?

---

### Post by awaldram on 2007-05-30
ah its me got the wrong end of the stick I thought

"....and updated the kernel on reboot all I get is


GRUB_
"

meant just that.

In which case you have been stung be the kernal bug

try 

vol_id -u /dev/hda1

to find which UUID goes where  replacing hda1 with the correct partion numbers

check menu.1st and fstab.

if you want a quick  fix try

update-initramfs -u

---

### Post by nightsbird on 2007-05-30
when i type that command I get "error open volume"

---

### Post by linuxbz on 2007-05-31
Try
sudo vol_id -u /dev/xxx

(where xxx is the device)

---

