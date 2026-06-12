---
title: "Givving Ubuntu Partition Space To Windows"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by pilsbury847 on 2007-04-01
Just a quick question for you guys this time ; I just got a new hard drive for my computer so I would like to have windows installed on one and Ubuntu on the other.When I do delete the current Ubuntu partition I would like all the space to go to windows.I tried using partition magic but that wouldnt even recognize the linux partition.So how do I give all the space back to windows?

---

### Post by 1/0 on 2007-04-01
Odd, I thought partition magic did that... Isn't it the manual?

Anyway, the Linux way is to use fdisk:

```
sudo fdisk /dev/hda
```

/dev/hda depends on which drive it is and what kind of drive. (Could be /dev/hdb or /dev/sda etc.) Then press "d" for delete and the number of the partition. You mustn't forget the mbr, so:

```
sudo fdisk /mbr
```

This will delete the partitions you choose and everything will be gone, so don't leave anything on the drive you want to keep. If you're uncertain which drive you're deleting, just unplug the IDE-cable to the other drive. That way you can't touch the other drive whatever you do.

After that you should be able to happily (???) install Windows.

---

### Post by ajgreeny on 2007-04-01
Are you already dual booting?  If so you will need to restore your windows mbr after deleting ubuntu, if you need to run windows before you get ubuntu installed again (on the new disk?).  There's plenty of info on how you can do this if needed in these forums.

Normally windows is best on the master disk rather than slave, so if possible arrange your disks that way, get windows running properly on the whole of its disk, and then install ubuntu on the slave disk as normal, using gparted on the live install CD to add the unallocated space on the master disk to windows if you need to do that still.

Good luck.

---

### Post by flooperer on 2007-04-01
Hi, I'm trying to give a disk back to windows too. I tried sudo fdisk /mbr
but I just get
Unable to open /mbr

right now the windows install cd claims I have no HD installed.

---

### Post by 1/0 on 2007-04-01
You could use Microsoft's tools instead. In that case boot into DOS and do:

```
fdisk /mbr
```

Otherwise, you can probably use the repair function in the Windows install CD. Press "R" in the menu and choose "fixboot" and accept. That should format the boot record.

---

### Post by pilsbury847 on 2007-04-04
Awesome thanks guys, its appreciated, and no I'm not going to "happily" install windows I just want my installations on seperate disks.

---

