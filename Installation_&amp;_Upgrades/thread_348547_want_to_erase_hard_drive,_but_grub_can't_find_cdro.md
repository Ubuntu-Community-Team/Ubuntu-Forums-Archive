---
title: "want to erase hard drive, but grub can't find cdrom drive"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by billtron on 2007-01-28
Hi,

I am at a friend's house trying to get his computer to boot to CD.  Earlier, before I came over, he had put in a 6.10 liveCD and followed all default options to wipe the hard drive and install a fresh copy.  The computer used to have ubuntu, then just winxp.

Now, he can't get the computer to boot from CD, regardless of what CD we put in the machine.  We tried adding a few lines to menu.lst:

title cdrom
root (hd1)
chainloader +1

but we don't know what to put between the parenthesis.  When we put (hd1), we get an Error 21.  When we put (hd0) we get error 23L error while parsing number.  No idea what to do.  We tried (sd1), but now we can't edit it back, and when we try to boot the ubuntu kernel we get error 16, inconsistent filesystem strucure.

This is really frustrating, because all we want to do is erase the hard drive and start anew.  We don't have a floppy drive.  Any help?

---

### Post by logos34 on 2007-01-28
To boot from CD you need to go into the BIOS and change the order of the drives so that the cdrom drive boots first.

---

### Post by billtron on 2007-01-28
the only thing we can do when the computer is starting up is press esc to go to the grub menu, and cdrom is not an option there.  is there another boot menu that we should reach before that?  If so, how do we find the button to press on a computer that uses an asrock conroe motherboard?

---

### Post by logos34 on 2007-01-28
diff boards use diff keys -- try F2 or F6, or start tapping TAB key and then Pause key and/or Delete (my board)...otherwise check asrock site or manual

---

