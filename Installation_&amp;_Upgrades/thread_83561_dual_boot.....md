---
title: "dual boot...."
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by Laz0r on 2005-10-29
I have 3 hard drives, 2 are sata and raided, the other is IDE.
I want to partition the raid, so i can boot between xp pro and ubuntu, and I would like to use the IDE drive as storage that I can access through both operating systems.
Am I right that I have to:
1. format the raid ntfs and the ide fat32
2. create the partitions on the raid
3. install xp
4. install ubuntu
5. grub should recognize xp

Can you tell me what order to do these things, and correct anything I've said wrong.

Thank you for your help...

---

### Post by audax321 on 2005-10-29
Sounds fine to me but make sure you leave space on the RAID for the linux partitions. I recommend a 5GB root partition (mounted to /) and use the rest of the space for a home partition (mounted to /home). Or you can just go for one root partition that takes up the whole space. The nice thing about a seperate /home partition is that you can reinstall linux by just formatting the root partition and not have to backup any user files since the /home partition will be left untouched. And step 2 should be taken care of in the Windows and Ubuntu installers (though I haven't installed Linux on RAID before).

---

### Post by Laz0r on 2005-10-29
Can you tell me how to install to a seperate /home and boot partition?

Thanks.

---

### Post by audax321 on 2005-10-30
During the Ubuntu installation it will come up with a suggestion for your partitions. This is by defualt one large partition using your freespace mounted to / (which is the root partition). There should be an option there to specify your own partitions.

All you have to do is create a 5 GB partition in the freespace and then choose the mount point as /

Next, tell it you want to create another partition using the rest of the available space and mount it as /home

Ubuntu will automatically install all of its system files to / and keep /home empty. After you specify your username in the installer it will create a user folder in there for you. So your path to user files will be /home/<username>

That way if you ever want to reinstall Ubuntu you can simply install over / and keep your /home intact and your settings/files will transfer over as well.

If you want to see some screenshots I found this website in another post here (it doesn't quite relate to this issue, but it might help make what I am saying clearer): [http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

---

