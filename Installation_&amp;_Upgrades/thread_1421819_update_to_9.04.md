---
title: "update to 9.04"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by fuzzybush on 2010-03-04
Hello , I have had Ubuntu on my computer for about a year. I keep being cued to update to 9.04 .  If I update to 9.04 what will I lose ? I am only interested in keeping some photos and spreadsheets . Do I have to copy them someplace else ?

---

### Post by lykwydchykyn on 2010-03-04
In theory, you lose nothing.  The upgrade happens in-place and after a few hours of downloading and updating, you reboot and have an upgraded system with all the same software and data you had before.

In practice, it CAN go awry, so if you want to upgrade make sure your data is backed up and you've got a CD ready in case you need to reinstall.  It also doesn't hurt to have another machine handy so you can consult the forums in case of problems.

---

### Post by adam22 on 2010-03-04
I would not "upgrade." Instead, I would drag all your documents onto an external drive (flash or hard), and then download the new version and burn it to a disc. Delete the old partition and install the new one.

If you did not know:
You can make 3 seperate primary partitions. /home, /, and swap. If you do this, you only delete the / partition and the documents and themes, etc. will stay in tact in the /home partition.

---

### Post by thomas144 on 2010-03-04
Ubuntu is not the most recent version. Ubuntu 9.10 is, and 10.04 will come out soon. I'm not sure if going to Ubuntu 9.10 or 10.04 would need a complete reinstallation. If you could seamlessly upgrade, I would wait for Ubuntu 10.04 to come out. I would back up my files and upgrade. If not, you might not want to completely reinstall.

---

### Post by lykwydchykyn on 2010-03-04
> **adam22 said:**
> I would not "upgrade." Instead, I would drag all your documents onto an external drive (flash or hard), and then download the new version and burn it to a disc. Delete the old partition and install the new one.



The way I see it, an upgrade will either succeed or fail.  If it fails, then reinstall.  If it succeeds, you've saved yourself a whole lot of hassle.

If you're prepared to reinstall anyway, you have nothing to lose but a little time and effort upgrading.

---

### Post by adam22 on 2010-03-04
It takes me 10 minutes to download the .iso and 15 to install, and since I keep a seperate /home partition, it's just as fast and it's a sure thing, that's why I prefer it. Also, somethings can not be upgraded (like going from ext3 to ext4).

---

### Post by mörgæs on 2010-03-04
9.04 is one of the most bug-free releases available, so I agree on that advice. If you (like me) are on 8.10, you should upgrade within a few months.

9.04 is supported though most of 2010. If everything works on your machine, I would stay with 9.04 untill the support runs out and then jump to 10.04, skipping 9.10.

I always prefer a clean installation to an upgrade done through the old system.

---

### Post by mörgæs on 2010-03-04
> **adam22 said:**
> 
You can make 3 seperate primary partitions. /home, /, and swap. If you do this, you only delete the / partition and the documents and themes, etc. will stay in tact in the /home partition.

This can be good or bad. /home contains a lot of hidden configuration files, and if one has really messed things up, it is best to wipe every trace of the old applications including the configurations. 

If you have a separate /home, remember to go through the hidden files by hand before installing the new system.

---

