---
title: "Lubuntu dual boot: no Windows option after updates"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by pburress on 2011-04-26
I've installed Lubuntu alongside my existing Windows XP installation.  The menu came up on boot allowing me to boot into either Lubuntu or XP.  But, after I install all the Lubuntu updates and restart, the option to boot into XP is gone. The boot menu comes up, but no XP option.  

I reinstalled Lubuntu again with the same results: after the updates, no XP option.  

I am experienced in a Windows environment but not so much Linux, so please keep this in mind!

I'm thinking if I don't get any help here I will reinstall Lubuntu again, and before I run the updates, I will make a copy of grub.cfg for later reference so I can add the XP section in again- am I on the right track here? 

Thanks in advance for any help.

---

### Post by Paddy Landau on 2011-04-26
You need to rebuild grub.

[LIST]
[*] Boot into Lubuntu.
[*] Open a terminal.
[*] Type the following command.
```
sudo update-grub
```
[*]Reboot.
[/LIST]
 Let us know if this works.

---

### Post by Quackers on 2011-04-26
Lubuntu sometimes can fail to install os-prober
Have a look in synaptic package manager and enter os-prober in the search box. If it is installed it will have a green box to its left. If it isn't installed you should install it and then run sudo update-grub in the terminal and as grub.cfg is run you should then see the Windows Loader picked up.

---

### Post by pburress on 2011-04-26
Paddy,That did not work.  It found the Linux image(s) and a memtest86+ but no windows.   I actually did some googling and tried this before my reinstall with the same results.

Quackers, will try that now. Thanks!

---

### Post by pburress on 2011-04-26
os-prober did the trick!  Thanks Quackers!

---

### Post by Quackers on 2011-04-26
Ah, very good :-)
I don't know why it doesn't get installed sometimes.
Please mark the thread as solved using the Thread Tools near the top of the page.

---

