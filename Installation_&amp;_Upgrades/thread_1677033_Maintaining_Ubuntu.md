---
title: "Maintaining Ubuntu"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by rshinde70 on 2011-01-28
Hello Friends,

I'm using Ubuntu 10.04LTS from last 2 months. My use is so rough. I use it for programming, Internet, Multimedia, etc.
Day by day, I realized that it's getting slower and slower.

Like in windows, I can make them like a clean install by De-fragmentation, C drive cleaning tools, etc. But as I new to Linux family,  I don't know how to maintain this OS.

So, is there any packages or ant tricks by that I can keep my desktop at high performance and clean?

                                                 :roll: :roll: :roll: :roll: :roll: :roll: :roll: :roll:

---

### Post by Frogs Hair on 2011-01-28
Two cleaning tools you may want look at  are BleachBit in the software center  and Ubuntu Tweak , the second doing much more than cleaning .  [http://ubuntu-tweak.com](http://ubuntu-tweak.com)

Unlike Windows the hard drive is used and accessed differently with Ubuntu and many users say defrag is unneeded , but there are many pages on the web about that subject and you can make up your own mind.

---

### Post by Rubi1200 on 2011-01-28
Personally, I think tools like Ubuntu Tweak and Bleachbit are unnecessary.

Learn to use the built-in tools in Ubuntu to "houseclean."

For example,

```
apt-get clean
``` [clears out the local repository of retrieved package files]

```
apt-get autoclean
``` [Like clean, autoclean clears out the local repository of retrieved package files. The difference is that it only removes package files that can no longer be downloaded, and are largely useless]

For more, see here:
[http://ubuntuforums.org/showpost.php?p=800462&postcount=1](http://ubuntuforums.org/showpost.php?p=800462&postcount=1)

---

### Post by vanadium on 2011-01-28
> **rshinde70 said:**
> 
Day by day, I realized that it's getting slower and slower.

Are you sure about that, or is this just an impression?

The only reason indeed why a linux system could become sluggish is fragmentation, indeed. Fragmentation may become problematic on partitions that are quite full. On partitions that have sufficient free space, fragmentation is practically not a problem.

Unfortunately, the only way to defragment a linux volume is to reformat it. Try to have sufficient free space on your partitions to avoid fragmentation.

---

### Post by uRock on 2011-01-28
> **vanadium said:**
> Unfortunately, the only way to defragment a linux volume is to reformat it. Try to have sufficient free space on your partitions to avoid fragmentation.
There are defragmenting applications out there for EXT4, but they are nowhere near as easy to use as the ones found in Windows. [http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/](http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/) [http://www.linuxtoday.com/infrastructure/2008060300626OSHWHL](http://www.linuxtoday.com/infrastructure/2008060300626OSHWHL)

---

### Post by rshinde70 on 2011-01-29
Thank You Friends for all your great Comments and help.
@[vanadium]("http://ubuntuforums.org/member.php?u=268902") Actually, I used OpenSUSE 11.3 on another partition, I used and It was really Greatest performance I ever seen.
It was working like a SuperFast Computer. As compared to that, Ubuntu is only 70% in performance.. So, I thought, may be it's cuz of Zero maintenance.. So, I made this thread.

---

