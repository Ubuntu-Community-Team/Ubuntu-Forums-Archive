---
title: "Uninstallig Ubuntu"
date: 2005-02-18
forum: Installation &amp; Upgrades
---

### Post by Tinuz on 2005-02-18
Last night i tried to uninstall ubuntu after X didn't start and was determined to stay so(Even after trying everything i could find on this forum). Even worse, GRUB wont let me boot my windows system(Unlike the fedora one).
Last night however, it cost me my windows install(Ubuntu kept trying to boot or something).
This time around( I reinstalled this morning to see wether it was an install error which caused the problems) i would like to keep my windows install.

I run from a single HD and used free space to partition for ubuntu.

Thanks in advance.

---

### Post by cyberchills on 2005-02-18
Add this to your /boot/grub/grub.conf /boot/grub/menu.lst
Edit at your convenience:

title=Windows
root (hd0,3)                                                          #change to your windows parti.
makeactive
chainloader +1

Give Linux a chance.  The web is full of ready to read info, take a few minutes to get a broad overview before you attempt anything.

---

### Post by Tinuz on 2005-02-18
[QUOTE=cyberchills]Add this to your /boot/grub/grub.conf /boot/grub/menu.lst
Edit at your convenience:

title=Windows
root (hd0,3)                                                          #change to your windows parti.
makeactive
chainloader +1

Give Linux a chance.  The web is full of ready to read info, take a few minutes to get a broad overview before you attempt anything.[/QUOTE]

I really want to and i have tried multiple times. All to no avail though, only one got as far as a GUI, the rest failed hopelessly before that stage. 
The one with the GUI failed to recognize my graphics card and refused to install mostly anything.

If anyone can give me a well supported Linux distribution which can boot straight away and works without much problems, mail me at [email]mjvdberg@mytweakers.net[/email].
Oh, it would be nice to have something which allows me to deinstall linux without crashing windows(Grub seems to incorporate in NTLDR or something)

I did read by the way, but the support when things go wrong isn't as good as i'd like.
B

---

