---
title: "help with grub"
date: 2006-05-18
forum: Installation &amp; Upgrades
---

### Post by illfilles on 2006-05-18
Been using ubuntu on my desktop as a replacement for windows. After making a few recent hardware changes I think I am ready to reinstall XP... but I can't seem to get the system to reboot from my dvd-rom drive. Can someone tell me if I am missing a feature of the GRUB loader that allows me to do this... or should I be looking at something that happens before GRUB does it's dirty deeds...

any help would be appreciated.

---

### Post by aysiu on 2006-05-18
Where you boot from (DVD-ROM, hard drive, USB key) is defined in the BIOS, not the boot loader (Grub or otherwise).

---

### Post by Sef on 2006-05-18
To get into the BIOS to change the boot order, you have to press a button at the beginning of the boot up.  Usually this button is either **esc, F2, or delete**.  It will tell you in the beginning what button to push to get it to go into the BIOS.  Keep pushing it until you go in.  Be careful about changing other things in the BIOS though.  

Your Boot order should be

1) DVD-ROM

2) Floppy (if you have one)

3) Hard Drive

---

### Post by illfilles on 2006-05-18
whoa... sorry... kind of had a brain fart there and missed a prompt.

thanks

---

