---
title: "Lubuntu CD/USB after install screen shows _ and restarts pc"
date: 2014-12-15
forum: Installation &amp; Upgrades
---

### Post by randy12 on 2014-12-15
[SIZE=4][FONT=verdana]**hi guys m using lubuntu 14.04 from a year on dell gx270 2.8 82865g graphics 2.5gb ram however my clonezilla backup got deleted so i decided to reinstall lubuntu 14.04.1 from live cd/usb the install screen come try lubuntu without installing,install lubuntu etc i tried both of them but after that a black screen comes with a _ and then after 30 secs it shut downs my pc i thought its a iso error so i downloaded puppy linux and it also shut downs my pc i also then reset my bios but no use plz help me i really want to use lubuntu again and right now i'm running xp. :-(**[/FONT][/SIZE]

---

### Post by sudodus on 2014-12-16
1 - Please use the standard font and size in your posts at the Ubuntu Forums

-o-

2 - If I understand correctly, Windows XP works properly, so we can guess that the hardware is still working.

3 - I think there is problem with the graphics, and I would try with an older but still supported distro,

3a. with a light-weight desktop environment based on Ubuntu 12.04 LTS: ***LXLE*** or ***Bodhi*** (Lubuntu 12.04 has passed end of life, but these two distros (o re-spins) promise support until April 2017.

3b. ***Wary Puppy***, which is particularly good for old hardware. (You may have tried another flavour of Puppy Linux.)

3c. You can try again with Lubuntu 14.04.1 LTS and use ***UXA acceleration*** according to this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics)

Maybe you need a boot option, for example **nomodeset** or **text**, to be able to create or edit the file (and then reboot).

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

