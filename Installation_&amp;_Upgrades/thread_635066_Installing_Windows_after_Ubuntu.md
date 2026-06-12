---
title: "Installing Windows after Ubuntu"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by gewitty on 2007-12-08
Has anyone ever had any success installing XP _after_ Ubuntu? I tried to load it onto a second slave drive on my machine the other day and although I abandoned the attempt when Windows told me it needed to make the Ubuntu drive inactive, it still screwed up GRUB, which had to be repaired before I could get Ubuntu started again.

I've seen some posts from people who tried to install on a new partition, but not on a separate drive.

I'm sure there is a safe way to do it, but need a few pointers before attempting it again.

---

### Post by Joeb454 on 2007-12-08
AFAIK the only way to do it is to install Windows and then reinstall grub afterwards

---

### Post by teryowen on 2007-12-08
Yes just go about the install. Once its done you will only be able to boot into windows to allow you to boot into Ubuntu and Windows you need to reinstall grub do this from the live CD, and you will need to add a few lines to the menu.lst file to have the XP choice in there.

---

### Post by gewitty on 2007-12-08
Thanks for the replies. But why does Windows need to make the Ubuntu drive inactive and what effect does this have? It also requires that I make a new FAT32 partition on the primary drive.

---

### Post by teryowen on 2007-12-08
Basically GRUB comes in two parts one on the MBR and the other on the Ubuntu partition. So when windows gets installed it reinstalls MBR to suit it self, thus wiping out the GRUB part on the MBR, so thats why you have to reinstall it. And why probably because its microsoft and why would they give a rats a**....

As for the FAT32 partition havnt heard of that.

---

### Post by gewitty on 2007-12-08
Thanks for advice and the explanation. One day when I'm feeling brave, I'll give it a go. But I think I'll make a full ISO backup first. It's taken me a long time to get everything the way I want it in Ubuntu and I really don't want to have to start all over again.

---

### Post by Sciamano on 2007-12-08
Hi everybody.

I am trying to install XP on my Pc with Kubuntu Gutsy, too.

Here is the problem I'm encountering. I have partitioned my HD this way:
- Partition1: EXT3 (on which I've installed Kubuntu's root)
- Partition2: EXT3 (on which I mount my /home)
- Partition3: empty (I left this empty knowing I would need Windows later)

Now, when windows installer asks me where to install, I select Partition3, but an error message comes up saying that Windows needs to install system files on the hard disk, but it contains no Windows compatible partitions.
I've already tried deleting partition3 and re-creating it in the installation process, but still Windows complains that the partition is not good.

Any ideas?

Thanks
Luca

---

### Post by gewitty on 2007-12-08
What file system have you got partition 3 formatted to? It needs to be Windows compatible.

---

### Post by Sciamano on 2007-12-08
It's an empty space. I create the partition during the setup process, so it can format it any way it wants, but it refuses to.

---

### Post by Sciamano on 2007-12-10
anyone? :(

---

### Post by gewitty on 2007-12-10
As I said, I believe that you need to format the partition for Windows, *before* you try to install. You should be able to do this with GParted I think.

---

### Post by Sciamano on 2007-12-10
I've already tried that.
The Windows setup program "sees" the partition as an NTFS partition, but still refuses to install xp, and outputs that same error :(

---

### Post by gewitty on 2007-12-10
Sorry. If that's the case, I just ran out of ideas. You need a guru :icon_frown:

---

### Post by Sciamano on 2007-12-10
:( Thanks anyway.
Let's see if a guru picks this up :)

---

### Post by BryanFRitt on 2007-12-10
If you have a second harddrive, you can take out the harddrive you have / want ubuntu on, and leave in the drive you want to install Windows into.  Install Windows on that drive then add the other hard drive back after install.  Then use the bios to switch which drive gets booted into.  Windows might have to be on the primary master drive for this, but I don't know.  Also you might want to mess with each drives boot menu so it includes the other drive, so you don't have to mess with bios no matter which drive the bios is set to boot to, and for added security if something were to go wrong.

---

### Post by Sciamano on 2007-12-10
Thanks BryanFRitt for the suggestion, but unfortunately I don't have any other drive.
Well, I have it, but it's full :)

If I can't find any other solution, I might have to "clone" the partition that currently hosts my root, and move it to the third partition of the drive, and then try to install windows on the first partition. Who knows if this would work, though?

---

