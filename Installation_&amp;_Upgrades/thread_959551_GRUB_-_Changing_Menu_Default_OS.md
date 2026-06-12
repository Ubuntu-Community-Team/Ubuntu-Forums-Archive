---
title: "GRUB - Changing Menu: Default OS"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by TBerk on 2008-10-26
Can I edit the menu.1st file directly? Or, do I have to use GRUB line commands to alter that file...

I'm dual boot Win2k & Ubuntu 8.04.1 right now and I'd like for it to default to Windows, the last item on the menu. (This allows for the computer to be powered up and default to the OS that currently had internet access.)

Later I intend to default back to HH, or II in the future. For the moment it is a drag to attend the system on boot, every time.


TBerk

---

### Post by ciscosurfer on 2008-10-26
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by The Doell on 2008-10-26
Yes, you can edit the grub menu directly.  

The path is, /boot/grub/menu.lst

Make sure you make a copy of menu.lst before editing :) 

Here is a step by step procedure, to book from another OS.  Hope this helps

[http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/]("http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/")

---

### Post by zvacet on 2008-10-26
You can also install **startupmanager** from synaptic.

---

### Post by ciscosurfer on 2008-10-26
> **zvacet said:**
> You can also install **startupmanager** from synaptic.Which is actually a pretty nice app :)

---

### Post by TBerk on 2008-10-26
Well, I went to the link CiscoSurfer posted and lo & Behold I found what I was after.  Many Thx, returned here and saw more replies- so I'll check out the utility next, but for now I'm a happy ccamper...

btw- I:

- Saved the instructions as text to the local drive.
- Rebooted in Ubuntu.
- Backed up the menu file.
- Edited it to change my default OS from 0 to 4
(I actually rem'd out the default line values and adjusted a copy of each line I was changing.)
- Activated the color scheme to see what it was like, (not bad).
- Save & Exit.

Rebooted and it did what I wanted. 

Thx again,
TBerk


Appended: After connecting to the Internet and getting Updates the menu now defaulted to Item 4 but item 4 was now another OS. 

(Seems the 8.04.1 I installed from CD to Hard Drive had it's Kernel bumped up enough to show as another version to the GRUB menu-ing function.)

Fixed it by editing 'menu.1st' file (again) to point to Item Seven; back to normal.

btw- set hide menu option as well, and set delay to 5 seconds from the default of ten.
-end-

---

