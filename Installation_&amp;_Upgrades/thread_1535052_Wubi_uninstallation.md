---
title: "Wubi uninstallation"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by mbajaj on 2010-07-20
Hey guys,

So I switched to Ubuntu about a month ago and have been loving every bit of it so far! Today, I decided it was time to switch from having ubuntu installed within windows (through wubi) into creating a separate partition for itself.

I tried UN-installing using the wubi-uninstaller file but that did not work. Tried removing from the Add/Remove box in Windows 7 but neither wubi nor ubuntu were listed. SO I ended up manually deleting ubuntu from the C: and then using EasyBCD to remove Ubuntu from the boot menu.

It may all sound great but I noticed that my hard disk is missing around 25GB of space. I even re-installed windows 7 but that hasn't changed this. It may well be that my hard disk is just old (~2 years) but I think it maybe because of an incorrect UN-install of wubi. Having read through forum posts around the interwebs all evening, this seems to be a problem that a few people share. Any help is appreciated!

ps: I intend on installing Ubuntu again once this hard disk issue is resolved!

---

### Post by Frogs Hair on 2010-07-20
In my case  Ubuntu was listed in add and remove programs , but the Ubuntu folder was not in program files.When I clicked computer and disk C in W7 some folder options were listed , the driver folder among others , this is where the wubilder file and the Ubuntu file were located . My disk space was restored Upon removal.

I also used a utility to wipe the free space on my hdd after removing the Wubi install . When using Wubi most of the files are hidden to windows, even my anti virus reported  them as hidden. As for Wubi installer I had saved it to downloads so it was easy to locate. If you have reformatted your drive I'm not sure why the space was not returned .

---

### Post by gordintoronto on 2010-07-20
> **mbajaj said:**
> It may all sound great but I noticed that my hard disk is missing around 25GB of space.


How big is your hard drive? Are you aware of the discrepancy between GB and GiB?

---

### Post by mbajaj on 2010-07-21
I had to look up the definition of GB vs GiB. My hard disk is 250 GB according to the manufacturer but I understand that these values are usually reduced by about 7-10% when figuring out actual space. At the moment the C: says it has 177/233 GB free. I only have about 10 GB of actual used space in the C: so that still leaves (233 - 187 = 35 GB) of unexplained space.

@ Frogs Hair - I didn't actually re-format the drive itself, just re-installed windows 7. what utility did you use to clear out the free space from the HDD?

---

### Post by mbajaj on 2010-07-21
problem solved!

i used the disk cleanup feature in windows 7 and selected the remove 'system restore and shadown copies' and 35 GB of space was freed up. Now i'm not sure if this space was my previous ubuntu copies or a system restore of windows 7 (doubt it), but either way - i am 35 GB richer :)

thanks for your help

---

