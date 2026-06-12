---
title: "Grub Installation"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by goodfella on 2006-11-11
I am planning on building a new computer.  I have never done this before but have the confidence that I can do it.  Currently I dual boot windows xp and ubuntu without any problems.  I have windows xp on one hard disk and ubuntu on another.

With this configuration if windows goes down and I reinstall it I believe I will have to reinstall grub to boot into ubuntu.  For my new computer I would like to avoid that by installing grub on both drives but using the same menu.lst.  That way if windows goes down I just have to select the other drive as the first bootable device from the bios screen and it will run from there skipping the drive with windows.  Then if need be I could reinstall grub on the windows drive to get back to my original configuration.

If this seems crazy, unfeasable, or both please let me know; otherwise, if you know of any good documentation please give me some links.  I have already looked at the GNU GRUB manual it was very helpfull.  Thanks for your help.

---

### Post by deepwave on 2006-11-11
In your case, I would:
- figure out which drive is the master (or boot)
- make the ubuntu drive boot first (Optional but easier)
- install GRUB on the MBR (master boot) of the booting drive
- enjoy.

Naturally this is more involved than me just hand-waving.  Spend some time figuring out boot sequences in the BIOS and reading up on installing GRUB manually.  I am not sure Ubuntu will do the GRUB installation automatically, but then again I never tried.

---

### Post by goodfella on 2006-11-11
Thanks, Ubuntu does install GRUB automatically.

---

### Post by ReaderRat on 2006-11-11
These may help:
How To Do Most Anything With GRUB
          **[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)**
[[color=BLUE]**GRUB HowTo**[/color]](https://help.ubuntu.com/community/GrubHowto)
And, if you want to change the boot order;
**[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)**

---

### Post by confused57 on 2006-11-11
I have 2 computers set up this way:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

