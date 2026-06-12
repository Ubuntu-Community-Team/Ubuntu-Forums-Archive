---
title: "Dualboot - Cannot access linux boot - doesn't recognize root partition as ext4"
date: 2023-06-10
forum: Installation &amp; Upgrades
---

### Post by linuxcmt on 2023-06-10
Hello,

I am running a dual boot system (Windows 11 pro + Ubuntu 22.04.1) which was working perfectly; however I ran out of storage on the root partition (the / and /home partitions are stored separately in /dev/sda6 and /dev/sda7 respectively), and so I ran GParted as a live boot; I shrank the C: windows partition, and then moved the SWAP partition (/dev/sda5) and root partition to fill the free space. I then expanded the size of the root partition, and then used the remaining space to increase the home partition. I ran GParted and after following the suggested actions (chkdsk /f and reboot twice), it ran and when restarting the computer everything seemed to be normal.

 However, a few days later when I was on windows I got a Blue Screen Error whilst out of the room, and from then on when restarting the computer I entered the GNU GRUB 2.06 command-line boot loader, and I was unable to access linux at all, I could only get to my windows OS using the 'exit' command, which seemed to be running but with some errors such as not running apps correctly. After a few hours it found an error and asked to restart to repair drivers etc, which seemed to improve the windows side of things, however I a still stuck in the conmand-line boot loader rather than having access to choosing either Ubuntu or Windows as normal. 

Having loaded a live USB version of Ubuntu I can see and access all of my /home partition which I have copied to an external hard drive, however I cannot do the same for the root partition, and I see from GParted that the filesystem type for the root partition is listed as unknown, where previously this was ext4. The same issue seems to have occurred for the linux swap partition, where the filesystem type is unknown, where previously it was listed as 'linux-swap'. I can still access and view the contents of the root partition on the live boot, but I am very confused as to what the issue is and how I can fix it.

I have read through many similar cases but cannot seem to find where someone has had the same issue; many tutorials seem to suggest using 'set root=(hd0,1)', then 'linux /vmlinuz roo=(hd0,1), then 'initrd /boot/intrid.img', and finally 'boot', to tell the computer where it needs to boot from, however I have been unable to work out what this is actually doing, and in the cases I have found, the root files system is recognized in the GRUB command-line when using the ls command, whereas for me it appears to be an unrecognized filesystem. I also really don't want to make my situation work but I really need to have access to Linux to run simulations for my thesis, and so have been looking into absolutely any option to remedy my issue, if anyone has any suggestions or further information I would be extremely grateful.

Note** I have downloaded Grub-Repair and generated a report which can be viewed at:
[https://paste.ubuntu.com/p/5PWjXq685B/](https://paste.ubuntu.com/p/5PWjXq685B/)

Thanks.

---

### Post by tea for one on 2023-06-10
> Having loaded a live USB version of Ubuntu I can see and access all of my /home partition which I have copied to an external hard drive, 
Good start.
Have you backed up your Windows data?

---

### Post by yancek on 2023-06-11
Did you 'move' the / (root filesystem) partition or did you simply increase the size?    Have you tried running a filesystem check (fsck) on the / partition?  When you use the set root command, do you have it pointing at the correct partition (sda6)?  Do you see the expected output when you run the ls command from Grub command line?

Line 136 of boot repair shows no os on sda6 where you indicate Ubuntu was originally installed (/ partition).  Line 146 shows no fstab file.  However, lines 166 and 167 show Linux filesystem on sda6/sda7.  I would try running fsck on the / partition from the Ubuntu live usb.

---

