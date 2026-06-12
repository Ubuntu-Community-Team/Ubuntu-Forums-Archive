---
title: "Issues when Installing"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by Alrin on 2007-07-12
Hi,

I have a HD that is partioned with XP on one side, and nothing on the other side.  The partition that does not have anything on it is unformated.  I have a free cd containing Ubuntu version 6.06 LTS for the PC.

When i try to install Ubuntu (after hitting enter to start installing it), this is what happends:
"Uncompressing Linux... Ok, booting the kernel.
[17179569.712000]  ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[17179569.712000]  Kernel panic - not syncing: IO-APIC + timer doesn't work!  Boot with apic=debug and send a report.  Then try booting with the 'noapic' option
[17179569.712000]   _"

Not sure how to debug it and send a report.

I read somewhere how to get past this bug by putting noapic after Boot Options but before the -- and then hitting enter.

The boot then goes as normal i assume until i get another error.  This error is concerning the X server:
"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

I am no where near competent enough to diagnose this problem, so i select no.

"  The X server is now disabled.  Restart GDM when it is configured correctly."

I am then left with a black screen with white text.  It appears that it is bash, but i'm not sure what i would do at this point.


What i ended up doing was downloading the latest version of Ubuntu (Ubuntu 7.04), and burning the .iso image to the disc as instructed by the Ubuntu site.  When i try and install from this disc, i get:
 "I/O Error:  Error reading boot CD.  Reboot" - a notification window with an OK button.
"Loading isolinux: Disk error 32, AX = 4200, drive 9F"  - command line at the top of the screen.





My intent is to dual boot my computer with Xp and Ubuntu.  Xp being on the first partition and Ubuntu being on the 2nd partition.

If anyone can help me, i'd greatly appreciate it.

Thanks,
Alrin



EDIT:
Forgot to include some system specs.  if that helps.
E6600 core 2 duo
8800 GTS EVGA video card
2 gigs of ram
300 gig HD - SATA

---

### Post by merlinus on 2007-07-12
It would appear that either your .iso download or cd burn is bad.  Did you do the checksum?  Also, you might try burning it a slow (4x) speed.

It also seems as though there is a video problem with your first install attempts.  I highly recommend the Alternate Install cd, which is text-based.

Another thing you might try whilst using your first cd:

when you get to the command line, enter:

```

sudo dpkg-reconfigure xserver-xorg

```

You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```

-merlin

---

### Post by Alrin on 2007-07-12
Thank you for helping.  I managed to install Ubuntu all thanks to your assistance, but now there's an issue.

"Uncompressing Linux... Ok, booting the kernel.
[17179569.712000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[17179569.712000] Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the 'noapic' option
[17179569.712000] _"


This error comes up when i select to boot into Ubuntu.

---

### Post by merlinus on 2007-07-12
Press "e" at the grub boot menu, arrow down to the kernel line and press "e" again. Then try adding 

noapic

to the end of the kernel line.

Then boot.  If it works, then you can add noapic to the end of the kernel line in /boot/grub/menu.lst as follows:

```

gksudo gedit /boot/grub/menu.lst

```It will look something like this:

> 
title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=74ea0d79-f0a5-4381-a98d-08258758e696 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault
Add noapic after splash, or whatever is at the end of your first kernel line.

-merlin

---

### Post by Alrin on 2007-07-13
I took a friend's advice and re-re-downloaded the latest version and burned it to a disc.

At the moment, it installed and boots fine.

Thank you for replying to the issue.

---

### Post by Pumalite on 2007-07-13
Please post 'latest version' of what, so it can help others. Thank you.

---

