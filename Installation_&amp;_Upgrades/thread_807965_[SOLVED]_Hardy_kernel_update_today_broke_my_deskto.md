---
title: "[SOLVED] Hardy kernel update today broke my desktop"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by posburn on 2008-05-26
So I logged in to my laptop this morning and there were 18 updates available, one of which was a kernel update (to 2.6.24-17).  After updating and performing the requested restart, all my desktop icons had disappeared and the desktop was totally unresponsive.  The wallpaper was still there, AWN was still running fine at the bottom, programs started ok (e.g., Firefox) just the desktop itself was borked.

I checked the desktop settings in gconf-editor and they haven't been altered - my Home, Network, and Computer icons are still listed as visible, but of course they actually aren't.

I restarted with the older kernel (*.24-16) and no longer had this problem.

Anyone else seen this?  I'm just curious if this is a general problem or if it's specific to my system.  I can give hardware details if anyone thinks its necessary.

Thanks!

---

### Post by dstew on 2008-05-26
When you get a kernel bug like this, it is helpful to look at the kernel log files (use the dmesg command), and make a bug report to [Launchpad]("https://launchpad.net/ubuntu"). The problem is usually some particular aspect of your hardware is incompatible with the new kernel. Maybe the bug has already been reported. Usually kernel bugs are hardware-specific, so if you search, include a term about your hardware.

Along with your dmesg output, be prepared to post information about your hardware: lspci will show your PCI devices, and the bug-squashers will also want to know details about your motherboard.

---

### Post by posburn on 2008-05-27
Thanks very much for the pointers about Launchpad.  I was putting together the info (dmesg, lspci outputs) for a bug report and needed to boot back in to the *.24-17 kernel to get a fresh kernel log and to my surprise everything started just fine - icons were there, desktop was ok....

Here's what I think happened - there must've been some conflict between the newer kernel and the version of avant window navigator I was using.  Later yesterday afternoon, after the kernel update, I dl'ed several updates to AWN.  Since that's the only thing on my system that's been changed since the kernel update, I can only assume there must've been a conflict somewhere since the problem is now gone.

Thanks very much for your response - I'll mark the thread as "solved" though I didn't actually solve anything - the problem just "blew away":)

---

### Post by stanley82 on 2008-05-27
You can activate the old kernel during boot by hitting "esc" when prompted by grub.  Just arrow down to the previous kernel.  Also you can sudo gedit /boot/grub/menu.lst and look for "defaults   0" that refers to the default kernel, change it to most likely 2.  0=first,1=first_restore.

---

### Post by shr2004 on 2008-05-27
I had this update today. No problem so far, just another menu item is added to grub. I have deletd previous entries "..16" from grub. Still everything in going fine in my machine.

---

### Post by Rodd_Roddy on 2008-05-27
THanks for the info stil new to the linux world .. was able to read what u had put and it fixed my problem. I had type a similiar question in another forum on here [http://ubuntuforums.org/showthread.php?p=5051420#post5051420](http://ubuntuforums.org/showthread.php?p=5051420#post5051420)

---

