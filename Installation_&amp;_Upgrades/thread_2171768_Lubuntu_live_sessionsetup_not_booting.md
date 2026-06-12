---
title: "Lubuntu live session/setup not booting"
date: 2013-09-01
forum: Installation &amp; Upgrades
---

### Post by Yasashii on 2013-09-01
Recently I got an old PC, manufactured back in 2006, from my friend because he bought a new one and wanted to throw this one out.

I've decided that for the time being, I will use it as a storage device. For that job, I wanted to employ a Linux system so that I don't have to seek out the drivers on my own (I don't have any CDs or manuals for it) and since it's an oldie, I though a lightweight distro like Lubuntu will fit the bill nicely.

And here's my problem: Lubuntu 13.04 is apparently too modern to boot properly on this machine. In fact, every reasonably new system is. This is what happens:

The CD boots up, the menu shows up. However, when I choose "Try Lubuntu without installing" or "Install Lubuntu", the screen goes blank, the drive stops reading from the CD and it stays that way forever.

In an attempt to fix the problem, I tried out several DVD and CD drives. No improvement. After that, I tried several other Linux disc I had and every one behaved the same way. I was in a dead end since there was no error popping up which would give me a lead. Finally I put in a Windows 7 disc and received a code 5 cdboot error.

I googled it and it turns out that this occurs on some old Asrock and MSI motherboards because the BIOS can't handle new kinds of booting up. The machine happens to have an MSI motherboard with ami bios version 3.31 a.


With Windows, the solution is simple: a floppy disc boot. Unfortunately, I have no idea what to do with Linux systems in this situation. Any ideas?

---

### Post by Quackers on 2013-09-01
Try the nomodeset boot option described in the thread below.
[http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by Yasashii on 2013-09-01
It worked!

Thanks a lot!

---

### Post by Quackers on 2013-09-01
That's good then :-)
Don't forget that if you install it you will need to boot with the same boot prompt but it is accessed in a different way. Keep that link as it explains how to do that and also how to make the change permanent, if required. Often the installation of an appropriate graphics driver will negate the need to use the nomodeset boot option.

---

