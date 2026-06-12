---
title: "how to install Ubuntu without losing partitions?"
date: 2015-06-11
forum: Installation &amp; Upgrades
---

### Post by AkwatiKata on 2015-06-11
I am trying to install Ubuntu on my old laptop. It has two partitions. One partition contains Vista and the other is the Recovery partition and also contains the drivers. I want to install Ubuntu over the Vista partition; i.e. overwrite it, but keep the Recovery partition. 
When I start the installation (from USB) I get three options: 1- Install alongside Vista; 2- Erase disk and install Ubuntu; 3- Something else.
I don't want the first option because I want to use that whole partition (300 GB) for Ubuntu.
The second option wants to erase everything including the Recovery partition and I don't want that.
The third option makes me pull my hair out! When I select the Vista partition, I get a pop-up that says "No root file system is defined. Please correct this from the partitioning menu."
What does that even mean? Yes, I am a total noob :( 
In the main screen there are three 'devices' listed; first:/dev/sdb (I assume this is the hard drive itself); second: /dev/sdb1 (this is the Vista partition); third: /dev/sdb2 (this must be the Recovery partition)
I have clicked on the second one so it is selected (it becomes orange)
Below that there is "Device for boot loader installation" and there is a drop menu. In that drop menu I have selected the Vista partition.
How do I 'define a root file system'? I thought it was 'defined'; it says NTFS. So what am I doing wrong?
I know I can make a dual boot or back-up the Recovery partition on a USB or even go for the full erase, but I don't want that (just yet). I want to keep the Recovery partition and overwrite the Vista partition.
Thanks

---

### Post by mikewhatever on 2015-06-11
...but the recovery partition won't work if you remove Vista, so why keep it?

PS: As you are new, try a tutorial: [http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation).

---

### Post by v3.xx on 2015-06-11
I don't know if it still applies, but use to be a bug with gparted (linux) and Vista.  I would use a window's partitioning manager to create a free space (no format).  Then run the ubuntu installer.  It will then give you the option to install to free space on your hdd.

---

### Post by ubfan1 on 2015-06-11
Use /dev/sdb for the location of the bootloader, and after you select the sdb1, look at the various drop-down choices, one for "use as" and make it ext4, another drop-down is mount point, choose "/" or root.  And also select the "format" checkoff.  Do read the tutorials.

---

### Post by mastablasta on 2015-06-12
/ or root file system should be a Linux file system (such as ext4, btrfs etc.). root (or /) in Linux is same as c:\ in windows.

indeed, the easiest way to create a dual boot is to have some free unformatted disk space available and only 3 partitions occupied (in MBR style which Vista and XP use).

---

### Post by AkwatiKata on 2015-06-19
> **ubfan1 said:**
> Use /dev/sdb for the location of the bootloader, and after you select the sdb1, look at the various drop-down choices, one for "use as" and make it ext4, another drop-down is mount point, choose "/" or root.  And also select the "format" checkoff.  Do read the tutorials.

Hurray! It worked!:p I am now posting from my laptop that now has Ubuntu. Thanks!):P

---

### Post by v3.xx on 2015-06-19
Hurray! :D

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

