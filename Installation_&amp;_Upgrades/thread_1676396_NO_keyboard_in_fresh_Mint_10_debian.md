---
title: "NO keyboard in fresh Mint 10 debian"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2011-01-27
Hi,
I did a fresh install of Linux Mint 10 Debian/Gnome/386 on an old laptop.
Installation completed flawlessly, yet after reboot (into the fresh installed Mint) I encountered the following problems:
[LIST=1]
[*]Upon loadinding gdm I get the following error message: " Loading OAFIID: GNOME_IndicatorApplet failed". I chose to keep (rather than delete).
[*]Wrong (larger than actual LCD screen) desktop - known Xorg problem with S3 graphic chip -I know how to fix this.
[*]While I can login in to my user account, and type the password, once I've logged in, the keyboard won't function- no characters appear whatsoever when I try to type in terminal, firefox and the like. Alt+Ctrl+F1/2/3.. won't open a non graphic terminal as well. Thus I can't look at dmesg/log files, nor fix X. I would like to point that the keyboard was fully functional during install and during entering user's password.
[/LIST]

Please advise how do I get a functional keyboard and how do I fix the first problem.

Thanks

---

### Post by TBABill on 2011-01-27
Probably best to join the Mint forums and ask the question there. Since you are using Mint Debian (I think...you also mentioned "10" which is based on Ubuntu), the method of fixing, becoming root (using "su" command, not sudo as in Ubuntu and Mint based on Ubuntu) and other things are slightly different. The forum is very friendly and there are many LMDE users there (I'm one of them) who can assist. Asking here would likely lead you in a wrong direction since Ubuntu and Debian are different because Ubuntu adds a great deal to how the distro functions (hardware installation, drivers, repos, use of PPAs, etc).
 
Hopefully my message didn't come off as disrespectful in any way. I just don't want to see you misled by great intentions because of the differences between Mint 10 and Mint Debian, which will affect how you tweak and manage your system.

---

