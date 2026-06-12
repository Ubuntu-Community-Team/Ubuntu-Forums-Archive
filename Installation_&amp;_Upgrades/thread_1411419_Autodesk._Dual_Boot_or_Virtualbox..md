---
title: "Autodesk. Dual Boot or Virtualbox."
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by urepedese on 2010-02-19
Which is likely to be better for Autocad, Revit and 3DStudioMax. Also use Photoshop, Indesign and Illustrator. 

As a mature architecture student with 1.5 years under my belt. I have just built a new computer for this CAD work and have just set it up to dual boot with Ubuntu. But I am wondering if a VM might work for me, although I have heard they slow the CAD programs down.

Also I have set up my system with two hard drives, one for the OS and the other for storage. I intend to image each drive and store it on the other for backup. Would I be better with one OS on each disc? or stick with what I have.

**Although I am aware of Gimp, I have photoshop and know how to use it well so will stick with it for now.

---

### Post by quixote on 2010-02-21
It's a good idea to have the OSes on the primary disk.  It makes the grub setup easier.  So having OSes on one, data on the other sounds like a good set up to me.  I'm not so sure about backing each one up to the other.  If things fail -- which is when you'll want the backups -- your backups are on the same machine and could well have failed too.  Not so good.  I'd suggest backing up to a third, external harddrive, or a network drive if you're on a network.

As to vm versus dualboot.  I've run Photoshop in virtualbox, and I'd say both it and Windows itself actually runs faster and better under vbox than natively.  ??  Who knows why.  That said, if I remember right, Autocad used to require a dongle once upon a time, didn't it?  If it still does, I'm not sure how virtualization will deal with hardware authentication.

The advantage to virtualization is that with a sufficiently powerful machine you can have your vm and your linux programs running together and it takes no time to switch between them.  Getting the vm to share specific linux directories is a bit tedious.  Otherwise it sees only its own vm directories.  But you only have to do it once.

The disadvantage is there might be incompatibilities.  If it were me, I'd try it all in virtualbox.  If there were problems, then I'd go the whole dual boot route.  But there probably won't be.  Virtualization works amazingly well.

---

