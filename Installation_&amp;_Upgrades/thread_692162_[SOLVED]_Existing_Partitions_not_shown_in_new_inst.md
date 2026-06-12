---
title: "[SOLVED] Existing Partitions not shown in new installation"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by sourabhsharma149 on 2008-02-09
Hello Friends,

I am trying to install kubuntu on  my existing partition scheme as

1) Primary Partition : 30 GB ( Vista)

2) Extended Partion:         i)   25 GB ( D Drive)
                                          ii)   25 GB ( E Drive)
                                         iii)   10 GB ( F Drive)
                                         iv)   /boot ( Gnome ubuntu)
                                         v)   / ( Gnome ubuntu)
                                         vii) FREE PARTITION 7 GB <---

I want to do it on 7 GB free partition.
BUT when I try to install from  live cd of kubuntu then it doen't show my existing partition but a complete 120 GB disk and ask to create new partion table...
I am sure by this i will end up with spoiling my existing scheme...
Please help how can opt from my exiting partion the / for kubuntu..

Thanks

---

### Post by taurus on 2008-02-09
From the liveCD, open a terminal and post the output of this command.

```
sudo fdisk -l
```

---

### Post by The Avatar of Time on 2008-02-09
Okay just to make sure that I understand, you are only using one hard drive right? Assuming that is the case this might help, when using the Kubuntu live cd did you select 'manual' or 'guided' partittioning? Generally when the partitioner starts up the first option is something like 'use entire disc' and you do not want to do that. There should be an option to partition manually. That is what you want. Turn your free space you are wanting to use to Ext3 or file system of your choice then mount to root '/'. Then make sure that that is the ONLY partition that is going to be formatted, don't want to loose any important stuff. That should install Kubuntu to that partition. You will have to choice a place for grub also. Just make a point not to overwrite the existing one, though if you do you can restore it from the cd you installed off of. I hope this helps, if I am way off here let me know and I'll try to do better.

---

### Post by sourabhsharma149 on 2008-02-09
Thanks Avatar....That's the trouble I am using manual but still getting no option to select my desired partition..

---

### Post by sourabhsharma149 on 2008-02-09
One more strange thing when I run gparted in ubuntu(my well running installed one) it shows the same type of display means no partitions but single 120 GB Hdisk.....but fdisk -l shows the correct result....

---

### Post by The Avatar of Time on 2008-02-09
Hmm, that is odd. You only have on primary partition and the rest extended/logical right? I know you can only have a total of I believe four primary partitions or else the rest of the disc will be marked unusable but if you should be able to have as many extended ones as you would like. Does there happen to be a + beside your extended partition where you can view more of it? I know I have had five or six partitions on one disc before. I usually do the first three as primary and the rest extended though. Do you have a way to post a screen shot of your partitioning table?

---

### Post by sourabhsharma149 on 2008-02-09
root@sourabh-laptop:/home/sourabh# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           14333       14594     2096128    c  W95 FAT32 (LBA)
/dev/sda2   *           8        3885    31147008    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            3885       14593    86014913+   5  Extended
/dev/sda5            3885        7532    29297430+   7  HPFS/NTFS
/dev/sda6            7533       11180    29302528+   b  W95 FAT32
/dev/sda7           12679       14593    15382206    b  W95 FAT32
/dev/sda8           11181       11204      192748+  83  Linux
/dev/sda9           11205       11569     2931831   83  Linux
/dev/sda10          11570       11812     1951866   82  Linux swap / Solaris
/dev/sda11          11813       12678     6956113+  83  Linux

Partition table entries are not in disk order

---

### Post by sourabhsharma149 on 2008-02-09
Hello Avatar...

I have 1 Primary then extended one....as above output of my screen I want to install Kubuntu on last ext3 partition (sda11) which is empty ...I formatted it and left blnak for future when i was installing ubunu...

---

### Post by The Avatar of Time on 2008-02-09
Well I can't say as I have ever encountered anything quite like this. Normally gparted works realy well. You could try installing qtparted and see if it can read the partition. 
/dev/sda2 * 8 3885 31147008 7 HPFS/NTFS
Partition 2 does not end on cylinder boundary.
I am not sure what this means but could it be causing a problem? I would try running gparted from a live cd and see if it sees anything more. I have had some weird problems where I have had to use a couple of partitioners like gparted and the one on the alternate install disc (cfdisk I think). I will look into this some more. I will be away for a few hours, then if nothing is fixed I will see what I can do. Could you get a screen shot of gparted and post it here? You should be able to use the print screen key to take a screen shot and crop it down for just gparted. GIMP works well for that. Sorry I can't do more now.

---

### Post by The Avatar of Time on 2008-02-09
Well I was going to put a screenshot of my gpated on here but I haven't figured out how to post images so..........

---

### Post by The Avatar of Time on 2008-02-09
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=59190&stc=1&d=1202593108[/IMG]

Perhaps this will work.....

Okay, there is how my gparted table looks, to do this for yours after taking a screenshot with gimp, go to 'additional options' below where you would write you reply and 'manage attachments' you can the upload it. the right click on the link to it to get the url. then click the 'insert image' icon above where you reply. give it the url address and that should work. I might be able to help more if I could see just what gparted is doing. Thanks.

---

### Post by sourabhsharma149 on 2008-02-18
Done that but at very heavy cost...

It was a dell partion in built with laptop that caused issue...

I had to recreate all my partition but more efficiently...

Now no more dell partition (basicaly for Windows)........

---

### Post by The Avatar of Time on 2008-02-19
Glad to see you got it taken care of.

---

