---
title: "No grub showing on start up"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by maeske on 2011-09-23
I have a Samsung N220 with Windows 7 on it. I just installed Ubuntu 11.04 alongside windows on the other partition D:
Installation was successful but with restart there is no possibility to choose for Ubuntu. Windows is just loading. Can anybody give me some solution to get the screen where I can select which OS I want?

---

### Post by Quackers on 2011-09-23
Welcome to UF :-)
Where did you install grub to? It appears it may not have been the default option, if Windows still boots directly.

---

### Post by R3cKL3SS_aM on 2011-09-24
My guess is that you installed Ubuntu 11.04 with either a USB or a boot disc, as I had the same problem myself installing 10.04 with a USB, make a long story short it was a waste of my time re-installed windows twice erasing my whole HDD both times, trying to solve the problem (Never done so with a boot disc so I can't speak here) but NEVER AGAIN with a USB. 

I highly recommend using the windows installer aka Wubi.exe as it's noob friendly and there's virtually no way to mess up. Here is a link to the [_*Windows-installer (Wubi)*_]("http://www.ubuntu.com/download/ubuntu/windows-installer")

Some people dislike using the windows installer, me personally found it hassle free and very quick.

Hope this helps.

---

### Post by bcbc on 2011-09-24
If you installed on D: I assume it's a Wubi install.

Right click on Computer, Properties, Advanced, Startup & recovery settings. Check that the Time to display operating systems is not set to zero - set it to 10 if it is.

---

### Post by Rubi1200 on 2011-09-24
If for some reason the suggestion by bcbc doesn't work then please post the results of the boot info script.

There is a link at the bottom of my post with instructions.

Thanks.

---

