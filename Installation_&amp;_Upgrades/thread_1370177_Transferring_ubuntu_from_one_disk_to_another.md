---
title: "Transferring ubuntu from one disk to another"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by gilch on 2010-01-02
I guess I'll be asking the impossible... Is it possible to EASILY move my Ubuntu set up from one disk (smallish) to a bigger one, so that I can install Win7 as well on that bigger disk drive?
I am not too keen on reinstalling ubuntu because then I will lose all those other ubuntu programs that I have installed.

Gilles
Thanks in advance

---

### Post by MelDJ on 2010-01-02
try remastersys [http://geekconnection.org/remastersys/remastersystool.html](http://geekconnection.org/remastersys/remastersystool.html)

---

### Post by prshah on 2010-01-02
> **gilch said:**
> Is it possible to EASILY move my Ubuntu set up from one disk (smallish) to a bigger one

Yes, and it's quite easy. You have multiple options.

The one I recommend is using "dd". This is very risky if you are not careful. Please see this thread for more details:[[SOLVED] Exact duplicate of entire HDD]("http://ubuntuforums.org/showthread.php?t=874643")

Using "dd" you can "rip" your entire existing HDD to the new HDD directly, without need of a third, intermediate storage medium.

Your new HDD can be completely blank. The existing partitions will be copied/created, and then you can resize your partitions on the new HDD if you want. GRUB will also be copied over using this method.

An alternative, less risky, but slow method is to use "partimage" which is a partition imager. You can make an image of your existing partitions, for which you will require an intermediate storage device such as a USB drive, or network share, etc. The partition image can then be restored to the new drive, but you will first have to manually create the partition on the new drive. The new partitions can be any size greater than or equal to the original partition. You will also have to manually install GRUB (but that's something you will have to do in any case after you install Win 7).

The last I read, remastersys does not work with 9.10. However, I may have either misread it, or a newer version may work. Just FYI.

Please post back if you want further details on either option.

---

### Post by gilch on 2010-01-02
Thank you. I think I can do that. 
But before I can do that I have another problem to solve which I will post in the General Help.
Gilles

---

