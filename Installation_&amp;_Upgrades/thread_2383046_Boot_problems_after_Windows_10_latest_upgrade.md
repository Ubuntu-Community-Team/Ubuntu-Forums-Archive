---
title: "Boot problems after Windows 10 latest upgrade"
date: 2018-01-20
forum: Installation &amp; Upgrades
---

### Post by magdaleen-ballot on 2018-01-20
Good morning,

I have a dual boot: Windows 10 / Ubuntu 16.04.
After the latest upgrade of Windows 10 I got into grub rescue mode, not being able to run either Windows or Ubuntu.
I opted to try and restore grub using the Boot-repair disk, opting the 'Recommended Repair'.
The url on the info at that stage is:
[http://paste.ubuntu.com/26416416](http://paste.ubuntu.com/26416416).

After this I got Windows to run immediately but no grub menu (and hence no option to start Ubuntu)
The 'BootInfo' summary I did after this can be found at:
[http://paste.ubuntu.com/26421385](http://paste.ubuntu.com/26421385)

I would rather not re-install ubuntu, so I would be greatful if somebody can help me out here.

Kind Regards
Magdaleen Ballot

---

### Post by oldfred on 2018-01-20
Windows had a bug going back years for BIOS/MBR installs.
It "forgets" to write Linux logical partitions back into partition table.
```
 /dev/sda4         583,417,854 1,250,263,039   666,845,186   5 Extended
/dev/sda5       1,224,990,720 1,250,263,039    25,272,320  82 Linux swap / Solaris 


```

If you only had one Linux partition it starts two sectors after start of extended and ends somewhere before start of swap.

 backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 


You can use testdisk or parted rescue to restore.

Another user just posted with same issue.
[https://ubuntuforums.org/showthread.php?t=2382978&p=13732318#post13732318](https://ubuntuforums.org/showthread.php?t=2382978&p=13732318#post13732318)

       Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)

---

