---
title: "dual boot with Ubuntu already installed"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by davidranran on 2012-02-02
So I am currently on Ubuntu 11.10 and was wonder how to dual boot it with windows 7 while already running Ubuntu. I have looked around on google and it looks like I should have installed it with the option to erase everything and use the whole hard drive. I should have chosen to partition option. Im thinking I have to start all over, but it would be cool if there was another way.

---

### Post by darkod on 2012-02-02
There is always another way. :)

I assume right now ubuntu takes your whole disk. In short, you would need to:
1. Shrink one of the ubuntu partitions to create enough unallocated space for win7.
2. Format this unallocated space into one primary ntfs partition (this way you save one primary partition).
3. Boot with the win7 dvd and install onto the prepared ntfs partition. Windows will overwrite grub2 on the MBR so the computer will start booting into win7 directly.
4. Have your ubuntu cd at hand, boot with it in live mode and reinstall grub2 to the MBR.

There are plenty of tutorials on google. If you have some specific questions, you can come back here of course.

The most important, and first step, is to sit down and plan your hdd layout. What partitions you have right now, how you plan to create the unallocated space for win7, and what the hdd will look like at the end.

---

### Post by ajgreeny on 2012-02-02
So what exactly have you done so far;  your post does not help us much.

Do you have windows on the machine already?  
Have you taken the whole disk for Ubuntu?  
Do you still have some unallocated space left?  

Run the command ```
sudo fdisk -l
``` in terminal and copy the output back here, please.

It is easier to install windows first then add ubuntu, but don't despair, it is not difficult to do it the reverse way;  you will simply need to restore grub 2 to the MBR with a live CD/USB using a couple of commands.

---

