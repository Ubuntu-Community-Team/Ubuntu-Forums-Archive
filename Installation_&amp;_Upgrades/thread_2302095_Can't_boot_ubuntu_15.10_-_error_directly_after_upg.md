---
title: "Can't boot ubuntu 15.10 - error directly after upgrade"
date: 2015-11-07
forum: Installation &amp; Upgrades
---

### Post by streak3 on 2015-11-07
I just upgraded from Ubuntu 15.04 to 15.10 and I may have caused my own demise.. System indicated reboot was necessary after all packages installed and cleanup complete (removed obsolete packages).  Screen was blank for awhile so I did a power off/on (this may have been my issue), though I saw no activity going on w/ harddrive. Now receive

fsck from util-linux 2.26.2
/dev/sda1 contains a file system with errors, check forced.
/dev/sda1: Inodes that were part of a corrupted orphan linked list found. 

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
            (i.e. , without -a or -p options)
fsck exited with status code 4 
The root filesystem on /dev/sda1 requires a manual fsck

BusyBox v1.22.1  (Ubuntu  1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) _

I am not knowledgeable of Ubuntu (user for a year, but very much a newbie).  I have searched the forums and tried different avenues, but none have helped.

Any help would be greatly appreciated... thanks in advance

---

### Post by oldfred on 2015-11-07
Must be unmounted:
Try "e2fsck -f /dev/sda1". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.

   #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

And it that does not fully work you may need to use an alternative superblock.
      
 List backup superblocks:
sudo dumpe2fs /dev/sda1 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda1

Try to never power down a system, remember the elephants:
      
 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by streak3 on 2015-11-07
Thanks oldfred!! I will try when I get home. Got discouraged and went out for a beer !!

---

### Post by oldfred on 2015-11-07
And you did not offer me one. :(

---

### Post by streak3 on 2015-11-07
I OWE YOU A BEER!!!!  Worked like a champ!!!

---

### Post by oldfred on 2015-11-07
Glad that worked. :)

You can post as solved.

Someday a world tour and I will collect a beer or cup of coffee. :)

---

### Post by fernando60 on 2016-01-05
Worked for me too!!! Many thanks!!!

---

### Post by streak3 on 2016-02-02
Further question on this.. I shut down normally each time, but always have to go through the above e2fsck routine.. any thoughts on a permanent fix?

---

### Post by oldfred on 2016-02-03
If you shutdown normally, you should not need fsck, only after a forced shutdown with power switch may it be required.
If system seems to hang on shutdown or while running, then remember the elephants.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

Also may be worthwhile to see if hard drive is ok.
In Disks, click on tools icon in upper right and Smart Status. It can run lots of tests on drive, but all I know is whether it says drive is good or not. And if not usually time for a new drive.

---

