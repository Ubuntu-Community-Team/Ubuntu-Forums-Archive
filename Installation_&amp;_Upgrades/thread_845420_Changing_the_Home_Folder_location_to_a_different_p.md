---
title: "Changing the Home Folder location to a different partition"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by xtrumanx on 2008-06-30
Hi everybody (/Dr. Nick)

Just installed Ubuntu and didn't make a seperate partition for the Home Folder while I was at it. I decided to get rid of my Windows and thought if it would be possible to use that partition as my Home folder. Problem, I don't know how to do so. 

I found [this thread]("http://ubuntuforums.org/showthread.php?t=48536") which was supposed to accomplish exactly what I needed but it pretty much made me unable to login back to Ubuntu because the system couldn't find the Home directory. Luckily, I backed up the fstab before editting it so was able to restore it using the Live CD.

Anyone know how to make this work when using 8.04? Btw, my fstab doesn't have an entry for the Home directory currently. Thanks in advance.

---

### Post by vanadium on 2008-06-30
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

is the classical howto for moving your /home to a separate partition.

---

### Post by eryksun on 2008-06-30
> **vanadium said:**
> [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

is the classical howto for moving your /home to a separate partition.

If you make your current NTFS partition into /home, you may end up wasting a lot of space with a big / partition that you never use. You may wish to follow the above how-to closely, rather than adapt it, resizing your root partition to around 5-20 gigs (depending on your HD size and how many packages you plan to install) and creating a big new partition for /home, where most of your files will be. Then use GParted to reformat your Windows NTFS partition as ext3 and mount that for whatever (e.g. /media/movies, /media/music).

---

### Post by vanadium on 2008-06-30
+1

---

