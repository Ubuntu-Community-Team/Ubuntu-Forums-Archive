---
title: "Can't run or install Ubuntu 8.04 x86"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by andystauffer on 2008-09-05
Ok first I would like to mention that I have tried the following with Windows 98 SE, Windows XP Home, and Windows XP Home Media Center Edition, and get the same results with each.  Also, I have tried it with and without any OS updates, such as Service Pack 3.

When I try to do the full install, it tells me to boot from the CD, which I do.  It shows the Ubuntu startup screen with the orange bar at the bottom like it is loading.  It flashes all kinds of "squashfs ..." and I/O errors, all preceded by numbers like 247.357432.  It eventually stops flashing errors and starts doing different checks on my computer, only to start giving me the same type of errors again.  Eventually it takes me to a brown screen with a white box in the upper-left corner.  It stays on this screen for hours until I have no choice but to restart the computer and choose Windows.  I get the same results when I try to boot from the Live CD instead of install.

The next thing I have tried is to install it with windows so I can duel-boot into either one.  It goes through the full installation, and then says to run Ubuntu I have to restart the computer.  I restart, and when given the choice, I pick Ubuntu.  Once again, I get the Ubuntu startup screen with the orange loading bar.  Then the mouse shows up on the screen as an "X", and at the time I can move it, but then the screen changes to a picture of the "Hardy Heron" and I am unable to use my mouse or keyboard.

Any Ideas?

Also, I am running a Pentium 4 1.8 GHZ, with 2 sticks of 128MB DDR RAM, although for some odd reason the computer only recognizes them as regular RAM, and says I only have 256MB instead of 512MB.

---

### Post by TransitMan on 2008-09-05
You state you are have 2 sticks of 128mb ram.
Therefore you only have 256mb of ram to start, not 512.

When you boot the CD, highlight the Memory test and run it to see if any of the memory errors out. If it does, then you will have to replace the defective stick or sticks before proceeding.

---

### Post by andystauffer on 2008-09-05
> **TransitMan said:**
> You state you are have 2 sticks of 128mb ram.
Therefore you only have 256mb of ram to start, not 512.

When you boot the CD, highlight the Memory test and run it to see if any of the memory errors out. If it does, then you will have to replace the defective stick or sticks before proceeding.

I thought if it was DDR ram, it would be 512MB, not 256MB.

Anyways, when I boot from the CD, my options are as follows:
Start installer in normal mode
Start installer in safe graphic mode
Start installer with ACPI workarounds
Start installer in verbose mode
Read-Only Demo

I don't and havn't seen anything about a Memory Test.

---

### Post by Slug71 on 2008-09-05
Try ACPI workarounds.

---

### Post by TransitMan on 2008-09-05
> **andystauffer said:**
> I thought if it was DDR ram, it would be 512MB, not 256MB.

Anyways, when I boot from the CD, my options are as follows:
Start installer in normal mode
Start installer in safe graphic mode
Start installer with ACPI workarounds
Start installer in verbose mode
Read-Only Demo

I don't and havn't seen anything about a Memory Test.

When you boot from the CD drive, those are your only options?
What version of Ubuntu are you trying to install?

---

### Post by andystauffer on 2008-09-05
I had tried that already, and I just tried it again.  It skips almost every error, and starts loading different things such as network management, but then I get about 20 errors which are the same as before, and they are in the 216.xxxxxx range and up.  I get passed these and it says loading Bluetooth and then the screen goes blank.  It goes to a screen of the Hardy Heron and the computer completely freezes after a few minutes.  Also, I have had Red Hat on here a while back, so I know that Linux will work, I just don't know why this won't.  =(((

---

### Post by TransitMan on 2008-09-05
Sounds almost like you got a corrupt download and or bad burn of the CD.

You might want to re-download and then burn to a CD on the slowest burn setting to get a good burn.

Also, compare the md5 checksums between the download you got and the one at the website to see if they match.

---

### Post by andystauffer on 2008-09-05
I got the download of 8.04 Desktop version directly from [www.ubuntu.com](www.ubuntu.com).  When I choose to startup with the Ubuntu CD, it says press escape to access the menu.  If I don't, then it automatically tries to install, but I get HUNDREDS of error messeges.

---

### Post by TransitMan on 2008-09-05
> **andystauffer said:**
> I got the download of 8.04 Desktop version directly from [www.ubuntu.com](www.ubuntu.com).  When I choose to startup with the Ubuntu CD, it says press escape to access the menu.  If I don't, then it automatically tries to install, but I get HUNDREDS of error messeges.

Sounds like a corrupt download.
You should have the option to boot into the LiveCD mode as well as a Memory Test listing.

Again, download, compare the md5 checksums and burn on the slowest possible CD burn speed.

---

### Post by andystauffer on 2008-09-05
I just tried the installation in verbose mode (which i have no idea what that means), and it only had 1 error, but then when it showed the picture of Hardy Heron, it just ceased up again, forcing me to restart my computer.

---

### Post by andystauffer on 2008-09-06
Ok so I tried installing Kubuntu 8.04.1 with KDE 4, and it gets to the first of 6 screens where it asks me to pick the install language, but then it completely freezes up again, so at least I'm not getting any errors anymore and I can get to the installation somewhat.  Still trying new ideas...

---

### Post by andystauffer on 2008-09-06
Still no progress, every installation attempt just lags then freezes the computer before I get to the actual install.  Any ideas?

---

### Post by Partyboi2 on 2008-09-06
There should be a option at the main menu to check the cd for defects,  run it and see if there are any errors.
Did the iso you downloaded pass the [[COLOR=Blue]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") check?

---

### Post by TransitMan on 2008-09-06
Here's a suggestion, try to install Ubuntu 7.10 and see what happens.

And don't use the KDE (Kubuntu) version, just the Gnome version. 
If it installs, then we can go from there.

---

### Post by andystauffer on 2008-09-08
I have tried Kubuntu 8.04.1 KDE 4, and that doesn't work either, even though I do get closer to the actual installation.  I have tried checking the CD for errors, and it's fine, and I have run Memtest86 and had 20 passes after letting it run through the night.  Tomorrow I will try 7.10, as I don't have any CD's to burn it to right now.

---

### Post by andystauffer on 2008-09-12
Well 7.10 doesn't work either, and so I tried Open Solaris, which is Java, and that isn't working either.

---

