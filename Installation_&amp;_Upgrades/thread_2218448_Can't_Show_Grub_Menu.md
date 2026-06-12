---
title: "Can't Show Grub Menu"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by JerryC on 2014-04-20
Two years ago I installed 12-04 along side windows 7.0.  It has been running well until today.  When it got to the grub menu, I started linux and it displayed a message on the splash screen which said something about a problem with the tmp file couldn't find a disk (or something like that) with a list of choices.  I picked "press M for manual" and it went to my desktop like always.  Later it wouldn't let me select log out, so I picked switch user and the shut down and restart so I could go to windows.  It went through the reboot and displayed an error:
-------------------------------------------------------
ERROR: No Configuration file found
No DEFAULT  or UI configuration directive found.
boot:
--------------------------------------------------------

What do I do to get my grub menu back?  The last couple of days I have changed my desktop choice about three times, but I can't believe that messed anything up.

JC

---

### Post by grahammechanical on 2014-04-20
> [COLOR=#000000]The last couple of days I have changed my desktop choice about three times, but I can't believe that messed anything up.[/COLOR]

I can believe it. Conflicting configuration files. I once tried installing a few alternative desktops. Never again. I re-installed but as that was just an experimental Ubuntu in another partition it was no trouble to me.

Just to confirm. Do you not get a boot menu? Does the machine now boot straight into Windows 7? Please confirm that it was the Grub boot menu that you were seeing and not some Windows boot loader. Otherwise this advice will take out your Windows boot loader. And I would not advise doing this if you installed Ubuntu inside Windows using Wubi.exe.

Run a Ubuntu live session and at the desktop use the File Manager to open the hard disk. That will mount it. Then open a terminal and run.

```
sudo grub-install /dev/sda
```

That will re-install Grub into the MBR of sda.

Regards.

---

### Post by JerryC on 2014-04-20
That is correct, I do not get a boot menu.  It does not boot straight into windows. It is not the grub menu that I am seeing.  All I am seeing is what I posted in the original message.  I do not know where that message comes from.  Ubuntu is not installed using wubi. Ubuntu and windows are installed side by side.  So do I go ahead and do the grub install?  I have several linux versions on USB that I can boot from.

---

### Post by JerryC on 2014-04-25
Sorry it took so long to get back.  I waited til Monday and tried starting my laptop again. This time it let me boot up to Ubuntu 12-04, but some things weren't quite normal.  It did let me get my two most important programs off; Quicken and my vehicle records software.  Then I ran Gparted and removed the partition and recreated it.  I have installed Xubuntu and all is working well now.

JC

---

