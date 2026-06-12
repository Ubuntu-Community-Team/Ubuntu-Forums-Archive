---
title: "[SOLVED] Ubuntu Fresh Install - problems"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by dave00001 on 2007-12-10
Hey all,

I'm new to both linux and forums, so forgive me that I posted this in both this section and the "absolute beginners" section...

I'm currently running a kubuntu distribution on my pc (no windows partition) and am trying to get a fresh install to ubuntu 7.10 fiesty fawn..  The only problem is that I can't get it to boot from my installation cd (iso image).  I know it must have something to do with my /boot/grub/menu.lst file, but I don't want to mess anything up until I get some second opinions..  so if anybody knows what I should do can you let me know?!?

Thanks in advance!

---

### Post by PmDematagoda on 2007-12-10
The problem must with the BIOS being improperly configured, go into the BIOS and then change the Boot Device Priority so that the CD-ROM is at the top.

You should be able to enter the BIOS by pressing the Delete key or F2 key when the PC starts up.

---

### Post by dave00001 on 2007-12-10
I couldn't figure out how to get into the BIOS setup..  I could only see the GRUB loader... but it's going now!  Thanks!

---

