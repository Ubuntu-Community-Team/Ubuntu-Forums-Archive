---
title: "move Ubuntu on other partition, installing Win98"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by barbex on 2008-01-16
I rebuilt a 800MHz computer for my son to play simple games on, Xubuntu is installed and works perfectly. Unfortunatly, I have had no luck in getting his Edu-games to run under Wine, it's been a major hassle. These games have all just minimum requirements so I thought I would just install Win98 on another partition and be done with it.

As far as I remember, Win98 wants to be installed on the first partition. Ubuntu sits on that one.

Is there a way to move Ubuntu to the second parttion and have it run from there, install Windows on the first partition and restore Grub after that?

I have searched, I have looked but I have not found an answer to this question.

---

### Post by bernied on 2008-01-16
The simplest way:
- take a copy of all the data files you want to keep
- partition the disk using a [gparted live-cd](http://gparted-livecd.tuxfamily.org/), creating a partition for windows, and leaving the rest unused
- install windows into the partition you created
- install ubuntu into the empty space, allowing it to decide how to partition
- check that ubuntu has installed grub so that you can boot either ubuntu or windows
- restore your data onto the new ubuntu

A (relatively) simple way:
- use a [gparted live-cd](http://gparted-livecd.tuxfamily.org/) to shrink down your ubuntu partition.
- create a new install of ubuntu in the spare space you just created.
- transfer what you want from the old install to the new
- install windows over the top of the old ubuntu
- re-install grub

A more complicated way, if you didn't want to reinstall ubuntu. I (and others, I am sure) would help with details if this is what you want to do. It depends on you having enough space to have two installs of ubuntu on the disk at once:
- use a [gparted live-cd](http://gparted-livecd.tuxfamily.org/) to shrink down your ubuntu partition, so there is room for another of the same size. Make the new partition, exactly the same size as the first one, for ubuntu's eventual home. The first partition will eventually belong to windows. You will need to take account of any swap partitions when you do this, these will still be needed by ubuntu.
- still in the live-cd environment, use the [dd command](http://linux.die.net/man/1/dd) to copy the partition, byte for byte. You will need to do some reading to make sure you do this properly. dd can make an exact copy, which will take care of the filesystem creation, timestamps, permissions, links etc. Aternatively, you could create a new filesystem using [mkfs.ext2](http://linux.die.net/man/8/mkfs.ext2) and then use the [cp command](http://linux.die.net/man/1/cp) to copy the files, but again you'd need to make sure you got your options right. Whichever command you use, this duplication will take a long time, like hours, or overnight, depending on how large your partitions are, and how fast your disk reading/writing is.
- still in the live-cd environment, mount the new partition and reconfigure the new ubuntu for operation in its new home. You will have to change the files /boot/grub/menu.lst and /etc/fstab so that they point to the new partition instead of the old. 
- at this point it would be a good idea to try to boot to the new partition, before you make any changes that will make your first one unbootable. You can do this by manually editing the entry when grub starts. (Hit the 'E' key to edit, and change anything that refers to a specific partition, like '(hd0,0)' might change to '(hd0,1)' if you've copied ubuntu into the second partition, and 'hda1' would change to 'hda2'.
- if this works, use [grub-install](http://linux.die.net/man/8/grub-install) to make the machine boot to the new ubuntu. Again, check that this works before you commit yourself and overwrite your original ubuntu.
- install windows over the original ubuntu
- run grub-install again, you might have to manually add windows to the grub menu

I hope this helps.

---

### Post by barbex on 2008-01-16
Hmm, I see.
None of these look particularly tempting I must say. I had hoped for something like "Copy Ubuntu and then use the rescue option on the CD" but that was just wishful thinking.

I think I will leave my /home partition untouched, install Windows on the first partition and install Ubuntu on the second partition, reusing /home. That's something I have done before without problems. Now where have put that CD?

I just wish I had a way to find out what exactly I installed until now. Is there a way to save a list of installed applications trough synaptic?

---

### Post by Mze on 2008-01-16
I've used this [script]("http://ubuntuforums.org/showthread.php?t=613462") with repeated success. Copy tar file to pen drive, burn to DVD, external hard drive. 

Check the thread out. 

Hope it helps.

---

### Post by Zill on 2008-01-16
barbex:  > Is there a way to save a list of installed applications?
```
dpkg --get-selections | grep -v deinstall > packages
```

---

### Post by barbex on 2008-01-16
Oops, too late. But good to know.

I used the [system rescue cd]("http://sysresccd.org/Main_Page") to format the first partition with FAT32. Just installed Win98 -- good $deity how horrible! And it bluescreened! The irony!

Thanks for the help, everyone.

---

### Post by barbex on 2008-01-18
Wasn't Ubuntu supposed to detect Win98? It didn't. How strange.

---

