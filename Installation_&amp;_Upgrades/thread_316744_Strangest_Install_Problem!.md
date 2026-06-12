---
title: "Strangest Install Problem!"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by howipepper on 2006-12-11
I purchased a new Dell Dimension E520 a couple of months ago, and installed Edgy as soon as it was released.  The install went fine, and with the exception of having to get the ATi video card to work, it worked very well.  Yesterday I decided to reinstall Edgy, to get the Automatix cruft out of the system.  After a reinstall, using the alternate CD in Expert mode, I was unable to boot!  I reinstalled again, and made sure Grub was installed to the MBR, but the boot hangs at the very beginning, right after the "Ubuntu" screen gets displayed.

I tried several times, with the same problem each time.  Finally, because I can't afford to be without my computer, I installed Windows XP to get me up and running.  XP boots fine and runs with no problems.

Any idea what happened?

Howard

---

### Post by ReaderRat on 2006-12-11
Did you re-install the ATI drivers? (the obvious). Have you tried installing using the Alternate CD (text mode)? Is Automatix causing problems on your system?....just curious...

---

### Post by howipepper on 2006-12-11
The boot process doesn't hit that part.  You have to install the ATi drivers AFTER a successful install and reboot.

If you had read my post, you would have notices I said "Alternate CD, in Expert mode".

Thank you for your input anyway.

---

### Post by wpshooter on 2006-12-11
Do I understand correctly that ultimately you want to run just Ubuntu on this machine ?

If so, get the **KILLDISK** program and **WIPE** your hard drive clean and then attempt the install again, making sure that your ALTERNATE CD has been integrity checked by running the verification function found on the initial Ubuntu boot screen menu.
[http://www.killdisk.com/](http://www.killdisk.com/)


Good luck.

---

### Post by howipepper on 2006-12-11
**wpshooter:** Thanks for the info, I'll look into it.

As an update to my first post, I was running Ubuntu Edgy exclusively.  No Windows.  I wiped Windows off of the computer when I first received it, and replaced it with Ubuntu.  I had been running Ubuntu since the day Edgy came out.

It is only after I reinstalled Edgy that it wouldn't boot.  I tried everything I could think of, and it wouldn't work.

I only installed Windows as a last resort, because I can't afford to be without my computer.  The coding I do can be done on either Windows or Linux.

---

### Post by howipepper on 2007-01-15
As a final close-out to this problem, I was never able to get Ubuntu to boot after install, using Grub as the boot loader.  It didn't matter what I did or tried, it just wouldn't work.

The final time I reinstalled Ubuntu, I skipped Grub and installed Lilo as my boot loader.  Needless to say, my system now boots into Ubuntu and runs fine.  I don't know what the problem was with Grub and my hard drive (SATA, 160 GB), but they just wouldn't play well together.

If anyone else experiences this or a similar problem, I'd love to hear about it.

---

