---
title: "CD read on startup !?!?"
date: 2008-09-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dawynn on 2008-09-02
I have no splash-screen in Intrepid right now.  That allows me to see the messages scrolling past.  I see several messages related to drive SR0, which in effect tell me that something's not right with either my CD-ROM or the disk in my CD-ROM.  But when I go to /etc/fstab, both of my CD-ROM / DVD-ROM drives are set to not auto-mount.  Why is it bothering to even investigate whatever this SR0 is?  Within a few seconds it passes and continues on its merry way.

Do I need to investigate something here?  Is this normal activity that I can safely ignore?

If it helps, this system has been upgraded a few times.  Probably originally a Feisty Fawn build.

---

### Post by Robertjm on 2008-09-02
Is your computer set to have it attempt to boot the CD first? If so, log into the bios and change the boot cycle to HDD0/1 as first device, and then the CD second.

At least I'm hoping I'm understanding what you're asking.

Later,

Robert

---

### Post by dawynn on 2008-09-02
Yes, but we're past that stage.

It attempts to read the CD first (as I want it too) -- but that's all before it hits grub.  No, at this point, I've chosen the 2.6.27-2 kernel in grub, and its booting.  And at some point in there, it tries to read from some SR0 reference -- which evidently its interpreting as my first CD drive.  But I don't have anything in /etc/fstab called SR0, and the CD-/DVD-ROM drives are all set for no auto-mount.

---

