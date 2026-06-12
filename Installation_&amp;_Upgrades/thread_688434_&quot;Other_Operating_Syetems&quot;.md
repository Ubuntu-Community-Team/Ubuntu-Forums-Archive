---
title: "&quot;Other Operating Syetems&quot;"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by tom_the_drummer on 2008-02-05
Origionally I had windows XP home on my laptop. Formatted disk, re-installed it, then Ubuntu 7.10. Ubuntu 7.10 was at the top of the list as the default os and XP was under other operating systems. Fine.

Installed ubuntu studio and that has taken priority as default os and windows and ubuntu 7.10 are listed under "Other operating systems".

How can I set Ubuntu 7.10 back as the default OS?


Thanks for the help!


Tom

---

### Post by 7llusion on 2008-02-05
Yes, just edit your grub boot file:
[URL="https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS"]https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS
[/URL]
Or you could try startup manager for a gui solution:
[apt://startupmanager]("apt://startupmanager")

---

### Post by tom_the_drummer on 2008-02-07
I've tried both of those solutions.

And neither have worked.

It still boots up Ubuntu studio when left.

---

### Post by plucky on 2008-02-07
tom_the_drummer,

Where did you edit the **/boot/grub/menu.lst** file?

Can you open a terminal and copy and paste the output of these commands ```
sudo fdisk -l
```that is lowercase L not 1and ```
cat /boot/grub/menu.lst
``` when you have booted into Ubuntu Studio.

Thanks.

---

