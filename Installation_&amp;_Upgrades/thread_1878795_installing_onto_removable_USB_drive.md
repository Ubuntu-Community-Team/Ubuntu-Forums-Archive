---
title: "installing onto removable USB drive"
date: 2011-11-10
forum: Installation &amp; Upgrades
---

### Post by SinusPi on 2011-11-10
Situation: laptop has a dead Windows XP HDD. The drive was removed and connected via USB to my desktop PC running Windows 7. I need to install Ubuntu onto the USB-connected drive, which has to return to the laptop it was removed from and boot there.

WUBI seems to only set up boot options in the current Windows system I'm running; I don't want that, as it would break my desktop boot setup. I need to be able to specify that WUBI installs Ubuntu onto the removable drive (already possible, of course) AND that it set up booting on THAT drive and its XP booting mechanism, not my current desktop Windows 7 setup.

Under good ol' DOS this would be simply "sys E:"...

Any ideas?

---

### Post by mohamedtoma73 on 2011-11-10
please read this [thread]("http://ubuntuforums.org/showthread.php?t=1650699&page=3")

---

### Post by SinusPi on 2011-11-10
I thought of that already, but I'd definitely rather not reboot and modify BIOS settings on the desktop machine - it's my work PC and I have a rather strict rule NOT to modify anything crucial that could destabilize my work environment.

So, any way to force an MBR update on a designated drive, without rebooting to the installer?

Or, alternatively: that drive IS a Windows XP bootable; I could put something in its boot.ini, and it would probably work if worded right.

---

### Post by mohamedtoma73 on 2011-11-12
try putting this entry in boot.ini of the usb-connected drive
c:\wubildr.mbr="ubuntu"
then save the changes in boot.ini
then install ubuntu by wubi inside the usb-connected drive using your pc windows 7.
after completing the install and before reboot move  wubildr and wubildr.mbr from the c drive of your pc to the root of usb-connected drive.use easybcd to remove the entry ubuntu from your pc boot screen 
then  reconnect your usb-connected drive to the laptop it came from
boot and choose ubuntu from the boot screen .if it boot the ubuntu will complete installation in the laptop environment and will install its hardware.

---

### Post by mick222 on 2011-11-12
What do you mean dead xp hdd . Is xp working on the disk if not wubi wont work,

---

### Post by SinusPi on 2011-11-12
> **mohamedtoma73 said:**
> try putting this entry in boot.ini of the usb-connected drive
c:\wubildr.mbr="ubuntu"
..........


Yup, that's what I did, but it didn't work.

Then, on a hunch, I dug into the partition table of the drive. Hello, main partition wasn't even active. I have no idea how that happened - but I activated it... and then everything started working; booted, got asked to run either Windows or (new) Ubuntu...

As usual, problem was not where I thought it to be.

Thank you for your help, though - it'll surely come in handy some other time.

---

### Post by mohamedtoma73 on 2011-11-12
the problem is solved

---

### Post by Rubi1200 on 2011-11-12
Problem solved?

Then please mark the thread as such by using the Thread Tools near the top of the page.

And good work by the way figuring out the solution :)

---

