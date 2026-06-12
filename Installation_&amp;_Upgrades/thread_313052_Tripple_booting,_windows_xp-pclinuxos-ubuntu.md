---
title: "Tripple booting, windows xp-pclinuxos-ubuntu"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by ilanesh on 2006-12-05
I have installed windows xp and pclinuxos on my machine, pentium 4, on two seperate harddrives, so i tried to install ubuntu together on the same harddrive with pclinuxos. The install went fine, but then when finished to install, it could read windows and pclinuxos and ubuntu, but I couldn`t boot up on anyone of the 3 distros. Grub error, so I tried it so many times, but it would not work.
Any help would be appriciated.
Would it be easier when installing it with LILO? I have the ubuntu dapper drake live cd.

---

### Post by louieb on 2006-12-05
What error? 
Does it display the grub menu?
If not see link in signature below.

---

### Post by ilanesh on 2006-12-05
it shows only up on boot, 

ubuntu
pclinuxos
windows

and then when i click on them no booting, 
it is not doing anything,
only grub error, that asll. not more.
I am puzzeld.

---

### Post by louieb on 2006-12-05
I would like to help. But I need some information from you.
Lets start out by you posting here the display of fdisk -l. [LIST]
[*]Boot your PC with the Ubuntu live CD
[*]Open a terminal window (Applications>Accessories>Terminal)
[*]at the command type ```
sudo fdisk -1
```
[*]copy the output fdisk printed to the clipboard
[*]and paste it into your next post.
[/LIST]
Also if you can please post the content of file /boot/grub/menu.lst

---

