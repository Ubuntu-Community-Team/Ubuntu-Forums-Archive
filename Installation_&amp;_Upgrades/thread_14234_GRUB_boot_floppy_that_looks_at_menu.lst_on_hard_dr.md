---
title: "GRUB boot floppy that looks at menu.lst on hard drive?"
date: 2005-02-05
forum: Installation &amp; Upgrades
---

### Post by Joker23 on 2005-02-05
I looked on Google for a way to make a GRUB boot floppy and found several.  To narrow down the search I included the word 'Ubuntu' to find one more specific to my situation.  That search lead me to:

[http://www.ubuntulinux.org/support/documentation/howto/Randy%20Magee](http://www.ubuntulinux.org/support/documentation/howto/Randy%20Magee)

I followed the how-to step by step and am now booting into Ubuntu with my GRUB boot floppy.  The reason I am using the boot floppy is because my young son likes to play on my computer and when he restarted it, the first option was Ubuntu and Win XP was at the bottom.  He would end up in Ubuntu by mistake more often than not.  I changed my menu.lst to place Win XP at the top, but after one upgrade or another I ended up with a new boot menu that was missing Win XP.  I had saved a backup of the file I had edited, and used it to add Win XP back to the menu.  I'm pretty sure the cause of the new menu.lst was when I added the K7 kernel at one point.

On my computer I have a 160GB HD with Win XP Pro and a 6GB HD with Ubuntu.  The boot floppy has a copy of my menu.lst, and what I'm wanting to do is either alter my current floppy or make a new floppy that will start the boot process by floppy, but then look to the menu.lst in my Ubuntu installation.  That way if I do anything to cause the menu.lst to be altered, it will boot to that new menu.lst instead of the old one on the floppy.

Is there a good way to do this, or should I just get in the habit of copying the menu.lst from the hard drive to the floppy?

Thanks!

---

### Post by Buffalo Soldier on 2005-02-05
There is a way to change the default boot from Ubuntu to WinXP. Refer to: [http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub)

note: X_sequence = the order of the OS on the menu. For example if WinXP is the fifth (5) OS on the menu then your X_sequence should be 4. (start counting from 0).

---

### Post by Joker23 on 2005-02-05
Thanks!

I'll give that a shot and see how it works.

Earlier I had just used cut-and-paste to move XP to the top...  this looks more reliable.

---

