---
title: "Windows is now drive F: instead of Drive C:"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by randell6564 on 2007-10-11
**[COLOR="Red"]Hey Folks![/COLOR]**
I dual-boot Windows XP with Ubuntu.  Always have.  (All Flavors. Currently Feisty Fawn.)
I have always Installed Windows first.  Then Linux.  And as you know, Grub is then automatically installed to the MBR and you get your boot options.,Windows or Ubuntu.
SO..In the past, Windows always identified itself as C: but now is showing as F:
Windows is on my 120Gig IDE master.  Ubuntu is on my 20Gig IDE slave.

The problem that I'm having is that when trying to install hardware like an HP printer,  I'm getting errors that tell me that the installation files are looking for, but not finding C:.  So the installation can never complete.
The last time that I reformatted my 120gig Windows drive, I chose to keep Ubuntu on my 20gig slave, so naturally Windows rewrote the MBR.
This time, I used 'Suber Grub Disk' to reinstall Grub to MBR.  I'm thinking that this might be the problem.  (Why has C: now become F:?)
Any ideas?
Thanks!

---

### Post by kyphi on 2007-10-11
That is one of the quirky things that Windows will do if you do not watch it throughout the installation.  On one screen during the installation it states that it will install to drive F (for example) and if you do not intervene it will just go ahead and install to its chosen drive.  I do not know why it does this.

The only clean way out of this, since you cannot change the drive letter, is to reinstall Windows and make sure that it chooses the desired drive letter.  By clean, I mean that while you can reorganise future software installations to go to drive F, it gets to be confusing to have to remember that all the time if you are used to Windows being on drive C.

The section of Grub that resides on your Windows disc or partition can easily be rebuilt afterwards, especially if you have the Super Grub Boot Disc handy.

To have the two OSs on separate drives is the way to go but Windows would easily function on the smaller drive.

---

### Post by randell6564 on 2007-10-11
> **kyphi said:**
> That is one of the quirky things that Windows will do if you do not watch it throughout the installation.  On one screen during the installation it states that it will install to drive F (for example) and if you do not intervene it will just go ahead and install to its chosen drive.  I do not know why it does this.

The only clean way out of this, since you cannot change the drive letter, is to reinstall Windows and make sure that it chooses the desired drive letter.  By clean, I mean that while you can reorganise future software installations to go to drive F, it gets to be confusing to have to remember that all the time if you are used to Windows being on drive C.

The section of Grub that resides on your Windows disc or partition can easily be rebuilt afterwards, especially if you have the Super Grub Boot Disc handy.

To have the two OSs on separate drives is the way to go but Windows would easily function on the smaller drive.
[COLOR="Red"]Thank You my friend![/COLOR]This makes perfect sense.  I did not think to pay any attention to what drive letter Windows would assign.
As far as reinstalling Windows, I have no prob with that! Actually, now that you mentioned it, all I really have to do is direct any future installations to Drive F:!  YEAH..Thats the ticket!  No prob remembering to do that!
As far as Windows residing on my smaller drive.  Again, Not a problem!  In fact, we are on the same page there!
Thank You Again!  I just needed a 'Fresh set of eye's',  you might say!

---

### Post by kyphi on 2007-10-11
Cheers.

---

