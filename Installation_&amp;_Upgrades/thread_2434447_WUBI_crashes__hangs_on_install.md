---
title: "WUBI crashes / hangs on install"
date: 2020-01-06
forum: Installation &amp; Upgrades
---

### Post by prodave on 2020-01-06
Trying to install Ubuntu 14.04LTS on top of Windows XP on an old Compaq laptop using WUBI, the version that came with the ISO.

The initial stages work, it re boots into a UBUNTU gui screen.

A box opens titled "install"

A progress bar "verifying the instalation configuration" completes

Then it hangs for a wile, the screen goes blank, a text error message briefly appears and the computer re boots.

It is very hard to read the error message, not enough time. I have photographed it and what I can read says something along the lines of 

(some unreadable numbers) Reboot, restarting system 
ping rsync daemon rsync
kill now restart <warn> could not acquire the 'org.freedesktop.modemmanager1' service name

* unmounting temporary file systems
* deactivating swap
* stopping early crypto disks


That may not be exactly correct, the photographed screen shot was a bit out of focus and hard to read.

What can I do to make it complete please?

---

### Post by CatKiller on 2020-01-06
Neither Wubi nor 14.04 are supported any more. You should try with a supported version: 16.04, 18.04, or 19.10.

---

### Post by Impavidus on 2020-01-06
Windows XP isn't supported either. So, why do you want to "dual boot" two obsolete systems using an obsolete method to fake dual boots?

If you had asked this in 2013, using Ubuntu 12.04, we could have helped.

---

### Post by prodave on 2020-01-06
I am just trying to revive an old computer. It had Windows XP originally.  I am not bothered about retaining windows XP.

I am trying with Ubuntu 14.04 as that is the version I already had from a previous install on a different computer to save a several hour download on our slow broadband.

I had previously tried installing a current version of ubuntu from DVD only to find problems with the DVD drive.  This PC won't boot from USB so trying WUBI was my last chance to try and install something from the USB memory stick.

---

### Post by yancek on 2020-01-06
> Trying to install Ubuntu 14.04LTS on top of Windows XP on an old Compaq laptop using WUBI, the version that came with the ISO.


Maybe this is just a terminology thing, but you can't install Ubuntu using WUBI without having an installation of windows as it is installed inside the windows system  Brief overview of it at the site below.  

[https://en.wikipedia.org/wiki/Wubi_(software)](https://en.wikipedia.org/wiki/Wubi_(software))

---

### Post by Impavidus on 2020-01-06
I'm tempted to say "just bring it to the recycling centre" (there, I just said it), but if you wish to get some more life out of that computer despite being unable to boot from removable drive, I've got one suggestion. You could take the hardrive out and put it into a different computer that does boot from removable drives. Next install Ubuntu. Make sure it matches as far as bios/uefi and 32/64 bit are concerned and don't install any proprietary drivers. Then move the hard drive back to the old computer. With a bit of luck, it will boot.

BTW, it's theoretically possible to use Windows tools to make some free disk space for Ubuntu, install Ubuntu using Wubi inside the Windows partition as a fake dual boot, then format the drive using the installed Ubuntu system to make an Ubuntu partition, migrate Ubuntu to that partition, reboot to get the real dual boot Ubuntu running, format the Windows partition to get rid of Windows and reuse it as /home partition. Theoretically.

---

