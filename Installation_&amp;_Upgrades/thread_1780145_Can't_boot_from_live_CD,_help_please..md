---
title: "Can't boot from live CD, help please."
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by Niva on 2011-06-11
Hello everyone,

A couple months ago I attempted upgrading to 11.04 and the upgrade did not go well.  Had frequent freezes and eventually had to wipe out my linux partitions and start from scratch.

Note: I dual boot with Win 7 due to Photoshop

Now all of a sudden I can no longer boot with linux.  This is not particular to Ubuntu, I tried Fedora and Debian.

I get no error messages upon bootup, instead the loader seems to be getting stuck somewhere while it's attempting to load the linux kernel.  The only message I see is as follows from the Ubuntu 11.04x64 cd:

**ISOLINUX 4.02 debian_20101016 ETCD Copyright (C) 1994-2010 H. Peter Anvin et al**

I get a blinking cursor under this but cannot type, and cannot proceed in any way, hard reboot is required.

Because I'd been using grub as the booter for the machine this severely set me back.  Eventually supergrub disk managed to restore my windows booter so I could get within windows at least.  From there I had to install Ubuntu from within windows via WUBI.  The system runs stable but it's been a couple of months and I've found no good way to fix this issue.  It makes no sense why I could not boot from the live CD.  I also get the same error when booting from a thumbdrive.  I found another thread in the archives suggesting it was a problem with my CD rom drive, it wasn't because I tried using another drive which works just great on another machine... same error.  Searching for this problem in google gets me some results but in other languages and not much useful info.  I'm really not willing to admit defeat about the hardware and buy a new machine because this one's plenty enough, but it is very frustrating why this happened all of a sudden.

What I suspect may have happened:  A few months before 11.04 came out I updated the bios on my machine.  Here are my hardware specs:

Asus M3A32-MPV Deluxe with Wifi (disabled wifi @ bios)
Phenom x4 955 (no OC)
8GB of RAM 

Any help with this problem is much appreciated.

Oh, I can no longer boot into older versions of Ubuntu either, I'd been running 10.04 and 10.10 prior to this fiasco and those booted and installed fine.  I'm not sure if Asus messed up their bios so badly but it seems like it's the only suspect I have at this time.

---

### Post by drs305 on 2011-06-11
It could be a video problem.

As the CD boots, press F6. You may get the language screen. Press ESC then F6 again. This should present a dropdown menu - try selecting 'nomodeset' and boot with that option. It really shouldn't be necessary if the LiveCD booted before but it's something to try. If you normally use other kernel options, you can select them or add them manually. See the following for more information:

[https://help.ubuntu.com/community/LiveCDBootOptions]("https://help.ubuntu.com/community/LiveCDBootOptions")

---

### Post by Niva on 2011-06-11
drs305 thanks for your prompt response, I attempted pressing F6 and it still gets stuck in the same spot, I don't get any options at all.

---

### Post by linuxinstalledfromhdd on 2011-06-11
If you want, you can start a trouble ticket with them to roll back your BIOS..  They should have the older BIOS original update you can use to re-flash your BIOS.   Usually when you search for updates for your BIOS, they provide a list of all the seperate BIOS zip files.  Check the dates, and see which one is able to reverse the changes you have made to your BIOS.

---

### Post by Niva on 2011-06-11
Aaah yes, I attempted doing this but the EZ flash tool Asus provides doesn't allow me to load a BIOS with an older date on it... plus I can't roll too far back, my CPU isn't supported by very old revisions.  I'm still unsure if it is the BIOS but it's the only thing that's really changed that I can think of.  Boggles my mind that it would happen just so.

---

### Post by drs305 on 2011-06-11
I think you tried using the CD in another drive. 

Have you tried using an older LiveCD - and do they still work? It just seems odd to me that a BIOS update won't boot a CD. 

Do you happen to have two drives, with the BIOS booting to an MBR on the secondary drive rather than the CD? (i.e. are you sure it's attempting to boot the CD?) I just tried booting a Natty CD and the F6 function worked ok on mine...

---

### Post by Niva on 2011-06-11
I only have 1 cd drive, I'm sure it's booting off it.  My supergrub disk boots ok for some reason off ths drive, thankfully.

I tried booting with another cd rom drive from a different machine because I suspected it could be an error off the reader, that wasn't the case.

I've also tried booting older live CDs and multiple distros, same (or similar error) while loading the kernel.

Windows DVD boots ok...

---

