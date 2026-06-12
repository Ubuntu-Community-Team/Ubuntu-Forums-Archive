---
title: "Can I install Mandriva one 2008 along with Ubuntu Fiesty"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by dvijaydev46 on 2007-12-07
Hi I want to try Mandriva one 2008. There is already xp, vista and Ubuntu Fiesty installed. Can I install Mandriva now? Wont it corrupt the GRUB installed by Ubuntu?

---

### Post by Pumalite on 2007-12-07
It will install a new Grub in your MBR. I'm not sure it will recognize automatically the other OS?s. You might have to edit menu.lst.

---

### Post by banewman on 2007-12-07
I tried mandriva 07 and it didn't recognise the other OS's
It runs from the live cd and will do everything from that including driver installs - just won't save them for the next boot.
:)

---

### Post by AdamWill on 2007-12-07
Unfortunately, Mandriva 2008 doesn't have the ability to find other distros and include them in the bootloader configuration. After installing Mandriva you'd get a bootloader with XP, Vista and Mandriva, but no Ubuntu. It should not be hard to re-add the Ubuntu entry to Grub, though.

We're hoping to add this feature in the next Mandriva release. I believe Ubuntu does have this feature, so if you do it the other way around (install Mandriva then Ubuntu), it works okay.

---

### Post by Eriksmits596 on 2007-12-09
Mandriva 2008 has a graphical interface to add posts in the GRUB menu, so it is very easy to do.

---

