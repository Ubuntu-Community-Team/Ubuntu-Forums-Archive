---
title: "Install fails during disk partition."
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by bbunker on 2007-03-13
Hello, Any help on this would be appreciated... I am attempting to install with a dual boot (Windows XP) on a HP xw6200 workstation. I am closely following the instructions referenced in the install docs ([https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) and [http://www.psychocats.net/ubuntu/installing)](http://www.psychocats.net/ubuntu/installing)). My install fails in the disk partitioning step.

I would prefer to use the "Resize IDE1 master, partition #1 (...) and use free space. When I try this, I get an error saying that ubuntu was unable to free enough space. I should have enough free space because my disk is about 250 Gb and I'm currently only using about 13 GB for Windows. Oddly, if I click 'ok' on the error dialogue box, and try the same thing again, I don't get the error any more but the system never completes the operation. I've waited up to 15 minutes for a response at this point, and get nothing.

Although I'm not an expert on this, I have also tried using "manually edit partition table" and set up my own partitioning (I can provide details on request). When I attempt to perform this partition, however, I get some kind of error, but the error dialogue box is corrupted so that I can't read it. However, I am able to click the 'x' to close this box. At this point, I'm returned to the ubuntu 'live' desktop, and nothing has changed.

Fortunately, none of this has damaged my Windows system yet. However, I am completely stymied on the ubuntu install.

I would appreciate any advice about how to troubleshoot this problem. :confused: 

-BB

---

### Post by zvacet on 2007-03-13
Try again with &#733;manually edit partition table&#733;.here is how it can look:
1.root / partition=10-15GB(you can put more,depends of your needs,but I think this is enough)
2.home patition =rest of space exept
3.swap=1GB(maybe more depends of your ram)
All partitions are in ext3 format.
This shoud work without any errors.

---

### Post by bbunker on 2007-03-13
zvacet:

Thank you very much for your reply. I followed your directions but unfortunately didn't succeed with the ubuntu install. I give a detailed description of what happened below, hoping you can spot where it goes wrong:

1) I insert Ubuntu Linux 6.06.1 LTS CD (image checked with checksum and also by doing "Check CD for defects" from install menu) and booted machine.

2) ubuntu installs successfully as a live session.

3) Selected "install" and arrive at welcome screen, select English, Denver, my name, password, name of computer, and arrive at "Prepare disk space" screen.

4) Select "Manually edit partition table" and arrive at "Prepare partitions" screen.

Info displayed on "Prepare partitions" screen is as follows:

Partition Filesystem Size Used Unused Flags
------------------------------------------------
/dev/sda1 ntfs 232.88Gb 12.16Gb 220.72Gb boot
unallocated unallocated 7.84Gb

5) Click on /dev/sda1 and choose Resize to 47600 MB (this is what I want to keep as the Windows partition)

6) Click on unallocated portion (now 180.96 Gb) and click "new" to create Primary Partition, ext3, 15000 MB -- this is successfully added to list, though rounded to 14.6 GB. (I intend this to be my root "/" partition.)

7) Click on unallocated portion and click "new" to create Primary Partition, ext3, 173873MB - this is successfully added to list, though rounded. (I intend this to be my  home partition.)

8) Click on unallocated portion and click "new" to create Primary Partition, ext3, 2000MB - this is successfully added to list, though rounded to 1.95 Gb. (I intend this to be the swap partition).

9) Satisfied with partitioning, I click "forward", get new box to select "apply pending operations".

10) I click ok, and quickly get an error: "Error while resizing/moving /dev/sda1." No further options.

11) I click o.k. and am returned eventually to the live ubuntu session with nothing changed.

Note that before attempting this install, I defragmented my hard disk from Windows. This seemed to be successfully, though looking at the map of used space, there seemed to still be large gaps between files. My current suspicion is that there is not actually as much free contiguous space as reported by GParted.

Any ideas would be greatly appreciated.

Thanks in advance,
BB

---

### Post by prabhasbajaj on 2007-03-14
Same problem occured with me too
Solution-

Open your boot settings on system startup
n change your visual memory to max..
that shud do it
P.S: It worked for me for 6.06

---

