---
title: "How do I partition disks for best performnce with VMware?"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by slope on 2008-07-02
The plan is to run Xubuntu 8.04 64 as a Host OS in VMware. From within Host I will run vmware workstation with several guest os.
I have played around with vmware now for a while and I decided to loose my dual boot and run vmware.
During testing vmware I have come to that for best performance I will run a slim but still user friendly host so I chose xubuntu. 
My plan was to have host os running from raid 0 with 2 disks preferable using the onboard raid adapter. Well that part did not work out for me so I guess software raid it is. 

My overall goal is to have best possible performance within the limitations of the hardware I have. No room for buying raid controller card or extra disks at the moment.
Ok here it goes lots of questions here:

1: What should I do when partitoning the drives, how many partitions should I choose and from which physical disk?  swap, /root, /home, /usr was the plan.  should I also have /var?
2: How can I best utilize the disks, as I have 5 disks and I will use 4 of them. I would not have ie winxp use all space within a 500 GB drive, but say max 50 GB. How can I set it up so I can use the free diskspace?
3: Could I take a given amount of all 4 drives to make up a raid 0 array, and will doing so actually give me max performance? (hw raid 0 gives better performance when adding additional drives is it also true for sw raid?)
4: If I could use space from all 4 drives for raid 0 array what partitions should I have running from that raid 0 array?
5: What filesystem should I choose for the different partitions? ie my /home directory will hold both smaller files but also music+movies collection. XFS, JFS or ReiserFS?
6: Does the choice of filesystem and partition play a big part when it comes to overall performance today? Reading articles on the net it seems people are divided on this.
7: Can I  set up boot from say a part of the winxp drive and then have xubuntu (host os) installed in raid 0, or best of all force linux to boot from a raid 0?
8: When installing apps and software from package manager synaptic, can i make sure everything is installed in /home?
9: If this was a pure windows box i would use raid 0 to install windows, and have all files/data on a separate drive. 
   Am i thinking correctly here when I will try to use 2 disks in raid 0 for the xubuntu+vmware? I'll guess most of the reading/writing of disks will take place from host xubuntu?

**My system:**
Intel Q6600
8 GB Ram
Asus P5N E SLI [Limitied to 4 x Sata]
2 x Cuda 750 ES 2 
2 x Cuda 500 ES 2
1 x Caviar 750
Bios version 801
OS Xubuntu 8.04 64 Bit

Hopefully someone can push me in the right directin here.

---

### Post by Pumalite on 2008-07-02
This might help some:
[http://ubuntuforums.org/showthread.php?t=385043](http://ubuntuforums.org/showthread.php?t=385043)

---

### Post by slope on 2008-07-07
Ok I ended up using 4 disks.
first drive is not in raid 0. Singel drive to have /boot + /root.

2 x hdd in raid 0 for /home and vmware.

1 singel drive for /tmp + /swap.

Those choices are based on tips I got on forums so I hope they ar enear optimal within the hardware and no raid controller.

---

