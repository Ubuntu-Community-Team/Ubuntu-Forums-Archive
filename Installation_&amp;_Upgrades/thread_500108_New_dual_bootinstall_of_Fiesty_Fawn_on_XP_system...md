---
title: "New dual boot/install of Fiesty Fawn on XP system.. troubles.."
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by uncleben on 2007-07-13
I downloaded a LiveCD of Ubuntu's Fiesty Fawn.  I've used Ubuntu in the past, and have some experience with Unix.

I had issues with my graphics card.  Int 14/Stack errors.  Pulling the carsm disabling quiet splash and acpi=off rectified this.  I got the liveCD to work.  Now onto the install..

I installed Ubuntu on my hard drive.  I get the grub menu and everything runs smooth.  Upon trying to load the kernel, it dies again.  Same INT 14/stack errors.

I'm assuming I have to make the same edits with quiet splash acpi=off, but don't know where/how to do it.

Any ideas?

---

### Post by merlinus on 2007-07-13
Press "e" at the grub menu, arrow down to the kernel line, press "e" again and add (or delete) the parameters.

If this works, then you can edit /boot/grub/menu.lst to add the same parameters to the kernel line, and you will not have to do this manually again.

```

gksudo gedit /boot/grub/menu.lst

```

-merlin

---

### Post by JimmyRiddle on 2007-07-13
In order to edit the start menu if you highlight the entry and press e.  Move to the line with the quiet splash entry (probably the longest one) press e again edit the line and press enter. Now press b to boot.

This is only a temporary solution. To edit the entry permanently you need to edit the the entry in /boot/grub/menu.lst.

hope this helps...

---

