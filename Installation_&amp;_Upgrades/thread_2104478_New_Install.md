---
title: "New Install"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by fablish on 2013-01-13
The os I have is new ubuntu. Now each time I log in all i get is orange desktop screen.  I made sure when it was installed that I ran it for lastest updates, so I am for unsure of reason why it is that I have only orange screen.

The only thing that has come is application Compiz close unexpectedly. What ever that means???????

I like to know how I fix it so at least I can have desktop back.

---

### Post by dino99 on 2013-01-13
you might have a better result if you remove "splash" from the boot line:

while you get the grub menu (hit "shift" key at bios end process to get it on a single OS installation), select the boot line to edit it (hit E key), and remove "splash" at the end of the line (or both "quiet splash"), then hit ctrl+c to continue booting.

that way you get the verbose mode letting you know about the possible error(s) while booting.

---

