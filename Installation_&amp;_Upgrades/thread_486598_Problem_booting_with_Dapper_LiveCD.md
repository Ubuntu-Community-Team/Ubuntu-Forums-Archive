---
title: "Problem booting with Dapper LiveCD"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by spideysensor on 2007-06-28
hi all
im trying to install Ubuntu on my computer. i have winXP already installed.
The problem is that the liveCD hangs while showing the following message:
"Uncompressing linux...Ok, now booting the kernel  "

i've searched the net extensively but havent found a definite solution.
i've also tried a variety of parameters but none of them worked:

```
linux all-generic-ide
linux pci-nommconf
linux noacpi

```

i think its a problem with my intel DG965RYCK motherboard.:(

**Computer specs:**
intel core 2 duo E6420, DG965RY mobo,
2*512 ddr2 dual-channel memory 
 160 GB hitachi SATA hdd,
40 GB seagate IDE hdd, Sony dvd-ram (atapi)

im thinking of trying Feisty Fawn now. Will it work? Or can i get around this problem?

im new to linux. Any help will be appreciated.
Thanx in advance!

---

### Post by louieb on 2007-06-28
Your on the right track by playing with cheat codes.  Won't know if feisty will boot till you try it.  Linux distros are  funny that way. On one of my machines some CDs will boot   out of the box others I have to use a cheat code. 
Heres a couple of cheat code list for Debian based distros. 
[Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes")
[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")

---

### Post by spideysensor on 2007-06-29
None of them worked!
then got Feisty and it worked out-of-the-box!!

Three days to installing...uh..Finally its over!!
thanx for the help.

---

