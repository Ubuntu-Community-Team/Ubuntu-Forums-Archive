---
title: "Preserving/Moving WUBI install after Windows reinstall?"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by RichStephens on 2010-04-05
I have a WUBI-installed virtual Ubuntu installation on my Windows XP machine.  I am considering upgrading my machine to Windows 7.  As you may know, Windows 7 doesn't like to upgrade Windows XP installs, so I have to wipe and reload everything, and I have a couple of questions:

1) Is WUBI supported on Windows 7?

2) How can I install WUBI and just have it use my current WUBI virtual installation?  Is there a fairly easy way to move it to the new machine?

Thanks,
Rich

---

### Post by Megaptera on 2010-04-05
You could move it to a USB (pen) drive and run it from there.
Guide here:  [http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/](http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/)

Richard

---

### Post by RichStephens on 2010-04-05
> **Megaptera said:**
> You could move it to a USB (pen) drive and run it from there.
Guide here:  [http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/](http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/)

Richard

Thanks for the quick reply, but that doesn't exactly solve the problem. I have plenty of hard drive space to store the install - as a matter of fact, it won't move at all - I just need WUBI on the new Windows 7 installation to recognize and set up the system so I can access it again.  Any thoughts?

Thanks,
Rich S.

---

### Post by new_tolinux on 2010-04-05
I don't know if it's supported, but this is how I should do it:

Back-up the Wubi-folder
Install Windows 7
Install Wubi (for the boot-loader etc.)
Overwrite the new Wubi folder with the one you've backed up.

---

### Post by RichStephens on 2010-04-05
> **new_tolinux said:**
> I don't know if it's supported, but this is how I should do it:

Back-up the Wubi-folder
Install Windows 7
Install Wubi (for the boot-loader etc.)
Overwrite the new Wubi folder with the one you've backed up.


Yes, that's the big question.  If I do that, will it work.  It'll be on the same drive, etc.  The other big question is whether WUBI itself is supported on Windows 7.  The wubi-installer web site doesn't say it supports Windows 7.   Well, we'll see I guess.

---

### Post by new_tolinux on 2010-04-05
> **RichStephens said:**
> Yes, that's the big question.  If I do that, will it work.  It'll be on the same drive, etc.  The other big question is whether WUBI itself is supported on Windows 7.  The wubi-installer web site doesn't say it supports Windows 7.   Well, we'll see I guess.
I have the 10.04 Wubi on Win7 without any wubi-related problems. Only (at first) some driver-issues with my graphics card, but that's most likely related to noveau (the new open source nvidia driver).

---

### Post by conradin on 2010-04-05
I think new_tolinux has the right idea. Whether it works or not, you wont loose any data that way.

---

### Post by bcbc on 2010-04-05
You just back up the c:\ubuntu\disks\root.disk file, and then replace the one you get when you re-install wubi under Win7.

---

### Post by Mark Phelps on 2010-04-05
> **RichStephens said:**
> ...  As you may know, Windows 7 doesn't like to upgrade Windows XP installs ...

That is true -- but only as far as MS is concerned.

LapLink makes a product that will allow you to do an in-place upgrade from XP to Win7.  While in-place upgrades are generally NOT recommended, for the low price of their product, you could try it out (be sure NOT to enter the product key when upgrading) and see how well it works -- BEFORE you take on the task of backing off and reinstalling everything.

---

