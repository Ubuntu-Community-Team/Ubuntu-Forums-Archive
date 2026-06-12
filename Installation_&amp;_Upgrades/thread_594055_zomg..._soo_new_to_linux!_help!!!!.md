---
title: "zomg... soo new to linux! help!!!!"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by krebzepplin83 on 2007-10-27
okay im trying to install the drivers for my sound card... and its says this.... what the hell does it mean? lol 
Installation
------------
1. As root type:

	make install

2. Add a new reference to the driver in /etc/modules.conf:

	alias sound emu10k1

3. Play some sound. The module should be auto-loaded.

Note for Debians' users: use /etc/modutils directory,
   create file emu10k1 here with the same content as is suggested in
   the paragraph (5.) and run update-modules afterwards - this
   will create the correct /etc/modules.conf file)
please help me out... i have a few more questions... like how do i install steam so i can play counterstrike? and world of warcraft? and maybe even maple story? please help<3

---

### Post by ddrichardson on 2007-10-27
> **krebzepplin83 said:**
> okay im trying to install the drivers for my sound card... and its says this.... what the hell does it mean? lol 
Installation
------------
1. As root type:

    make installOpen a terminal and type```
sudo make install
```From the folder you put the driver source in.

> **krebzepplin83 said:**
> 2. Add a new reference to the driver in /etc/modules.conf:

    alias sound emu10k1From the terminal```
gksudo gedit /etc/modules.conf
```However that's not used in Ubuntu so you need to type```
gksudo gedit /etc/modutils/emu101k1
```Then you can add the line```
alias sound emu10k1
```> **krebzepplin83 said:**
> please help me out... i have a few more questions... like how do i install steam so i can play counterstrike? and world of warcraft? and maybe even maple story? please help<3

Look into using a program called Wine, there are whole threads on it. Also welcome to Ubuntu - try to keep each post to one question!

---

### Post by krebzepplin83 on 2007-10-27
> **ddrichardson said:**
> Open a terminal and type```
sudo make install
```From the folder you put the driver source in.

From the terminal```
gksudo gedit /etc/modules.conf
```However that's not used in Ubuntu so you need to type```
gksudo gedit /etc/modutils/emu101k1
```Then you can add the line```
alias sound emu10k1
```

Look into using a program called Wine, there are whole threads on it. Also welcome to Ubuntu - try to keep each post to one question! thank you

---

