---
title: "Safest way of installing two copies of Ubuntu?"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by MarjaE on 2011-10-16
I am thinking of installing Xubuntu soon. I have a used Windows machine, and I'm not very familiar with Windows but I left it there for certain games, and I'm not very comfortable with repartitioning within Windows, so I use Ubuntu 11.04 within Wubi. But Wubi doesn't like double installs.

I think a Xubuntu 11.10 install would be best, but a secondary Ubuntu 10.10 install would also be nice.

---

### Post by Hakunka-Matata on 2011-10-16
I like the way you think, and installing two or many instances of Ubuntu is a good idea.  How much free space is available on your hard drive.  The *proper* way to achieve your goal is through partition installs, rather than via Wubi in windows.  Post the output of these commands please.
```
sudo fdisk -l && sudo sfdisk -luM
```

---

### Post by MarjaE on 2011-10-16
I currently have my backup disk attached...

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbd18a23c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1249    10025984   27  Unknown
/dev/sda2   *        1249        1262      102400    7  HPFS/NTFS
/dev/sda3            1262       60802   478256128    7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcbce2081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sda1         1   9791   9791   10025984   27  Unknown
/dev/sda2   *  9792   9891    100     102400    7  HPFS/NTFS
/dev/sda3      9892  476938  467047  478256128    7  HPFS/NTFS
/dev/sda4         0      -      0          0    0  Empty

Disk /dev/sdd: 121601 cylinders, 255 heads, 63 sectors/track
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sdd1         0+ 953867- 953868- 976760001    7  HPFS/NTFS
/dev/sdd2         0      -      0          0    0  Empty
/dev/sdd3         0      -      0          0    0  Empty
/dev/sdd4         0      -      0          0    0  Empty

Also, I keep most of my files/documents on the Windows file system, so I can, if needed, access them from either operating system, and I would like to be able to access them from both Xubuntu and Ubuntu.

---

### Post by Hakunka-Matata on 2011-10-16
Your /dev/sda drive has no unallocated space on it.Three of the four partitions (primary) availabe to a MBR disk are in use.
To install Ubuntu to a partition you would need to shrink/resize /dev/sda3 to make room for another partition, which would be an Extended partition.  Within that Extended partition /dev/sda4, you would then create all the other partitions(Logical) for the Ubuntu system(s).  It's really quite easy and quickly done, once you're ready to do it.

[This link]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions") is nothing more than a bookmarker in the **Partitioning link** in my signature.  It sounds like you're all backed up already?  I'm guessing your windows installation is a Windows XP installation, correct?

---

### Post by MarjaE on 2011-10-16
> **Hakunka-Matata said:**
> Your /dev/sda drive has no unallocated space on it.Three of the four partitions (primary) availabe to a MBR disk are in use.
To install Ubuntu to a partition you would need to shrink/resize /dev/sda3 to make room for another partition, which would be an Extended partition.  Within that Extended partition /dev/sda4, you would then create all the other partitions(Logical) for the Ubuntu system(s).  It's really quite easy and quickly done, once you're ready to do it.

[This link]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions") is nothing more than a bookmarker in the **Partitioning link** in my signature.  It sounds like you're all backed up already?  I'm guessing your windows installation is a Windows XP installation, correct?

It came with Windows 7.

Anyway, I can't get Wubi to work right now. It keeps crashing/quitting partway through the installation. ""cannot download the metalink and therefore the ISO"

---

### Post by Leaf on 2011-10-16
Back up your personal info FIRST!

Windows will overwrite the GRUB install if you install Linux first.
I'd recommend a fresh install of Win7, then install linux afterwards.  It will auto-configure GRUB (your booting partition) to give you a choice between windows or ubuntu.

Since you have no room on your primary HD, you'll have to remake the partitions by formatting, or shrink them down to make space for Linux as Hakunka-Matata said.

I'd recommend against installing with WUBI, that will forever tie your linuxos to your windowsos and make it difficult for you if (heaven forbid) anything happens to windows!

---

### Post by Leaf on 2011-10-16
In order for you to shrink your partition and avoid WUBI, you'll need to make a USB or CDROM liveCD.
Look at option 2 on this page to walk you through what you'll need and how to make a LiveCD or LiveUSB
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

This will give you an OS 'outside' your current installs, allowing you to perform the necessary operations.

---

### Post by MarjaE on 2011-10-16
> **Leaf said:**
> In order for you to shrink your partition and avoid WUBI, you'll need to make a USB or CDROM liveCD.
Look at option 2 on this page to walk you through what you'll need and how to make a LiveCD or LiveUSB
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

This will give you an OS 'outside' your current installs, allowing you to perform the necessary operations.

I already made two live CDs. An old one for Ubuntu 10.10 and a new one for Xubuntu 11.10. I've been doing this from the latter; how would one install without a live CD or another live disk?

