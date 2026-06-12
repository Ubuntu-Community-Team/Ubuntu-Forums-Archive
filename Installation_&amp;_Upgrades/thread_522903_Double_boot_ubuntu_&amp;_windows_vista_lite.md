---
title: "Double boot/ ubuntu &amp; windows vista lite"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by zero-Tolerance on 2007-08-11
i had ubuntu 7.04 with Windows xp, well i just installed windows vista lite 4.0, and now i can't load in ubuntu, i used a program named, easyBCD 1.6 and it supposed to add an entry to vista's boot, but it didn't work. So if there is any way to recover the grub, please tell me.

btw.
I am using a notebook latitud d610 with intel centrio 2.13 ghz and 1gb ram.

Thanks for the help

---

### Post by MQMike on 2007-08-11
***   The definitive dual-booting guide: Linux, Vista and XP step-by-step
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)


Reinstall GRUB:

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)


I’m guessing that you can probably get into EasyBCD editor and force it to include an entry for Ubuntu.
Or, you may have to edit your old GRUB boot menu (/boot/grub/menu.lst)  to include and entry for Vista.

---

### Post by zero-Tolerance on 2007-08-11
i forced an entry with EasyBCD but i had a error when i tried to log into ubuntu, i think i'll try to edit my old grub boot menu

---

### Post by MQMike on 2007-08-11
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

(Scroll down to editing the menu.lst; scroll through the posts following the first for a note about Vista’s boot entry (basically, just use rootnoverify (hdx, y) instead of root (hdx, y) in the Windows Vista boot stanza in menu.lst).  It’s for Kubuntu, but just use   sudo gedit /boot/grub/menu.lst for Ubuntu.)

---

### Post by merlinus on 2007-08-11
> 
sudo gedit /boot/grub/menu.lst for Ubuntu
Best to use gksudo for graphical apps run as root.

More info here:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

-merlin

---

### Post by MQMike on 2007-08-11
Happens every time.
I knew if I let it go as sudo, someone would call me out to the woodshed!

Yes, indeed, gksudo for graphical apps . . .  :)
--Mike

---

