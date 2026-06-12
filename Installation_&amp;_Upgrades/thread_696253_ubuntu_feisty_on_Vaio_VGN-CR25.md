---
title: "ubuntu feisty on Vaio VGN-CR25"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by erikringmar on 2008-02-13
I just bought this new Vaio computer, very nice, but I can't install Ubuntu on it.  Xorg doesn't start and I'm booted off the the command line.  Trying xstart gives me an error message:

[INDENT](EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.[/INDENT]

Any idea how I can get this started?

yours,

Erik

---

### Post by erikringmar on 2008-02-13
Ive made some limited progress.  I'm trying to reconfigure the Xorg server with:
[indent]sudo dpkg-reconfigure xserver-xorg/INDENT]

Going through the menus, I've changed the second window ("Configuring Xserver-xorg). 

If I change the default "Vesa" to "VGA" and change the "depth" in a subsequent menu to 8 rather than 24, I can load Feisty.  

The only problem is that I only see a small fraction of the screen -- super big!

The good news is that this indeed is a Xorg problem.  The bad news is that there doesn't seem to be a driver that can run the screen properly.

Any ideas?

Erik

---

### Post by erikringmar on 2008-02-14
Apologies for bumbing this topic.  My brand new 1300 dollar machine isn't going anywhere.  And I'm not installing Windows on it again.  It's a pretty attractive paperweight though.

---

