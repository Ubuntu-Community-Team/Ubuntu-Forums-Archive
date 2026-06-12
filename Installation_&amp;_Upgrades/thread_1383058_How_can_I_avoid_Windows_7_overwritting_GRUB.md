---
title: "How can I avoid Windows 7 overwritting GRUB ?"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by ASCHYIEL on 2010-01-16
Hi,

My Question :
Why does Windows (7) [over-]write the MBR [pseudo-randomly]?  And what settings can I change to prevent that?

Background :
I used to dual-boot Ubuntu and Windows-7 on my gaming-laptop, but periodically I run into GRUB-got-messed-up-please-fix-me-again welcome screens.
Using google, I can find lots of how-to guides on restoring GRUB, but no obvious ones on how to avoid messing up GRUB in the first place.
Whats interesting to note;  I have another work-laptop that dual-boots Windows XP and Ubuntu just fine (for the past year) and have never run into any GRUB-got-messed-up-please-fix-me-again situations.

My Hypothesis :
I have a hunch that Windows 7 writes to the MBR for enabling Restore-Points.

Thanks in advance,
-Aschyiel

---

### Post by ASCHYIEL on 2010-01-22
Also, a 2nd (completely unsupported) guess;

Windows Updates.

---

### Post by Sef on 2010-01-22
> Why does Windows (7) [over-]write the MBR [pseudo-randomly]?  And what settings can I change to prevent that?

Other than not installing Windows, I do not know a way you can avoid that issue.  Windows does not give you a choice about installing an MBR or not.

---

### Post by meierfra. on 2010-01-22
maybe it is not the Windows OS, which is causing the problem, but some random program you have installed, Check out this link:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

---

### Post by ASCHYIEL on 2010-03-22
...

[https://bugs.launchpad.net/debian/+source/grub2/+bug/441941](https://bugs.launchpad.net/debian/+source/grub2/+bug/441941)

[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)

---

### Post by wilee-nilee on 2010-03-22
> **ASCHYIEL said:**
> ...

[https://bugs.launchpad.net/debian/+source/grub2/+bug/441941](https://bugs.launchpad.net/debian/+source/grub2/+bug/441941)

[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)


Been running W7 and Ubuntu dual-booted and have never had this happen. A install of either will will rewrite the MBR. Are you referencing a problem with a wubi install?

---

### Post by theozzlives on 2010-03-22
Windows 7 may detect a startup problem and re-write the MBR. You got to figure out what's causing this startup problem. Maybe a boot sector virus?

---

