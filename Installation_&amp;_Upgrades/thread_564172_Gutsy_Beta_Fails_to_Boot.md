---
title: "Gutsy Beta Fails to Boot"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by gnuosphere on 2007-09-30
Hello,

I'm trying to install Gutsy Beta on several desktops (at a school) and keep getting the following message after choosing "Start or Install Ubuntu" after the CD boots...

----------------------------
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu4) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(intramfs) [   79.292199] ata1.00: failed to set xfermode (err_mask=0x40)
[114.444837] ata1.00: failed to set xfermode (err_mask=0x40)
[149.597494] ata1.00: failed to set xfermode (err_mask=0x40)
[156.246578] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[156.246631] ata2.00: cmd a0/00:00:00:00:20/00:00:00:00:00/a0 tag 0 cdb 0x12 data 36 in
----------------------------

And then the machines just sit there. I know the image I have of the CD is good.

Any ideas?

---

### Post by dabl on 2007-09-30
Is that the "Live CD"?  I really prefer the Alternate Install CD -- it seems to have fewer of these kinds of issues.

With the Live CD, you might try pressing F6 first, and see if one or more of the boot options will get it to boot.

---

### Post by gnuosphere on 2007-09-30
Yes, it's the Live CD. Any suggestions on what I should change regarding the boot options? I'll download the alternate CD and give it a go though I recall I had the exact same problem when I tried the last release of Gutsy so I'm not holding much hope. As well, I should add I had the same problem when trying to install Feisty on these machines as well.

---

### Post by Gasten on 2007-11-22
Did it work?

---

