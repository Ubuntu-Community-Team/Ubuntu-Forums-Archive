---
title: "Question: Need to increase storage.  Dual Boot (Window 7 / Linux)"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by rreyes3713 on 2010-07-28
I know there's a similar question thread but mine might be simpler.

I installed Ubuntu (not sure which version 2 month ago) under Window 7. I "allocate" 30 gigs for Ubuntu. Installation went fine.

Now I realize I may need more room for Ubuntu! I think I'll be using anywhere from 60% to 70% Ubuntu over Windows. 

Is there anyway to increase more storage for Ubuntu either an app or through the Terminal? I don't know if this type of installation (thought Window) really creates a partition and if 30 gigs is fixed.

---

### Post by luisito on 2010-07-28
I assume you used Wubi to install "through windows". In order to resize the partition, follow this guide: "https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?"

If you had to change the size of your partitions in a normal linux distribution, you would follow the instructions here
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Marlonsm on 2010-07-28
You can always use the Windows partition to store files for Ubuntu, the way you access it depends on how you installed Ubuntu.
If you used Wubi (that "Inside Windows" option), the Windows partition should be in /host in Ubuntu.
If you partitioned the HD, it should be seen as any other storage device.

---

### Post by rreyes3713 on 2010-07-28
Thanks guys, especially thanks luisito. I think this exactly what I need.

dang this Linux (Ubuntu) is awesome. 

unrelated: I guess all this UNIX stuff I learned as computer major really pay off.

---

### Post by rreyes3713 on 2010-07-28
> **luisito said:**
> I assume you used Wubi to install "through windows". In order to resize the partition, follow this guide: "https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?"

If you had to change the size of your partitions in a normal linux distribution, you would follow the instructions here
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)I'm not so sure LVPM will work since mine is 10.04 version. 

I'll do more research on my options. Suggestions welcome.;)

---

### Post by bcbc on 2010-07-28
> **rreyes3713 said:**
> I'm not so sure LVPM will work since mine is 10.04 version. 

I'll do more research on my options. Suggestions welcome.;)
If you're using wubi more than windows, and you can repartition your drive, I'd suggest migrating your wubi to a new partition. 

I wrote a howto and script to do this for 9.10 or 10.04 versions: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354) 

If you choose to continue using wubi, make sure you have backups. It's all on a single file (\ubuntu\disks\root.disk) and I saw a thread in the last 24 hours for someone who accidentally deleted it and lost everything.

---

### Post by rreyes3713 on 2010-07-30
bcbc, you D'man. Thanks for your post / link. Kind of nervous doing things on the terminal command line.

Yeah, I'm using wubi more than Windows. Now gotta make new partition for Wubi. 

Thanks.

---

### Post by bcbc on 2010-07-30
> **rreyes3713 said:**
> bcbc, you D'man. Thanks for your post / link. Kind of nervous doing things on the terminal command line.

Yeah, I'm using wubi more than Windows. Now gotta make new partition for Wubi. 

Thanks.

With windows 7, make sure you use Windows to shrink the partition. [http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Or at least use a tool that is aware of the windows MFT  - otherwise you could damage win7. [http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by QIII on 2010-07-30
> **rreyes3713 said:**
> dang this Linux (Ubuntu) is awesome.

If you think so, it may be time to actually dual boot.  (Wubi is not, by definition, a dual boot.  Wubi is a "kick the tires" solution for trying Ubuntu out and it is a really good option for doing that.)

Multiple booting is actually done by creating separate partitions for Windows and Ubuntu (or any two or more OSes), so that at startup you can choose between them and run them natively and entirely independent of one another.

---

### Post by rreyes3713 on 2010-07-30
> **QIII said:**
> If you think so, it may be time to actually dual boot.  (Wubi is not, by definition, a dual boot.  Wubi is a "kick the tires" solution for trying Ubuntu out and it is a really good option for doing that.)

Multiple booting is actually done by creating separate partitions for Windows and Ubuntu (or any two or more OSes), so that at startup you can choose between them and run them natively and entirely independent of one another.I thought about this option.

I thought about completely un-install my Wubi Ubuntu, then add a partition then "re-installed" Ubuntu.

But currently Ubuntu is running so well for me I'm kind of scared if I do un-installed Wubu Ubuntu and attempt to reinstall Ubuntu to this new partition I may face problems like listed in this particular forum.

so I'm facing this dilemma.

---

### Post by rreyes3713 on 2010-07-30
> **bcbc said:**
> With windows 7, make sure you use Windows to shrink the partition. [http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Or at least use a tool that is aware of the windows MFT  - otherwise you could damage win7. [http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)Thanks bcbc, should I refrag before shrinking and creating a partition?

---

### Post by bcbc on 2010-07-30
> **rreyes3713 said:**
> Thanks bcbc, should I refrag before shrinking and creating a partition?

I would... when I installed with XP I defragged a couple of times before partitioning.

---

### Post by bcbc on 2010-07-30
> **rreyes3713 said:**
> I thought about this option.

I thought about completely un-install my Wubi Ubuntu, then add a partition then "re-installed" Ubuntu.

But currently Ubuntu is running so well for me I'm kind of scared if I do un-installed Wubu Ubuntu and attempt to reinstall Ubuntu to this new partition I may face problems like listed in this particular forum.

so I'm facing this dilemma.

Once you migrate your wubi to partition, it will be the same as if you installed directly. (You just get to keep your customization and data).

---

