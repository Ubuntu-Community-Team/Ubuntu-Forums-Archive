---
title: "Grub issue on new install"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by chris.olsen on 2010-01-20
I installed ubuntu 9.10 on a new machine.  The install was smooth as usual, but when rebooting after install all I see on the black screen in white text is:

   GRUB _


Any ideas on what the problem is?  

The worst thing is that I am no longer even able to reinstall since it seems to hang before it tries to boot from the cd.

My partition settings are:
- 50GB (/) (ext4)
- 192GB (home) (ext4)
- 8GB (swap)

---

### Post by marmida on 2010-01-20
The installation did not correctly guess your partition layout, and thought the wrong drive would get itself booted.

I don't know how to solve this (I'm on here also looking for a solution to a grub problem), but I do know that you certainly can get back onto a CD boot; the problem is probably that your BIOS has your CD drive set to a lower boot priority than your HD, and thus, you always try to boot from the botched MBR first.  Follow the instructions while your computer is going through POST, and you should be able to get into BIOS and change the boot order.

---

### Post by chris.olsen on 2010-01-21
In regards to the boot priority I already tried to move the cd to the top of the priority list and it still fails to boot.  Unless there is something that I am missed.

** Cancel this.  I tried again this time it worked.  I may have not pressed F10 to save the settings :)

---

### Post by marmida on 2010-01-21
For some reason, it's trying the hard disk first.  I'd look for a "BBS Popup" or other boot device selection menu key (mine is f8 during post); failing that, you could temporarily disconnect the hard drive to make sure the cd is still there (the system should fail with a "no boot device"-style message if it can't find anything to boot from).

e: oh hey you just got it to work, nevermind.

---

### Post by _H3MLOCK on 2010-01-21
Press F2 or Del. just as your system starts up (This key is different for diffferent computers) and get into BIOS, make sure your CD/DVD drive is the highest priority... boot into the livecd... Let us know if you get that far

---

### Post by _H3MLOCK on 2010-01-21
Now mount your ubuntu filesystem and post contents of menu.lst (if any)

if not then reinstall grub (tricky)

---

### Post by chris.olsen on 2010-01-21
Well I figured out the issue :(

I accidentally installed over top a different hardrive that was connected via usb.  I just lost a lot of m*vies.

---

### Post by chris.olsen on 2010-01-21
Thanks for the help.

---

