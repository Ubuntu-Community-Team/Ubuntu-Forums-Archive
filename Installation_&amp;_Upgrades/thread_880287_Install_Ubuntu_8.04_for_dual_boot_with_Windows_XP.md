---
title: "Install Ubuntu 8.04 for dual boot with Windows XP"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by fhsm on 2008-08-04
**Goal**: Install 8.04 for dual boot on an old system running XP Home SP2 with 10 GB of free space in a single system NTFS partition.

I started with the instructions at [[COLOR="DarkOrange"]APCMag.com[/COLOR]]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1") which are quite good.

I defragmented my drive using  Win XP’s built in defrag utility.  I then booted from my Hardy CD and started the install as described in the APC Mag instructions.  I used the guided partition resize size slider-bar to set the new partition to 7 GB and clicked past the "Write Changes" warning.

After working for 2 min or so my system returned an error and then displayed the existing partitions (the little FAT16 partition and the full system NTFS partition) and gave no further useful options.  I tried twice more with smaller partitions before giving up and rebooting into windows without any problem.

In windows I freed up as much free space as I could.  I found clearing system restore points as described by Microsoft [[COLOR="DarkOrange"]here [/COLOR]]("http://support.microsoft.com/kb/555367")quite helpful.  After freeing an additional 7 GB I ran the Windows’ defrag tool.  I repeated the Ubuntu install which failed again, in the same way.

I then moved onto a free (beer) 3rd party defrag utility, [[COLOR="DarkOrange"]Auslogics Disk Defrag[/COLOR]]("http://www.auslogics.com/disk-defrag"), which was much better.  I also used [[COLOR="DarkOrange"]Auslogics Registry Defrag[/COLOR]]("http://www.auslogics.com/en/software/registry-defrag"), also free (beer), for the heck of it.  

After Registry Defrag finished the system rebooted into XP.  I rebooted the system from the Ubuntu CD.  Finally I was able to get the Ubuntu installer to make and then install into a 7 GB partition as described at APCMag.com.

The system then rebooted and GRUB defaulted me into Hardy, which ran without any problem.  I restarted and tried to boot into Win XP.  After the initial XP splash the system dropped to the reduced resolution safe-mode screen and wanted to check drive integrity using chkdsk.  Amazingly, after running the three stage check, XP rebooted the system, I selected XP from the GRUB menu and it boot into XP just fine.

**Take home**:
Starting from a very old XP install it will save you some time if you defrag a couple of time using something better than the XP utility.  It’s also important to have a good bit more space free than you plan to use for your Ubuntu partition.  Finally, XP is going to stop your heart for a second on the first reboot, but it should turn out okay in the end.

Hope this helps someone.

---

### Post by bizdcrawl on 2008-08-04
Look at you showing off!!! I cant get the wireless working on my dual boot which I installed couple of hours ago. Walk me on how to get that working. =;

---

### Post by bizdcrawl on 2008-08-04
There you go, I thanked you for your first post too. :oops:

---

