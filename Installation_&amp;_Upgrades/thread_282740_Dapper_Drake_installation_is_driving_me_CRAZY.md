---
title: "Dapper Drake installation is driving me CRAZY"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by boaisy on 2006-10-23
I've been trying to install Ubuntu 6.06 on one of my extra machines for the better part of 3 hours now. I'm having extreme trouble getting past some pretty simple areas, like selecting a keyboard layout. I downloaded the LiveCD image from their site and after messing around with it for a few hours, decided that it would be a good intro to Linux. Ugh.

The LiveCD has an Install icon on the desktop. On clicking it, I'm met with a list for a localization, then a time zone selection, and then a keyboard layout list that never populates. There's a text box at the bottom of the window where I can "try out my new keyboard localization" but I never get a Forward button, regardless of how many copies of War and Peace I type into the box.

I have tried every permutation of PS/2 and USB keyboard & mouse, I have booted into safe mode, I have downloaded the text install image and tried that.

Anyone have any suggestions? All the google results for the problem say that it's the fault of the USB keyboard but I've tried it again and again with a PS/2 keyboard. 

Machine: 
Biostar iDeq 200n, nForce 2 mobo
2x512 DDR333, memtest86+ shows no errors
300g Maxtor hdd

Thanks.

---

### Post by wpshooter on 2006-10-23
Have you checked the integrity of the Ubuntu CD by running the verification function found on the initial Ubuntu boot screen menu ?

---

### Post by jqk on 2006-10-23
If the integrity of the Ubuntu CD seems to PASS the integrity test, have you tried installing in via text mode?

---

### Post by gn2 on 2006-10-23
Have you tried disabling Legacy USB support in the BIOS and connecting keyboard and mouse to the PS2 ports?

---

### Post by John.Michael.Kane on 2006-10-23
boaisy the live install cd does not get along with alot of folks hardware.

As another poster stated please try the text mode alternate install cd.

---

### Post by boaisy on 2006-10-23
Ok, I'm just about ready to give up on Ubuntu.

I've downloaded & burned each of the images (LiveCD & alternate) 2 times now.  Every time I run the media check on them I get a black screen that says "Uncompressing Linux... Ok, booting the kernel." and hangs there for ~3 minutes.  Eventually "Starting system log daemon: syslogd, klogd." comes up and the system hangs indefinitely.

When I boot from the LiveCD (which always boots to 640x480, iirc) I am stuck on the original problem of not being able to select a keyboard.  When I boot into video safe mode (which brings me right to 1280x1024) I have the same problem.  It looks nicer, but I have the same problem.

If there is anything any of you could suggest as far as specific boot-time arguments that I could enter as to make this work, that would be great.  Am I just not meant to run this distro?

Thanks for your time.

edit: gn2: thank you for the suggestion, disabling legacy USB was one of the first things I did.  The PS2 ports are there... you might as well use 'em, right? ;)

---

### Post by gn2 on 2006-10-24
> **boaisy said:**
> Ok, I'm just about ready to give up on Ubuntu.

I've downloaded & burned each of the images (LiveCD & alternate) 2 times now.  Every time I run the media check on them I get a black screen that says "Uncompressing Linux... Ok, booting the kernel." and hangs there for ~3 minutes.  Eventually "Starting system log daemon: syslogd, klogd." comes up and the system hangs indefinitely.

When I boot from the LiveCD (which always boots to 640x480, iirc) I am stuck on the original problem of not being able to select a keyboard.  When I boot into video safe mode (which brings me right to 1280x1024) I have the same problem.  It looks nicer, but I have the same problem.

If there is anything any of you could suggest as far as specific boot-time arguments that I could enter as to make this work, that would be great.  Am I just not meant to run this distro?

Thanks for your time.

edit: gn2: thank you for the suggestion, disabling legacy USB was one of the first things I did.  The PS2 ports are there... you might as well use 'em, right? ;)

Have you tried the "Alternate" CD route?

If it was me (lazy sod) I'd try it with PCLinuxOS.

---

