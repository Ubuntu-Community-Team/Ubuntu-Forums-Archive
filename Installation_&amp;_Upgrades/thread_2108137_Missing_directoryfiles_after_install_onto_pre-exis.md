---
title: "Missing directory/files after install onto pre-existing BTRFS partition"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by rmdegennaro on 2013-01-23
What I did was "routine" for me, but perhaps a bit weird otherwise.  I had two 1.5TB HD's that I was using to test/play around with BTRFS.  They were formated to about 1.3TB and mounted on one Ubuntu system at /home/Storage/BTRFSTemp.  I loaded them up with files and what not, taking up about 1TB.  

After working with it a bit, I decided to reload my regular Kubuntu 12.04 desktop using them as the main drives.  I had planned for this, and left empty partitions on each drive.  So each drive has 4 partitions, 1GB, 2GB, 2GB and rest the BTRFS partitions.  I also moved all the directories to a directory called "Old_harddrive" on the root of the partition.  

During installation, I set the following:
[INDENT]SDA1 = /boot (ext3, formatted)
SDA2 = swap
SDA3 = swap
SDA4 = / (btrfs, not formatted)
SDB1 = swap
SDB2 = swap
SDB3 = swap
[/INDENT]
Then afterwards I added SDB4 to the BTRFS volume.  I forget the exact command.  Then I did: ```
btrfs filesystem balance /
``` Only after that did I go to look for the files.  But I can't find them.  :confused:  

When I do: ```
btrfs filesystem show
``` I get:
```
        Total devices 2 FS bytes used 1.11TB
        devid    1 size 1.36TB used 1.11TB path /dev/sda4
        devid    2 size 1.36TB used 1.11TB path /dev/sdb4

``` And a "df" using btrfs says used is 1.11TB.  

When I do: ```
du -h -d1 /
``` everything looks normal except that I see 9.9GB total for the installation.  That is typical for a brand new installation (with other stuff I've installed since).  

If I try a locate command on "old" with all possible case combinations (maybe I fat-fingered something), the directory does not show up.  

I'm at a loss.  Maybe I don't understand BTRFS enough and lost the files.  Not a big deal, because I just copied them from other systems.  But I'd like to know how I messed up, and perhaps the installer should warn people before they get themselves into a fix with real data.  

So anyways, any help is greatly appreciated.  Thanks in advance.

---

### Post by rmdegennaro on 2013-01-29
Did a bit of rereading and looking.  The *buntu installation process creates subvolumes on the BTRFS partition.  There is the "@" subvolume for / (root) and then "@home" subvolume for /home.  All my files were in the main partition, without subvolume.  If I mount the partition without any subvolume arguments, I see my old files.  

Maybe not a bug in the installer, but I should check the installer (especially new versions) to see if there was a warning I missed.  Because this is non-obvious and I'm not sure non-techies would figure it out.

Interesting side note, the subvolumes seem to be directories in the main volume.  Kinda cool...

---

