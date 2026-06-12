---
title: "Your Advice - triple boot"
date: 2014-02-14
forum: Installation &amp; Upgrades
---

### Post by rexineffect on 2014-02-14
sda1 - 100mb windows 7
sda2 - 350gb windows 7
sda3 - 20gb linux /
sda4 - 2gb linux swap
sda5 - 98gb linux /home
sda6 - 20gb linux /
sda7 - 2gb linux swap
sda8 - 98gb linux /home
sda9 - 5gb storage fat32

so far have installed windows 7, sda1, 2
currently installing arch linux, sda3, 4, 5

im mostly wondering how should i configure these boot loaders? what should i do with the arch boot loader? what should i do with the ubuntu boot loader to come on sda6, 7, 8

if no one helps in time im going to install arch boot loader to.... i actually dont know yet

any ideas or experiences would be appreciated, thanks
ill check in as it goes and eventually write a tutorial for this that will be specific and hopefully help some ppl.

---

### Post by TheFu on 2014-02-14
Share the swap between all the Linux systems.
1 boot loader is needed, not 1-per-OS.

I would share HOME between all the Linux systems too, just use a different login between them so the DEs don't get confused.

FAT32 is almost worthless. Too many stupid limitations.  Use NTFS if you want to share files between OSes.

---

### Post by oldfred on 2014-02-14
+1 on TheFu's suggestions.

I go one further and leave /home inside / and  keep root at 20 or 25GB. The have one or two shared data partitions for all data. I still my two data partitions from when I still had XP. I had a NTFS data for anything I might need with XP like my Firefox & Thunderbird profiles. And a Linux formatted data partition for all new data now that I do not use XP.
The only issue that I do not know with Arch is what is default GID?

 Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by rexineffect on 2014-02-14
OK that all makes sense..

So I would want to share swap, easy enough. Now there is something about hibernation with that. Ill look into it.

So you say to share /home that is interesting and seemingly useful idea, I would like to try.

Can you help me a lil more with it please?

So you say different username for each distro of Linux? what abount root, that will always be the same? Can you kinda just lay it out for me real simple and I can look into stuff more if I still don't get it plz?
And can u give me an example drive partition format, windows like mine then 2 distro of linux sharing swap and using the same /home but different / for each distro. Thanks! or did u say a different / for each distro?


EDIT: also now i have grub installed and arch so I will not add another bootloader. ill wait and config my partitions tell i understand this sharing a lil better

---

