---
title: "Ubuntu 9.10 Beta ISO not installing on Sun Virtualbox (PUEL)"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Toadinator on 2009-10-03
I'm running the latest Sun Virtualbox (PUEL, not OSE) and trying to install the new Ubuntu 9.10 Beta. Live mode works fine, and I have been able to install the earlier alpha releases, but for some reason Ubuntu 9.10 Beta does not want to install correctly no matter what I try. My main symptom is right when 9.10 starts installing, it stops and quits. After that, it either goes into a very stripped down Live mode or not responding at all. Launching the installer from Live mode--which works fine mostly by the way--doesn't work either and the same thing happens. Can someone else confirm this bug and possibly offer a workaround, such as upgrading an older build?

---

### Post by Longinus00 on 2009-10-03
I recently (last night) installed a copy of 64bit beta on virtualbox. The drive was mounted as sata (I have the sun version, not ose) and everything else was pretty standard.

---

### Post by Nobby on 2009-10-03
same problem is reported on this thread ([http://ubuntuforums.org/showthread.php?t=1280925](http://ubuntuforums.org/showthread.php?t=1280925)) (not using virtualbox though).  Bit disappointing as I was hoping to test the beta using a fresh install.

---

### Post by Guruji on 2009-10-03
installed beta on virtualbox (not OSE), x86, it was only booting into grub at fist, started it on recovery mode, did the upgrades and everything works fine now.
Try to get the latest livecd image, it will come with the updates and might work better.

---

### Post by Endolith on 2009-10-06
Doesn't work for me, either.  Just shows the desktop and then a bunch of text gibberish, and switches back and forth.

---

### Post by Merk42 on 2009-10-06
Worked fine for me with my 32bit Windows 7 hosts and 64bit Ubuntu 9.04 hosts.

The only problem I had was after finishing installing it would be stuck in a reboot loop. Resetting the VM fixed that though.

What version of Virtualbox and what are you specs?

---

