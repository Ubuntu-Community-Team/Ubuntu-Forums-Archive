---
title: "Noob needs help  or is it to late"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by paulb2004uk on 2010-04-07
Hi

Hopefully someone can help / advise

I recently scapped XP Pro on an old laptop (Toshiba Portege 7220)as it was so slow and I installed Ubuntu 9.10 - All installed ok and it worked fine for about a month. Last week I switched on, got the Ubuntu splash screen and thats where it stayed. I gave lappy to a friend of mine that knows about Pc's (hahaha). When I got it back he said he'd wiped the HDD and partially installed xp. The install apparantly hung after the reformat and copying files onto it.

My problem now is I can't boot from HDD, Ubuntu Live CD or Windows CD - Laptop is set to boot from cd then hdd.
When I try to boot from CD, the cd is read as I hear the drive being used also see light for cd flashing, after a while i get a blank screen with flashing cursor in top left corner and the cd stops.

If I remove the HDD and put it in external usb caddy I can see the windows folders/files when plugged into my desk top.

My questions are :-

1. Is there any way to make the drive reusable as a internal drive again as I know it works as an external drive
I would like to reinstall Ubuntu on it

2. Is it a fault with the laptop itself - how do I check

Any advice will be welcomed.

---

### Post by 2hot6ft2 on 2010-04-07
Can you boot the livecd with the hard drive out?
If you can run the mem check to see if the RAM has any issues.
If the livecd will work with the drive out you should be able to wipe the drive and install to it like it was a blank slate.
The part where you say
> **paulb2004uk said:**
> When I got it back he said **he'd wiped the HDD and partially installed xp. The install apparantly hung after the reformat and copying files onto it.**

May indicate either a hard drive failure or another hardware problem which is also what it sounds like when you said.
> **paulb2004uk said:**
> Last week I switched on, got the Ubuntu splash screen and thats where it stayed.
So you may be looking at replacing the drive, RAM or have something else failing but I would suspect the hard drive.

---

### Post by paulb2004uk on 2010-04-07
I originally thought hard drive but it is readable in an external drive caddy hooked up to my desktop via usb. 
I have run the memory test on Live CD - Completed - 0 errors

---

### Post by seafury on 2010-04-08
Hi 

Just an idea.

If you dont have data on the drive you need, hook it up to the usb caddy on your Desktop.

Use G-Parted (google and download and burn on cd) and wipe the disc clean.(make sure it's not your Desktop HD :-) )
Put the drive back in laptop and try to boot via live cd.

Or create usb start disc and boot from that if your laptop can boot like that. (older ones cant) can be done form live cd on your Desktop.

Last you can install it on the drive from the live cd on desktop BUT i dont know how as i think it will want to load grub someone with more knowledge might be able to help.

Good luck.

PS try taking battery out disconnect power and hold the on/off power button in for about 30 sec. it may be that the bios is a bit scrambled. it clears the bios. Or reset bios to factory default.
Reboot and set the boot priority back to CD--> HD. Hopefully it works.

---

### Post by paulb2004uk on 2010-04-12
Ok I've created a G-Parted cd - wiped the hard disk. Still unable to boot from live cd.

Tried to install windows xp pro, this also failed.
Found an old copy of WIN98 (said it waS OLD). This installed and booted from hdd with various driver errors. 
Tried then to start from live cd - still unable to boot from live cd.
I've also tried fixmbr and fixboot from the xp pro Recovery console.
Im now at a loss what to try.

---

### Post by paulb2004uk on 2010-04-16
RESOLVED - I tried installing XP again and that hung at 34 minutes left to finish. Google search showed that it's most likely a hardware fault - usually internal modem.
Disabled internal modem in BIOS
Rebooted and reinstalled Ubuntu 9.10 - installed and working ok.

---

