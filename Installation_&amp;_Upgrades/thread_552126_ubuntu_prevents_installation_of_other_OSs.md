---
title: "ubuntu prevents installation of other OSs?"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by jabzwnein on 2007-09-16
I have ubuntu on one of my computers and I want to install another Linux distribution over it, effectively erasing the harddrive.  But, for some reason, none of my live CDs for any other distro (even Windows) will boot.  The CDs are fine and have worked before on this computer, so that's not the problem.  It seems that Ubuntu and/or grub is effectively preventing anything else from booting.  I configured BIOS to start with the CD-rom drive, but, after spinning the CDs for a few seconds, grub kicks in and loads Ubuntu.  How can I get Ubuntu off this computer?

(btw, I run Ubuntu on my other computers, but I need to erase this installation and start over.)

---

### Post by K.Mandla on 2007-09-16
You might want to low-level format the drive first; I can't imagine how or why, but I suppose it's possible that grub is interfering with the boot. Look around for a copy of [DBAN]("http://dban.sourceforge.net/"), or [Killdisk]("http://www.killdisk.com"), which is what I use.

---

### Post by mocoloco on 2007-09-16
It's not Ubuntu my friend.  Your system should attempt to boot from the CD before it touches the HD, so nothing on the HD should affect that.  
I had an issue a few months ago where I couldn't boot from a liveCD.  Then I tried just to read a CD under Ubuntu and it wouldn't read the disc.  Checking my BIOS the primary slave (where CD-ROM connects) was disabled.  I changed it to auto and now things work.  Not sure how it changed :confused:.
Something's wrong with your drive or BIOS.  If you wanted to be really sure it's not Ubuntu you could disconnect your HD :).

---

### Post by LLauranzonIII on 2007-09-16
I would try using something like DBAN first.  Just to make sure you have a nice clean fresh start on the HDD.

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by jabzwnein on 2007-09-16
Thanks, but neither of these methods worked.  Adjusting the BIOS only caused the BIOS not to load at all (I switched primary slave to auto, which caused it to say "unknown device" and it would boot).    This is very strange...

---

### Post by mocoloco on 2007-09-16
I would seriously just open the thing up and disconnect the hard drive, just to be sure it has nothing to do with the drive.

---

