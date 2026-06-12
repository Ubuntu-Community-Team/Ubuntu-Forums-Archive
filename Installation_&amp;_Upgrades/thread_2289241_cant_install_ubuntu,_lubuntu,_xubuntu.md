---
title: "cant install ubuntu, lubuntu, xubuntu"
date: 2015-08-02
forum: Installation &amp; Upgrades
---

### Post by charlie32 on 2015-08-02
so iv been trying to install either ubuntu, lubuntu, or xubuntu, the issued is the same no matter witch version i use, i put the usb in, start it up, select boot from usb, and get a black screen with a blinking cursor and it does nothing afterwords, i checked the hash, all are correct, used Lili, unetbootin, pendrive, and its the same, tried all 4 usb ports, any suggestions here? stats on the laptop im trying to get can be found on this link [http://www.cnet.com/products/hp-pavilion-dv7-1245dx/specs/](http://www.cnet.com/products/hp-pavilion-dv7-1245dx/specs/)

---

### Post by Bashing-om on 2015-08-02
charlie32; Hello;

Likely a graphics driver issue.
Try booting with the 'nomodeset' boot parameter.
If you are able to boot with this parameter, you can install a graphics driver from the "Additional Drivers" utility in the actual install.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) <- How to set NOMODESET and other kernel boot options in grub2
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) <-nomodeset option in detail

[INDENT][INDENT]let us know how it goes
[/INDENT][/INDENT]

---

### Post by charlie32 on 2015-08-02
how am i supposed to that? when i try to load the image from the usb it shows the syslinux line then immediatly shows a black screen with a blinking cursor on all distros i have tried to install/boot.

---

### Post by Bashing-om on 2015-08-02
charlie32; Hey hey ;

Reading is good . But this should work to get ya booted in the 'try ubuntu' mode:
Boot the liveDVD;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> F6 key (other options) -> arrow down to the preset option(s)space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line is now available, one may append "other" desired boot parameters to the end of the line that are not present in the "presets".
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.
Additional Drivers, location varies depending on the version, ->locate the Additional Drivers utility and install the recommended driver.

If this works in the live environment we can make it work in the install !..
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) on how to use this parameter

Please to advise on your progress and results.

[INDENT][INDENT][INDENT]help is what we do
[/INDENT][/INDENT][/INDENT]

---

### Post by charlie32 on 2015-08-02
well thats one of the problems i cant get to the splash screen all i get is a black screen with a blinking cursor

---

### Post by Bashing-om on 2015-08-02
charlie32; Well;

Are we on the same page ?
When booting the install medium in a legacy MBR partitioned drive, as soon as the bios screen clears, depress and hold the shift key.
Language screen  ? -> boot options screen ?

Else when booting the install medium in the newer UEFI system then it is the escape key that grub looks for.
As soon as the firmware screen clears and AS Soon as ubuntu's splash screen appears repeatedly press release the escape key - there is but a 3 second window of opportunity for grub to recognize that the escape key has been pressed.

If the above does not happen, then you need to verify settings in bios, and that the boot priority is set for the booting medium.

[INDENT][INDENT]there has got to be a way
[/INDENT][/INDENT]

---

### Post by charlie32 on 2015-08-02
will try again, the laptop does not have UEFI though so i know that is not a problem i am having, will post back in a few and see if it works though, thanks for your patience

---

### Post by charlie32 on 2015-08-02
nope still dosnt work, now all i get is a black screen that says SYSLINUX 6.03 EDD 2014-10-06 Copyright (C) 1994-2014 H. Peter Anvin et al

Also, double checked bios and its set to boot from the usb

---

### Post by Geoffrey_Arndt on 2015-08-03
Just to get over the initial hurdle, try burning a DVD and booting up with that (1st check if boot order in bios looks to cd/dvd first, then usb, then hdd).    If you do get a normal bootloader screen, then Bashing OM's info about nomodeset may still be needed to install the proprietary drivers.

---

### Post by kerry_s on 2015-08-03
the "SYSLINUX ..." tells me the usb was not created correctly.
perhaps a issue with the usb drive, can you try another usb drive ?

---

### Post by charlie32 on 2015-08-03
not at this time (im out of state for a few more days) but iv also tried burning dvd's and that didnt work, though i did use the same usb and steps 2 days ago and succesfully loaded ubuntu hardy heron, but was having an issue with my wifi card, posted on here about it and was told to just try lubuntu and xubuntu as hardy is no longer supported (was gonna try and upgrade from there but couldnt get wifi to work and have no hard line here) will try to use a dvd of lubuntu though the other ones i made were of ubuntu.

---

### Post by charlie32 on 2015-08-03
so i used a dvd and got to the boot options screen and selected nomodeset but when i try to install or try without installing i get left at the ubuntu screen with the 5 dots that go from white to orange. does not load past that

---

### Post by Geoffrey_Arndt on 2015-08-03
Can you post a screenshot of the image (not the iso file) after creating the usb flash-stick or the DVD?   It would be helpful to see what directories and files are present - - that will tell if the live image was created with the right steps and tools.

---

### Post by charlie32 on 2015-08-03
yes[ATTACH=CONFIG]263602[/ATTACH]

---

### Post by charlie32 on 2015-08-03
hmmm well after leaving it alone for about 25 min it booted into the try lubuntu but while checking to see if i could get the wifi to work it suddenly shut down? so gonna try it again

---

### Post by charlie32 on 2015-08-03
im getting errors that say 1200.601306 end_request: i/o error, dev sr0, sector 90788 (have several of them all with different numbers)

and others saying SQUASHFS error: squashfs_read_data_ failed to read block (several different numbers)
and SQUASH error: unable to read fragment cache entry (several different numbers)
SQUASH error: unable to read page block (several different numbers)

---

### Post by kerry_s on 2015-08-03
/dev/sr0 is cd rom

most likely you burned the iso to fast, you need to burn iso's at a slow speed.

try booting it again & select check disk/installer

---

### Post by charlie32 on 2015-08-03
already ran memtest says my memory is good no errors on it, anyway to do the install through hardy heron? the other day i was able to get hardy heron to work only problem was my wifi card dosnt work with it. was hoping to just upgrade from hardy but cant get connected to wifi, is there a way to install it from hardy?

---

### Post by charlie32 on 2015-08-03
also tried to burn the disks in another burner and still same errors, kinda lost here on what to do

---

### Post by charlie32 on 2015-08-03
will do but everytime i burn a disk i burn it x2, but will check it still to be certain.

---

### Post by charlie32 on 2015-08-03
Thank you all for your help, so far none of the options mentioned worked, i did the checks on the hard drive, memory, the dvd and the usb, BUT! i decided to check the usb to see if it would install in another computer and it booted just fine, so i used "try ubuntu" to create the lubuntu usb i needed....and it worked like a charm! didnt have to use nomodeset or anything! so maybe that will help someone else if they run into the same problem. i am now running the install and keeping my fingers crossed that there are no more errors, but thank you anyway for the people who replied to the post. will post if the install completes with no problem.

---

### Post by Bashing-om on 2015-08-03
charlie32; Yah !!

Feels good all over.

we await the 
[INDENT][INDENT]final outcome
[/INDENT][/INDENT]

---

