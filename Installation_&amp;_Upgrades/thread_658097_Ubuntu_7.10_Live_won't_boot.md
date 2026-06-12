---
title: "Ubuntu 7.10 Live won't boot"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by carlosvega on 2008-01-04
hi everyone, i'm trying to boot from the Ubuntu 7.10 Live CD. i downloaded it, burn it, entered setup and set the dvd drive as the boot drive, entered the ubuntu menu, "start or install ubuntu". then it goes to the loading bar which loads just fine but right after it finishes loading the orange bar, it says:

Loading, please wait:
Permission denied
Permission denied
Permission denied
Permission denied
Permission denied... and so on
no more details than that.. from then on it goes nowhere
the only thing i can do is Ctrl+Alt+Del to reboot

Leave you with my system specs:

Pentium D 915 @ 2.8 Ghz
1 Gb DDR2 533
Asus P5V-VM Ultra Motherboard
XFX GeForce 6200 TurboCache PCI-Express 512 Mb
160 Gb HDD Sata2 8 Mb Cache (with Windows XP pro+SP2 installed)
Samsung SyncMaster732NW WideScreen Monitor

BTW, i tried to boot from the 7.04 Ubuntu+Beryl Live Cd and it also showed a bunch of identical errors in the same phase of the boot sequence

if i missed any details please tell me.. any help will be appreciated

---

### Post by njparton on 2008-01-04
This is a long shot but... try selecting the safe graphics option and hit F6 and remove "quiet" and "splash" from the command line that pops up. Then hit enter.

Otherwise it sounds like it's having problems caching or writing some data to your hard drive (unless the live CD runs just in RAM, I can't recall).

---

### Post by PmDematagoda on 2008-01-04
You could also try the Alternate CD which might have a good chance of working.

---

### Post by carlosvega on 2008-01-05
i tried doing what you said (hitting f6, removing quiet and splash, entering safe graphics) and the following lines pop up repeatedly:
SQUASHFS error: unable to read fragment cache block
SQUASHFS error: returned unexpected result
SQUASHFS error: failed reading block
SQUASHFS error: unable to read page
start-stop-daemon: unable to start /usr/sbin/cron: input-output error

---

### Post by jonallport on 2008-01-23
Bump!

I have exactly the same error.  Installing on HP nx6125 with new HDD.

Help!!!

---

