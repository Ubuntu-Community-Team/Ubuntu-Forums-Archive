---
title: "Cleaning up my disk."
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by Hopalong on 2009-11-20
I have been using 8.10, even though i have 9.04 installed. I now want to try 9.10 in place of 9.04. How do I remove 9.04 (yes, I really want to - that other firm's system is going as well).

---

### Post by the8thstar on 2009-11-20
Just pop in the Ubuntu 9.10 live CD and select the Manual option when you get to disk partitioning.

---

### Post by Hopalong on 2009-11-22
"Just pop in the Ubuntu 9.10 live CD and select the Manual option when you get to disk partitioning." If it were that easy!!
  Qyestion 1: why doesn't gparted tell one the system that is in the partition? Get the code out of the 9.10 installer which does just that.
  (more to follow, but I.ll deal with them one at a time.)

---

### Post by RedSingularity on 2009-11-22
Why not do a system update to 9.10?

---

### Post by audiomick on 2009-11-22
> **Hopalong said:**
> "Just pop in the Ubuntu 9.10 live CD and select the Manual option when you get to disk partitioning." If it were that easy!!
  Qyestion 1: why doesn't gparted tell one the system that is in the partition? Get the code out of the 9.10 installer which does just that.
  (more to follow, but I.ll deal with them one at a time.)

Gparted will tell you which file system is in the partition.
Things with FAT or NTFS are Windows, or a data transfer partition that you had installed and should know about if it exists.

9.04 will be on an Ext3 file system. There will also be a Swap partition that belongs to Ubuntu.

---

### Post by Hopalong on 2009-11-22
> **RedSingularity said:**
> Why not do a system update to 9.10?
Because my disk was full of 8.4, 8.10, 9.4 and Windows partitions. I did get rid of enough, and am now using 9.10. And three of them were ext3, and there are now 4 undifferentiated swap partitions.

---

### Post by Hopalong on 2009-11-23
Question 2: of the 4 swap files, which one is 9.10 using and how can I find out?

---

### Post by Hopalong on 2009-11-23
Outstanding question: of the 4 swap files, which one is 9.10 using and how can I find out? [SIZE="2"]:):)[/SIZE]  Oops, ignore this one.

---

### Post by audiomick on 2009-11-23
As far as I know, and I could be wrong, Ubuntu uses all the swap partitions that are there when it gets installed, unless you specifically tell the installer not to mount them. I have two swap partitions on mine, spread over the two discs. This is supposed to be faster, according to what I read at the time of the installation.
Try looking at your system resources monitor. It shows you how big the swap is, but not how many there. However, if the stated size is the sum of all 4, then it is using all 4, I would think.

I saw a command to find out which swap is being used in a post in the last few days, but didn't write it down, I'm afraid.
Try searching the forum for swap..

---

### Post by presence1960 on 2009-11-23
> **Hopalong said:**
> Outstanding question: of the 4 swap files, which one is 9.10 using and how can I find out? [SIZE="2"]:):)[/SIZE]  Oops, ignore this one.

boot into ubuntu 9.10, open a terminal and run ```
gksu gedit /etc/fstab
```

your swap partition will be there and identified by a UUID #, here is my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc7 during installation
UUID=36d96022-7809-48c5-b527-7c7a156f8480 /               ext4    errors=remount-ro 0       1
[COLOR="Red"]# swap was on /dev/sdc5 during installation
UUID=a7907e24-9e12-4b51-8d78-7995579d955a none            swap    sw              0       0[/COLOR]
```

Note the red and UUID for swap.

Now one more thing:

Open a terminal and run ```
sudo blkid -c /dev/null
```

Match up the Karmic swap UUID with the swap partition that matches. There is your 9.10 swap partition. Make note of the partition (i.e. sda6 as an example)

---

### Post by audiomick on 2009-11-23
Hi.
I just tried what presence1960 ( who, incidentally, seems to know what he is talking about. I have seen lots of posts from him, and wouldn't assumed to contradict him :) ) suggested.
Both of my swaps turn up in both of the queries, so I still think it is possible that the machine could be using all 4

---

### Post by presence1960 on 2009-11-23
> **audiomick said:**
> Hi.
I just tried what presence1960 ( who, incidentally, seems to know what he is talking about. I have seen lots of posts from him, and wouldn't assumed to contradict him :) ) suggested.
Both of my swaps turn up in both of the queries, so I still think it is possible that the machine could be using all 4

Possible. Anything that happens does not surprise me. Stay in this community and you will see all the weird stuff that can happen to an OS.

---

### Post by oldfred on 2009-11-23
I am surprised that presence has not recommended running the boot info script that he has in his signature. It will help you identify what is where. I learned from him to recommend it whenever someone is not sure of their configuration and has boot issues. But I still like to shoot from the hip with a quick solution sometimes.

I am in the process of reconfiguring my system to make Karmic the primary and I have 3 drives, XP and 3 installs of Ubuntu. I run the script after making changes to make sure where everything is. I also like to chainboot and need to know what is in the MBR and PBR and the script is the best tool for documenting that.

---

### Post by presence1960 on 2009-11-23
> **oldfred said:**
> I am surprised that presence has not recommended running the boot info script that he has in his signature. It will help you identify what is where. I learned from him to recommend it whenever someone is not sure of their configuration and has boot issues. But I still like to shoot from the hip with a quick solution sometimes.

I am in the process of reconfiguring my system to make Karmic the primary and I have 3 drives, XP and 3 installs of Ubuntu. I run the script after making changes to make sure where everything is. I also like to chainboot and need to know what is in the MBR and PBR and the script is the best tool for documenting that.

Not a bad idea, why don't you run the script in my signature. Do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.35 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Hopalong on 2009-12-06
Thanks Presence: the fstab told me what I need to know. It appears that 8.10 uses one swap file, and 9.10 another. The othe two I presume wer used by 9.04 and whatvere came before that: I can therefore, I presume, delete them. I shall soon close this thread, unless some one wants to continue it? :D

---

### Post by presence1960 on 2009-12-06
> **Hopalong said:**
> Thanks Presence: the fstab told me what I need to know. It appears that 8.10 uses one swap file, and 9.10 another. The othe two I presume wer used by 9.04 and whatvere came before that: I can therefore, I presume, delete them. I shall soon close this thread, unless some one wants to continue it? :D

Glad to hear you got it sorted out! Enjoy Ubuntu.

---

### Post by Hopalong on 2009-12-16
Thanks to all for your help and advice. The disk is now clean, running 8.10 and 9.10 and with a data partition that both can read and write to, and all allocations are a reasonable size. I sometimes think I'm winning!:biggrin:

---

