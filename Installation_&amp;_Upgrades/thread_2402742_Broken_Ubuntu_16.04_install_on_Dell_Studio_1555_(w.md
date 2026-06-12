---
title: "Broken Ubuntu 16.04 install on Dell Studio 1555 (want to upgrade to Ubuntu 18)"
date: 2018-10-03
forum: Installation &amp; Upgrades
---

### Post by wog on 2018-10-03
Okay...!
I have a Dell Studio 1555. I installed Ubuntu 16.04 LTS on it. 
Somewhere along the way, it seems to have become a broken install. 
It currently boots up with the message: "The volume boot has only 3.6 MB disk space remaining."
The first problem is that when I look at About This Computer, the disk size is listed as 487.9 GB, and I don't have all that much on it.
The second problem is the wireless doesn't work.

I thought: Okay, I can fix this problem (and possibly others) by updating to 18.04, so I used Rufus to make an up-to-date USB booter and tried to boot off it.
The third problem seems to be that the laptop won't boot from the thumb drive, and when I try to press F12 to select the thumb drive to boot from, the laptop freezes, forcing me to do a hard reset from the power button. 

I am not that far from being a beginner, but I am apparently unable to cling to beginner status, so here I am. Tell me what to do and I will do it.

James

---

### Post by Autodave on 2018-10-05
Try this:  Shut down and disconnect every cable from the laptop. Remove the battery. Let it sit like that for 10 minutes. Reinstall battery and power cord and your USB install medium.  Try now to boot to that and see if it works.

---

### Post by wog on 2018-10-07
Always a bit of one to overdo it, I disconnected every cable, removed the battery, and then let it sit overnight like that. 
I reinstalled the battery and the power cord and then started up the laptop. The thumb drive flashed, so I know it's detecting it, but after pressing F12 twice (to get the laptop to let me choose what to boot from), the start-up process froze, forcing a reboot.

The last time I looked at the start-up procedure, there didn't seem to be a way to choose to boot from USB. It does give the option for booting from a DVD, so I'm trying to remember how to make a bootable DVD from Windows 10. 

If you know how to make a bootable DVD in Windows 10, or how to make a bootable DVD from a bootable Ubuntu USB, I'd really appreciate being told or being pointed at the link. 

Thank you for your help.

PS: 
When I look at the Disks window, I see some things that puzzle me. 
There's the hard disk, which makes sense. 
There's the DVD burner, which makes sense.
Then there's the 495 GB Block Device, labeled "/dev/ubuntu-vg/root" which does not make any sense to me.
And then there's the 4.3 GB Block Device labeled "/dev/ubuntu-vg/swap_1" which is almost certainly the swap partition.

In the diagram for the Volumes, the first partition is marked "Filesystem Partition 1, 511 MB Ext 2".
After that is an odd arrangement of 500 GB sliced in half horizontally. 
The top half reads "Extended Partition, Partition 2, 500 GB".
The bottom half reads "Partition 5, 500 GB LVM2 PV".
Then on the far right is a partition which reads "Free Space, 1.1 MB".

Does this make any sense to you? Is it possible that I am trapped in a tiny partition somewhere, and the 500 GB partition is inaccessible to me?
It makes no sense to me that there is a 500 GB chunk of drive with two simultaneous Partition names.

Thx

---

### Post by wog on 2018-10-07
Update:
I managed to find an Ethernet cable and hooked it up to the laptop. I think I fixed the problem I had with the wireless (although I have not yet tested it).
The problem with the available disk space remains. Until I get that solved, I can't update to Ubuntu 18 because there's not enough disk space to update.

---

### Post by wog on 2018-10-07
Further update:
After trying to mount the 500 gb partition mentioned above and failing, I finally decided if I couldn't get at it, it wasn't worth trying to save.
I then tried to format it, and got this message:
=========[ START ]=============
Error creating file system: Command-line `mkfs.ext4 -F -L "Files" "/dev/sda2"' exited with non-zero exit status 1: mke2fs 1.42.13 (17-May-2015)
mkfs.ext4: inode_size (128) * inodes_count (0) too big for a
	filesystem with 0 blocks, specify higher inode_ratio (-i)
	or lower inode count (-N).

 (udisks-error-quark, 0)
==========[ END ]=================
Now I don't know what to do. One possibility I am thinking of is that I'm faced with a failing hard drive. The trouble is I don't know how to find faulty sectors on the disk and how to mark them so they don't get used in the future. Or maybe it's too late for this drive and I simply need to replace it, although how would I know?

Does anyone have any ideas on how to figure out what the issue is and how to fix it?

---

### Post by wog on 2018-10-08
Still a further update:
I got into the BIOS and discovered there actually *was* a way to select a USB drive, and changed the boot order. I formatted the entire disk and installed fresh, so I can now get at the entire drive. The count of how much hard drive I have is a little less than the entire drive, so perhaps whatever was bad about the disk has been marked so I can use the disk without fear, although I'm still going to be watching it to see if there are problems later on.

I have no idea what that earlier stuff was indicated by the screens mentioned earlier, but for the moment, the problems are fixed. I am running version 18, I have access to the majority of the drive, and the wireless is fixed. I'm inclined to call this problem solved.

Any last-minute advice would be appreciated, if someone knows the solutions to any of them problems mentioned earlier, or if anyone has a link to discussion about how to find and mark bad sectors on a disk. The automatic scripting of Ubuntu is making Linux easier and easier to operate without knowing what one is doing, but a little theory is better than not nearly enough when things go pear-shaped.

Thx!

---

