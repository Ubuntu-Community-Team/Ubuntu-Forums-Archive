---
title: "[SOLVED] HELP with 8.04 install ASAP!"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by CSEatOSU on 2008-05-29
I installed 8.04 via Wubi in XP. Went great for the first couple weeks with the 30Gb install until I ran out of disk space.  I would have rather done a 60Gb install, but the drop-down in Wubi only allowed for max of 30Gb. So I did some searching and found how to increase the disk space to allow Ubuntu to use another 30Gb. I used the instructions [here]("https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b") by running the script
```
sudo sh wubi-add-virtual-disk /home 30000
```
So basically when I ran the script above, I thought it would just increase root.disk from 27Gb to ~60Gb but instead it moved /home to a new virtual-disk, home.disk and added 30Gb to the / (root.disk).

So...

**What I have now**
/host/ubuntu/disks/root.disk 27GB 22Gb free
/host/ubuntu/disks/home.disk 27.9GB 4Gb free (not good)

**What I want**
/host/ubuntu/disks/root.disk **~60Gb**

So my real question goes like this, how do I get from where I am to where I want to be?

Thanks,
Matthew

---

### Post by iaculallad on 2008-05-29
Had you considered transferring your Virtual wubi installation to a dedicated partition, instead of increasing the size.

Try looking at this page: [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

### Post by CSEatOSU on 2008-05-29
> **iaculallad said:**
> Had you considered transferring your Virtual wubi installation to a dedicated partition, instead of increasing the size.

Try looking at this page: [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

Would I still be able to do that even after Ubuntu now thinks I have 2 "partitions" for it?

---

### Post by CSEatOSU on 2008-05-29
> **iaculallad said:**
> Had you considered transferring your Virtual wubi installation to a dedicated partition, instead of increasing the size.

Try looking at this page: [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

I would consider moving to a dedicated partition but there is only one partition C: on my machine.

---

### Post by iaculallad on 2008-05-29
> **CSEatOSU said:**
> Would I still be able to do that even after Ubuntu now thinks I have 2 "partitions" for it?

Give it a try :) (Honestly, I only experienced transferring 1 virtual drive of wubi to a fix partition and not that "broken" partition) Only this time, you'll only transfer the root.disk partition  and observe if there will be a /home partition. If not, you could create you're new /home directory (**sudo usermod username --home=/home/username** command) and backup your /home directory from the virtual disk.

Do post us for any update if you plan on doing it :)

---

### Post by CSEatOSU on 2008-05-29
> **iaculallad said:**
> Give it a try :) (Honestly, I only experienced transferring 1 virtual drive of wubi to a fix partition and not that "broken" partition) Only this time, you'll only transfer the root.disk partition  and observe if there will be a /home partition. If not, you could create you're new /home directory (**sudo usermod username --home=/home/username** command) and backup your /home directory from the virtual disk.

Do post us for any update if you plan on doing it :)

I can't really do the "give it a try" method.  This is my work computer so I can't really just hack around at it.  I need a definite solution.

I don't use windows on this machine at all, could I just insert the installation CD and install a clean version of Ubuntu, wiping Windows completely?  Would it recognize my current install and keep all the settings and apps I've installed.  Like Oracle, vmware, ssh, vpn... and more inside Ubuntu, I don't want to have to reinstall all those again.

---

### Post by iaculallad on 2008-05-29
> **CSEatOSU said:**
> I can't really do the "give it a try" method.  This is my work computer so I can't really just hack around at it.  I need a definite solution.

I don't use windows on this machine at all, could I just insert the installation CD and install a clean version of Ubuntu, wiping Windows completely?  Would it recognize my current install and keep all the settings and apps I've installed.  Like Oracle, vmware, ssh, vpn... and more inside Ubuntu, I don't want to have to reinstall all those again.


You could still wait for more answers to your query but don't try to wipe windoze because it handles/load your wubi virtual drive.
I really don't have a definite solution because I only tried transferring a single wubi virtual drive to a fix partition.

---

### Post by CSEatOSU on 2008-05-29
> **iaculallad said:**
> You could still wait for more answers to your query but don't try to wipe windoze because it handles/load your wubi virtual drive.
I really don't have a definite solution because I only tried transferring a single wubi virtual drive to a fix partition.

I checked out the LVPM site and they have a "resize virtual disks".  When I checked out the LVPM site about a week ago, it hadn't been created for 8.04... I wish I would have waited a week.  I'm sure this will work.  I'll keep you posted.

---

### Post by CSEatOSU on 2008-05-29
Well LVPM didn't work at all.  See my posts here

[post #230, 232, 234, 235]("http://ubuntuforums.org/showthread.php?t=438591&page=23#230")

Please someone help me!

---

