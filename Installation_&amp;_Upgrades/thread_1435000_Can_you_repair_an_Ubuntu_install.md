---
title: "Can you repair an Ubuntu install?"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by bigpayne69 on 2010-03-21
So here is the deal, I had been running Ubuntu 8.10 from the time it was released until about 2 days ago because when I went to 9.04, I got a warning saying that 9.04 didn't support any drivers for my video card. Well I decided to go ahead and upgrade to 9.10 so that I can upgrade to 10.4 LST once it comes out. Everything seemed to be fine but I turned it that night and left it running over night. When I got up the next morning, the screen was black and the computer was not responding. When I tried to restart it and it could not finish loading the OS. It made it about half way though and then the screen just went black. YAH!!! So far the only way I have been able to do anything with it was by having a Ubuntu boot disk in the CD/ROM when I start the computer. With the disk in the drive, whatever file or driver that the OS seems to be missing, it uses the one of the disk and loads just fines. So, no that you know how my day has been let me get to the point, does anyone know if the Ubuntu installer has a repair function and if not, can I just reinstall Ubuntu and let it reload the OS files without it deleting all of my files?

---

### Post by zvacet on 2010-03-21
You can reinstall without losing data if you have separate home partition.If you don´t follow [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.

---

### Post by phillw on 2010-03-21
> **bigpayne69 said:**
> can I just reinstall Ubuntu and let it reload the OS files without it deleting all of my files?

Hi,
Murphys' Law clearly states that upgrades will fail if a backup has not been made.

When you say 'all your files' I am assuming that you mean /home. If you are running a LAMP / Mail Server then a few more things need to be done.

If you can post ```
df -h
```
and from your /home directory the last line of ```
sudo du -h
```

Along with what options you have for taking a backup.

Regards,

Phill.

---

### Post by pastalavista on 2010-03-21
> **zvacet said:**
> You can reinstall without losing data if you have separate home partition.If you don´t follow [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.

Boot the install CD and go through the install process as usual. Use the SAME user name and when you get to the partitioner, check the box marked "Manually select partitions" and click forward. You'll see your old setup. UNCHECK all the 'format' boxes and mount the partitions in the same place they are now. As long as no 'format' boxes are checked, no data will be lost and system files will be overwritten with the originals. You'll need to do security updates again.

---

### Post by dez93_2000 on 2011-10-18
@pastalavista / anyone: any idea what to do with ubuntu 11.10 if the liveCD installer doesn't display my existing ubuntu configuration?
on
/sda
 /sda1 i have ubuntu

on sdb/
 sdb1/ i have my old xp install. neither are shown. What is does show is:

dev/mapper/jmicron_SiRAID
 dev/mapper/jmicron_SiRAID1 (type=ntfs)

In the drop-down selection below, for those entries it says
Linux device-mapper (mirror) for the first and
Microsoft Windows XP Professional for the second.

If i click to install on the linux one, it says "no root system is defined. please select one from the partitioning table". If i click "new partition table" on the top one it asks i i really want to format the whole partition. Given that I want to install over the existing setup, i assume i don't.

Any ideas? I'd be really grateful. 11.10's been a nightmare from the start.

---

