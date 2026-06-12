---
title: "libgvfscommon keryx usb problems"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by palmettoj on 2011-04-23
So I don't have internet and have been using keryx to update my machine (lucid). I think libgvfscommon wasn't updated correctly (unmet dependencies I think) and now my machine won't mount my usb with keryx on it. Nautilus in general seems to have something wrong with it as I can't go to places->computer. I can see my devices with lsusb but I they don't automount and I can't cd to the usb to install my keryx updates with the command line. What are my options at this point? lsusb shows two hexidecimal id's that I think I might be able to mount the usb with, but that's beyond my expertise (or lack thereof).

---

### Post by palmettoj on 2011-04-23
I guess I just need advice on how to mount the usb. It is listed in the output when I do lsusb, but I don't know of any way to access the usb. And this usb has keryx which has my updates (like the libgvfscommon lib). Any mounting advice would be welcome. I've looked into the man files for mount command but I'm still in the dark.

---

### Post by palmettoj on 2011-04-24
Have I changed something in /etc/fstab that could possibly affect this? I can't access "computer" in gui either. I also have a "floppy0" under places that is unresponsive. I don't recall the floppy drive ever having worked, but then again, I haven't really tried to use the floppy drive.

---

### Post by Dutch70 on 2011-04-24
Well since you don't have any other answers, I'll give this a shot.

Edit: It doesn't look like this will work unless you know the drive letter...sorry.

Use the following command to find out the drive letter, as in sda or sdb. That's a lower case L.
```
sudo fdisk -l
```

Then try...
```
sudo mount /dev/sdX
```
replace "X" with your drive letter.

---

### Post by palmettoj on 2011-04-27
thanks, I was able after some work to mount the drive. I followed the manual mounting article in the ubuntu official documentation. When I tried to run keryx by double clicking its icon in the keryx/linux folder, it tried to open in gedit but gave an error tab that the code type was unidentified (or something similar). the error tab also said to make sure i wasn't trying to open binary. This has always worked before and just launched the program.
 
So I tried to Alt+F2 and ran the program from the directory in the usb. It alternatively tried to open in gedit as above or when I tried not to designate a program, it just said it didn't have anything designated to open an exe.
 
I copied my commands from the terminal, but alas, now my usb won't mount in xp. I had created an entry in /etc/fstab to mount the usb as per the documentation, but when I did gksudo gedit (before it opened the file in gedit) it returned an error about libgvfscommon (just as it had done before when I was trying to troubleshoot before posting). Any ideas, anyone?

---

