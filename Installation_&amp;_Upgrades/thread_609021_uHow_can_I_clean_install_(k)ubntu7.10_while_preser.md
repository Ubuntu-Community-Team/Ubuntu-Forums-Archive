---
title: "uHow can I clean install (k)ubntu7.10 while preserving windows?"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by edisav on 2007-11-10
I've been planning to clean install the newest (k)ubuntu version but I'm concerned about preserving my current windows install. 

Currently, the booting and OS selection is done thru grub, but what will happen to it when I install the newest OS? 

Any help/info would be appreciated. I guess I could go thru the window reinstall, but I'd rather not.

Thanks

---

### Post by Seisen on 2007-11-10
When you reinstall Kubuntu just use the partition's you have set now  or you can actually delete them and when it asks you where to install it at you just select the largest continuous free space. Also  make sure that Grub is reinstalled when you install Kubuntu and you should be fine.

---

### Post by Pumalite on 2007-11-10
Install on top of the other one (point to the right partition) and you'll have a new Grub with the same options you had before.

---

### Post by Herman on 2007-11-10
The other posters are correct.

Many Windows users seem to be concerned about the (imagined) possibility of Linux and particularly GRUB writing to their Windows file system when Ubuntu is installed.
In fact, GRUB is installed in the MBR of the first hard disk, and not in the Windows boot sector or anywhere in the Windows partition at all.
Many people think that since Windows is their first partition, then it must be at the start of the hard disk. 
The truth is, the MBR is in the first sector of the hard disk, and the MBR and the entire first track of the hard disk (63 sectors) are empty and not formatted with any file system, so they are not part of your Windows installation.
Your Windows file system (partition) doesn't start until sector number 63, where the Windows boot sector is.

If you want to check up on that and see for yourself, try this command,
```
sudo fdisk -lu
```As you will see now, Windows (or whatever your first partition is), does not begin until sector number 63.

The Windows boot sector is in the first sector of the Windows partition and that's what GRUB chainloads to hand over control to Windows boot loader to boot Windows for you.
GRUB is not written to the Windows boot sector and should never be.

A lot of the time the cause of people's worries is that many others, even some web site developers, write about the hard disk's MBR and the boot sector of a partition as if the two terms have the same meaning. Probably it's because they don't know any better themselves, so the misinformation and confusion spreads.

There are always posters here in Ubuntu Web Forums and in other forums too, claiming that this or that calamity has happened to their Windows after a Linux install. Usually if they find the right help and are willing and able to co-operate, their problems are easily solved. Nine times out of ten their problem isn't as bad as what they claim in the title of the post. That's often designed just to get attention.

A partition table problem or a file system problem caused by trouble with a hard disk partition editing program is still a remote possibility. For those reasons you should always back up your data before you re-install or use a hard disk partition editing program. It might not be the programs fault either, I have had a problem like that caused by a few specks of dust on an optical drive lens. Nowadays we have good programs that can help you with those problems if they do happen, but it is best to make a good backup anyway.

As long as you are sensible and take the right precautions, even if the worst does happen, the most you can lose is a little bit of your time.

The most common problem would be a booting problem, and even though that is unlikely too, you can always take the precaution these days of downloading and burning a copy of [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and that will help you to boot again if you do experience any booting problems. Then you can come here and get help to fix the problem.

Regards, Herman  :)

---

