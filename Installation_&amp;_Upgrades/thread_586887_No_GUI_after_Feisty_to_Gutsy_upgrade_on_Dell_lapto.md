---
title: "No GUI after Feisty to Gutsy upgrade on Dell laptop"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by Joaz banbeck on 2007-10-22
I tried to upgrade to Gutsy on a Dell Inspiron 1420 laptop that had factory loaded Feisty.  The intallation appeared to be flawless; there were no error messages.  Everytime a dialog box came up I clicked on 'yes' or 'OK'.  :oops:

It boots ok, with no error messages. But I have no GUI, just a command line.

I suspect that I let the upgrade overwrite some config files that are particular to Dell.  I further suspect that those files are on my Feisty CD, but I have no idea what they might be.

So, I have several questions:

1) Is my guess of overwritten files correct?  If not, what did cause this?

2) What are the file(s), and what should they contain?

3) If I need to load old copies off the CD, how do I do it?  ( It has been 20+ years since I used 'mount' ).

Thanks

---

### Post by NilsE on 2007-10-22
Before you try anything else do the following at that command line

sudo dpkg-reconfigure -phigh xserver-xorg

This will reset your xorg.conf for video so select the correct video driver.  If you are not sure try them in this order then reboot:

intel
i810
nv
vesa

If this does not work come back with more details on what errors you may be seeing, what video, audio, processor etc. you have.

---

### Post by ljonesj on 2007-10-22
does it want you to login if it does login then type startx and it should take you to a gui

---

### Post by Joaz banbeck on 2007-10-22
Thanks, guys.  

Startx generates error messages, one which says that it is looking for an I810.  So that tells me where the problem is. ( A 1420 uses an Intel video chip )

I then used dpkg-reconfigure to fix it.

So I have a GUI up and running with only one little problem that I think I can fix.

---

