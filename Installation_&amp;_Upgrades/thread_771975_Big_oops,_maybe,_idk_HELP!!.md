---
title: "Big oops, maybe, idk? HELP!!"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by mjp216 on 2008-04-28
okay, ill start off blunt.

when i turn my (Acer 4620z) laptop on.
i get my nice pleasant "ACER" boot sceen.
now good ol' GRUB loader pops its way up.
my options are:(kinda paraphrased)

> Ubuntu 8.04 Hardy
Ubuntu 8.04 Hardy (recovery)
-----Other OSes-------
Windows Vista Home Premium
Winodows loader(Longhorn)

When i chose either Hardy, or Hardy recovery... no problem.... beautiful (linux pwns)

But when i go to any of the Vista loaders

my options are:

> Acer eRecovery
Microsoft Windows Vista Home Premium (Recovered)

acer erovery work fine but they forgot to preinstall my recovery partition correctly >:(

when i go to vista i get the lame vista little green loady bar for about a min

then... yay!.... the vista emblem thing glows, makes a "ding-DIINNG!" noise, as it should

but.... bum bum bum!!! i get a cursor, and a black screen for say 40secs.. then...... it reboots.... thats all..... it reboots... back to my happy acer bootscreen. 


so... i went in ubuntu and i opened vmware workstation. i set up a vista vm on the physical drive, and i get: (Typed EXACTLY)
> GRUB Loading stage1.5


GRUB loading, please wait...
Error 17

ok, i have no clue at all what to do, where to start but, w/e, help me please, sorry for the long story, and ill post additional info below..


_My hard drive:_
/dev/sda1 [COLOR="DarkGreen"]FAT32[/COLOR] [COLOR="DarkRed"]-09.67GB[/COLOR]
/dev/sda2 [COLOR="DarkGreen"]NTFS[/COLOR] <VISTA> [COLOR="DarkRed"]-69.65GB[/COLOR]
/dev/sda3 [COLOR="RoyalBlue"]extended:[/COLOR] [COLOR="DarkRed"]-04.99GB (2.8GB/2.1GB)[/COLOR]
     /dev/sda5 [COLOR="DarkGreen"]SWAP[/COLOR]
     /dev/sda6 [COLOR="Silver"][none][/COLOR]
/dev/sda4 [COLOR="DarkGreen"]EXT3[/COLOR] <UBUNTU> [COLOR="DarkRed"]-64.64GB[/COLOR]
[COLOR="Silver"]unallocated[/COLOR]  [COLOR="DarkRed"]-7.44MB[/COLOR]
[COLOR="Silver"]unallocated[/COLOR]  [COLOR="DarkRed"]-3.22MB[/COLOR]

---

