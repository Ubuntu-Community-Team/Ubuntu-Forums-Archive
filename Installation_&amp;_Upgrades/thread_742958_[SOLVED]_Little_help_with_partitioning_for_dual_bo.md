---
title: "[SOLVED] Little help with partitioning for dual booting XP and Ubuntu"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by Spacenoodle on 2008-04-02
Hey everyone, firstly i found [ this guide ]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm") and tried to follow it. But when i get to step 5, i don't have the slider, i have the options "Guided - use entire disk" (with a suboption which is my hdd which is selected) or "Manual". 

My laptop is a Fujitsu Lifebook S Series, and for some unknown reason when i got it, it came with 2 partitions on the HDD. 1 is 100gig and that's got XP on it, and the other is free space with 20gig. I was figuring to delete the 20 gig partition and put ubuntu there. But there's no easy way of doing that.

Since i've never used the manual partitioner before i figured i should post here and ask. Can anyone help?

---

### Post by louieb on 2008-04-02
Since I don't want to guess. Would like you to post your partition table.
If internet works with the live CD heres how to do it.
Open Application>Accessories>terminal
run (thats a lowercase L at the end)
```
sudo fdisk -l
```
cut and paste the output in you next post.  
Later, Lou.

---

### Post by Spacenoodle on 2008-04-02
Hey thanks for your reply, here's what i get. 

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b427b42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11945    95944704    7  HPFS/NTFS
/dev/sda2           11945       14594    21273600    7  HPFS/NTFS
ubuntu@ubuntu:~$
```

EDIT: On a totally unrelated note, ubuntu installer is fantastic, i'm using a web browser on my wireless network and running terminal commands....

---

### Post by housam on 2008-04-02
> **Spacenoodle said:**
> Hey thanks for your reply, here's what i get. 

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b427b42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11945    95944704    7  HPFS/NTFS
/dev/sda2           11945       14594    21273600    7  HPFS/NTFS
ubuntu@ubuntu:~$
```

EDIT: On a totally unrelated note, ubuntu installer is fantastic, i'm using a web browser on my wireless network and running terminal commands....

- Use the partitioner tool in your live cd to create two partitions for ubuntu 
- boot from the live cd and then go system >> admins. >> partition editor
- You need to delete the 2nd partition and create one partition for the root with mount point ( / ) ext3 format ( 19 GB ) and other partition as a swap ( 1 GB is ok )
- After finishing the partition task start to install ubuntu and when it comes to the partition choice, choose to do it manually ( you already did ) and assign them manually )

Good luck

---

### Post by Spacenoodle on 2008-04-02
Sure, what does the option "round to cylinders" mean and should i check it or leave it unchecked?

---

### Post by housam on 2008-04-02
Check it , It'll help shaping the partitions w/out broken cylinders .

---

