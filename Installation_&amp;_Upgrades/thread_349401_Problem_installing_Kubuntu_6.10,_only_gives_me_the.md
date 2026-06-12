---
title: "Problem installing Kubuntu 6.10, only gives me the command line"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by Subterranean on 2007-01-30
I'm relatively new to Linux, though I have installed Ubuntu 6.06 on my old laptop with no problems, so I thought I'd have a go on my new desktop.

I downloaded Kubuntu 6.10 and successfully burned to DVD, when I boot from it I get a menu with install, install text-based etc. If I choose install, the default, I would expect to go into live CD mode, however after a bit of text, and the Kubuntu logo with progressbar, I end up at the command prompt without going into the GUI, basically the terminal, but thats all, like going into dos instead of windows.

I chose the text based install and everything went fine, i partitioned successfully and it installed without a hitch. However if I choose the ubuntu option from GRUB (i kept my XP install) it goes straight to the command prompt again exactly like booting from the DVD.

It seems to me like its working fine other than not being able to load the GUI. Could anyone help me figure out whats wrong? If its useful my system is as follows: intel core2duo E6600, Gigabyte DS4 motherboard, nVidea Gefore 8800 GTS, 2GB Geil 6400 RAM, Seagate 7200.10 500GB HD.

Thanks for any help.

---

### Post by Gorgonzola on 2007-02-13
Unless you chose not to install X in the text based installation, you should be able to type: ```
startx
``` to get a GUI happening.

---

