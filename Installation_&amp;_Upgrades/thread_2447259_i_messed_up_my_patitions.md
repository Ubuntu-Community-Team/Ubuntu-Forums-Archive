---
title: "i messed up my patitions"
date: 2020-07-15
forum: Installation &amp; Upgrades
---

### Post by kickass1955 on 2020-07-15
i messd up my partitions and made  / only 20 gig and  /home 200 gig. now i am running out of room.   can i tell ubuntu to use the 200 gig space?
gpart will not let me resize / partition....help....i do not want to start from scratch if i have to

---

### Post by aljames2 on 2020-07-15
This info to start, post in code tags the result of:  **lsblk**

Is this a fresh install?
Do you have your data backed up?
Are these LVM partitions or regular ext4 partitions?

---

### Post by kickass1955 on 2020-07-15
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0   9.1M  1 loop /snap/canonical-livepatch/95
loop1    7:1    0  96.5M  1 loop /snap/core/9436
loop2    7:2    0    55M  1 loop /snap/core18/1754
loop3    7:3    0  27.1M  1 loop /snap/snapd/7264
loop4    7:4    0    55M  1 loop /snap/core18/1880
loop5    7:5    0  29.8M  1 loop /snap/snapd/8140
loop6    7:6    0    16K  1 loop /snap/software-boutique/54
loop7    7:7    0  14.9M  1 loop /snap/ubuntu-mate-welcome/524
loop8    7:8    0  14.9M  1 loop /snap/ubuntu-mate-welcome/539
sda      8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1   8:1    0   260M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0    16M  0 part 
&#9500;&#9472;sda3   8:3    0 186.3G  0 part 
&#9500;&#9472;sda4   8:4    0   467M  0 part 
&#9500;&#9472;sda5   8:5    0 232.9G  0 part 
&#9500;&#9472;sda6   8:6    0   7.9G  0 part /
&#9500;&#9472;sda7   8:7    0 139.7G  0 part /home
&#9492;&#9472;sda8   8:8    0   132G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom  

3rd operating system...windows 10,  ubuntu 18.04, ubuntu mate 20.04.... i used gparted to use ext4 file system...20 gig  /,,,,200 gig  /home,,,100 gig swap...

---

### Post by kickass1955 on 2020-07-15
20.04 ubntu mate is the problem...wasnt watching what i was doing...fresh install... but a bear to install wifi drivers ...rtl8821ce drivers i have to build from scratch...2 hours  of work

---

### Post by kickass1955 on 2020-07-15
sda...6...7...8 are the new for ubuntu mate

---

### Post by kickass1955 on 2020-07-15
sda...6...7...8 are the new for ubuntu mate
i also noticed that   /    and   /home have same data

---

### Post by aljames2 on 2020-07-15
> 3rd operating system...windows 10,  ubuntu 18.04, ubuntu mate 20.04.... i used gparted to use ext4 file system...20 gig  /,,,,200 gig  /home,,,100 gig swap...

So you have 3 OS's installed?
sda6 is your MATE root? (7.9 Gigs)

Attempting to resize partitions is tricky and can result in data loss.  I recommend backing up all your data before doing anything.
Also, since these are not LVM you cannot resize them while mounted.  You would need a Live USB or CD to boot up to & you would need to make sure none of the partitions are mounted.  The Live USB has the Gparted utility on it already.  
NOTE: whenever you edit partitions, data loss is a real possibility.  Care should be taken.  Generally, it involves shrinking partitions to the right to be smaller, then moving those shrunken partitions to the right to make room for the expansion of the troubled partition.  However, moving partitions containing /boot off of their original sectors will cause the system to not boot and would require reinstallation of grub.

I would hold off a bit and get some other ideas here.  I don't do multi OS/multi boot systems.

---

### Post by kickass1955 on 2020-07-15
well can i tell ubuntu to go to /home instead of  /   ?
yes ubuntu mate is sda   6  7  8
i went to fast....my bad

---

### Post by kickass1955 on 2020-07-15
never mind....just gonna redo it  all

---

### Post by Impavidus on 2020-07-16
> **kickass1955 said:**
> ```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
...
&#9500;&#9472;sda6   8:6    0   7.9G  0 part /
&#9500;&#9472;sda7   8:7    0 139.7G  0 part /home
&#9492;&#9472;sda8   8:8    0   132G  0 part [SWAP]
```

3rd operating system...windows 10,  ubuntu 18.04, ubuntu mate 20.04.... i used gparted to use ext4 file system...20 gig  /,,,,200 gig  /home,,,100 gig swap...

That final line contradicts the output of the command. It says you've got an 8GB root partition (which is indeed too small), 140GB /home partition (reasonable) and a 132GB swap partition (insanely large). I suggest 25GB root, 4GB swap, the rest /home.

Assuming those partition are in the same order on disk, you could resize or move them. Expanding the root partition to the right is safe, quick and easy after you made room by moving the /home partition. But a fresh install may be better. Have you kept notes on how you installed the wifi drivers? I always keep notes when I have to do something non-trivial that I might have to repeat later.

---

