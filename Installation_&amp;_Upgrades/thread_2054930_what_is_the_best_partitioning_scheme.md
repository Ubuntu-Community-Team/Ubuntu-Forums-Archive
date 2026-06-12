---
title: "what is the best partitioning scheme?"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by Chogan on 2012-09-08
i want to format my laptop hard drive totally (it is 250 Gb) and then  install ubuntu 12.04, openSUSE 12.2 and maybe arch linux, (i do not want to  install windows). what is the best partitioning scheme in such a  situation?

i know that installing multiple linux distros  alongside each other with a shared /home partition lead to creation of  these directories: /home/mandriva, /home/Ubuntu and /home/Arch. and  inside these directories i will have following folders:
Videos, Musics, dcuments, Desktop, etc.

but  i dislike this structure because i do not want to have for example 3  video directory or 3 music directory. i want to have only one video, one  music, and one document, ... directory shared between all distros.

if you were me, how do you partitioning you hard?

---

### Post by jerrrys on 2012-09-08
One partition for video, music, docs.  And no shared home partition.  Works for me :)

---

### Post by vasilbelarus on 2012-09-08
1. Arch / - 20Gb
2. openSUSE / - 20GB
3. Ubuntu / -20Gb
4. /home - =250-20-20-20-swap
5. /swap - double your RAM

1,2,5 - Primary partitions
3,4 - extended

---

### Post by vasilbelarus on 2012-09-08
I have folder data in /home where I put Video Audio Images and other, I added links to my home folder and to my wife`s home folder.

---

### Post by Chogan on 2012-09-08
> **jerrrys said:**
> One partition for video, music, docs.  And no shared home partition.  Works for me :)
how did you do that?

---

### Post by jerrrys on 2012-09-08
> **Chogan said:**
> how did you do that?

start here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=create+data+partition&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=create+data+partition&as_qdr=all&sa=Google+Search&lang=en)

make sense?

---

### Post by oldfred on 2012-09-08
I create a data partition with each folder at top level. Then mount that dat partition and link each of those folders into my /home. But with different distributions you may have to pay attention to UID/GID. Most let you set the GID. Ubuntu/Debian uses 1000, Fedora used to use 500 and recently changed to 1000. Do not know about other distributions.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by Chogan on 2012-12-26
i did so much search in the web and found that partitioning is hard and best thing for me is to use default partitioning.

---

### Post by orb9220 on 2012-12-26
Easiest for me is having a usb external ntfs drive. All music,images,movies,documents accessible by linux. 

And if need arises for pulling the drive and mount on another system that is windows then the data is still accessible. And easier to clone to another drive or copy to another OS.
.

---

