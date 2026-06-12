---
title: "Windows 7 will not load from Grub after installing Ubuntu"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by michnic on 2010-02-10
My Asus Eee PC 1001P came with Windows 7, and I successfully installed Ubuntu on to the computer (i.e. after Windows 7 was already installed). After installing Ubuntu, though, Windows 7 will not load from the Grub start up menu (it directs me to reinstall Windows from a CD - which I do not have and the Asus Eee PC does not have a CD drive). How do I go about being able to run both Windows 7 and Ubuntu from the Grub start up menu?

---

### Post by murderslastcrow on 2010-02-10
This is under the assumption that 1. You selected to automatically partition Windows 7 and Ubuntu side by side during installation (or did it manually beforehand if you happen to know a lot about partitioning), and 2. Both Ubuntu and Windows 7 are listed in GRUB.

If there are no recovery options when you begin to start up Windows, you may have to try defragmenting your Windows partition and perform some disk checks (this might help, but if selecting Windows 7 doesn't provide you with any recovery options in the first place, it's hard to tell).

One of my friends had a similar situation with manually partitioning Vista. It is a good idea with the newer Windows versions to clear space for Windows and install it after Ubuntu, then use the Ubuntu CD to restore GRUB (this will add Ubuntu back to the boot menu).

Of course, this isn't the most pleasant option, so you'll want to research a bit more about anything you can try from the screen you get to after choosing Windows 7.

I can provide some instructions if you've verified you can't get Windows to start up without reinstalling it.

---

### Post by theozzlives on 2010-02-10
Windows 7 consists of two partitions (system, and Drive C). If you didn't use the Windows Disk Management to resize the partition, you may have damaged the system partition.

Also, most computers that don't come with a CD/DVD have a recovery partitions. I can't speak for NetBooks, however.

---

### Post by murderslastcrow on 2010-02-10
Yes, netbooks usually do- even if they have Ubuntu preinstalled (system recovery partitions). It's always best to do some defragmenting and disk checking before ever starting up your Ubuntu CD (or USB in this case), and you can go to System/Administration/GParted to check up on how your partitions are all set up.

Again, installing Windows 7 afterward and restoring GRUB is a good idea, since NTFS filesystems aren't very trustworthy or flexible in the first place.

Also, you'll want to use Microsoft's DVD USB tool most likely, if you want to load the install files from a USB. Not sure if you need something more than Wine to run that, however. If you can snag a USB-powered CD/DVD reader and ask the manufacturer to send you an installation disc (or some other media, even), they may be able to assist you.

Also, for recovering Windows 7, since it seems like there aren't any particular issues with Ubuntu, you may want to get some further expertise from a Windows 7 based forum.

We're all more used to Ubuntu, as much as we like to help with these issues. I personally have limited resources when it comes to testing Windows releases, although I've set up a few dual-boots with Windows 7 successfully.

---

### Post by Mark Phelps on 2010-02-10
If you allowed the Ubuntu installer to shrink your Win7 partition, and it doesn't boot now, you almost certainly corrupted your OS partition.

If your first Win7 partition is intact, you can try booting your machine into Win7 and pressing F8 repeatedly until you get a menu screen that has a selection of Repair your computer.  Select that and run it several times.

If you're lucky and did not damage your boot partition, since it contains a copy of the Windows recovery environment and the Win7 boot loader files, there's a very good chance that Win7 booting will be restored.

After that, come back to the forums and ask about reinstalling GRUB2 -- to get access back to Ubuntu.

---