---

### Post by Leaf on 2011-10-16
No, that's definitely the way to go!  Just covering all the bases to be sure :)  The reason I said that is because you'll not be able to resize a partition while its in use, it requires an unmount of the drive altogether.

The program you'd use to resize the partitions is gparted, here's the site
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
you can sudo apt-get install gparted while booted from the liveCD if it's not present.  I'm pretty sure gparted is included in both ubuntu LiveCD images.

---

### Post by MarjaE on 2011-10-16
> **Leaf said:**
> No, that's definitely the way to go!  Just covering all the bases to be sure :)  The reason I said that is because you'll not be able to resize a partition while its in use, it requires an unmount of the drive altogether.

The program you'd use to resize the partitions is gparted, here's the site
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
you can sudo apt-get install gparted while booted from the liveCD if it's not present.  I'm pretty sure gparted is included in both ubuntu LiveCD images.

Neither the live cd nor Windows has any internet connection. I'll check to see if it has gparted though. (Yes it does)

---

### Post by MarjaE on 2011-10-16
Ran Windows Backup too, but, as usual it "did not complete successfully." Fortunately, both Back in Time and Deja Dup are set to back up both of my home folders. And I have the repair disk.

---

### Post by MarjaE on 2011-10-16
Attempted to run the regular Xubuntu installer, but the installer froze up at the screen where it asks for a wireless network.

---

### Post by Hakunka-Matata on 2011-10-16
Have you already created partitions for Ubuntu on your hard drive?

---

### Post by MarjaE on 2011-10-16
No. Some of the guides said this was best done during the installation process. Anyway, Windows is intact.

I downloaded the alternate live cd, but, unfortunately the computer will not boot from the alternate live cd.

---

### Post by MarjaE on 2011-10-20
After having so much trouble with Xubuntu 11.10, I reinstalled Ubuntu 10.10. So right now I have Ubuntu 10.10, Xubuntu 11.10, and Windows on separate partitions on that machine, instead of on Wubi, [and I have MacOS on this older machine].

I'm having some trouble though:

Firefox will not run. Whenever I try to start Firefox, including immediately after rebooting, the system claims that one Firefox window is already open and refuses to open another.

Evolution will not load the backup, claiming that the backup is corrupt. Since the Xubuntu partition is still available, is there any way for Evolution in 11.10 to create a backup which is readable to Evolution in 10.10?

The psmouse-alps patch triggers an unspecified "unhandlable" error when I try to install it.

Also, how can I give the Ubuntu installation and possibly the Xubuntu one [or the Kubuntu one if I decide it's the best replacement for Xubuntu] permanent bookmarks to the other partitions?

---

### Post by oldfred on 2011-10-20
Do not know about your errors.

Is one of your NTFS partitions separate from the operating system or seen as d:? I do not recommend writing into the Windows system partition from Ubuntu but a shared NTFS partition works well.

I have my Thunderbird & Firefox profiles in a shared NTFS partition. Then I can use it from my XP, and various Ubuntu installs.

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

Some of the add-ins complain as I may not have the same verison of Firefox and some things seem different but I have not have an issue using Firefox & Thunderbird in multiple systems. I also copy entire profile to my protable when we travel & copy back when we return.

---

### Post by MarjaE on 2011-10-20
I don't use Thunderbird, it tends to crash, to disappear email, to be unable to import, etc. It's actually one of the reasons I've reinstalled 10.10.

---

### Post by oldfred on 2011-10-20
Firefox is essentially the same. They both have profiles in slightly different locations.

---

### Post by MarjaE on 2011-10-20
I got Firefox working [the old uninstall the application, delete the preferences, and reinstall the application] trick. I copied my backups and my bookmarks list into the Firefox folder. But Firefox doesn't recognize my preferences, bookmarks, etc. either directly or as importable files.

---

### Post by searchfgold6789 on 2011-10-20
You can use Firefox Sync.

---

### Post by MarjaE on 2011-10-20
I just had to copy my old preferences folder into the newly-created preferences folder. I had been putting the two preferences folders side-by-side within the Firefox folder.

Evolution, psmouse, and file operations still need work though.

P.S. file operations fixed!

---

### Post by oldfred on 2011-10-20
Both folders can be there, but the profile.ini has to refer to the one you want to use. That is how you can redirect to the profile directory anywhere on your system, by editing profile.ini.

---

### Post by MarjaE on 2011-10-20
Since the psmouse-alps-dkms patch doesnt work in Ubuntu 10.10 and it works badly in Xubuntu 11.10 I'm coming full circle to Ubuntu 11.04. I'll still be able to use Gnome 2, I'll have the touchpad bugs sorted out, and hopefully, I'll be able to get Evolution working again too...

Oh. "Could not find the release notes."

---

