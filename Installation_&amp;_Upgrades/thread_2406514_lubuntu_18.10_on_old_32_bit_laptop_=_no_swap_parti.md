---
title: "lubuntu 18.10 on old 32 bit laptop = no swap partition?"
date: 2018-11-21
forum: Installation &amp; Upgrades
---

### Post by famewolf on 2018-11-21
I installed lubuntu 18.10 on an old 32 bit Acer Aspire 3000 (2gb ram, 128GB ide ssd sis chipset everything..video, sound etc)....it took some doing because it would stop right after the b43 firmware warning messages and do nothing...no black screen like x was starting...nada....through I found through pure luck that after logging into a shell via ctrl-alt-f2 I was able to type "startx" and the gui came right up...I did the normal install telling it I wanted the whole drive encrypted with LVM.   It installed overnight and the next morning it booted up into a 640x480 resolution gui....no big deal there...I have a custom xorg.conf that gives 1280x768 using vesa and it quickly was corrected.  I've noticed however that no swap partition was created and it allocated the entire length of the ssd.   I installed zram-config to see if it gave any difference in "feel".  I know that by default zram-config takes 25% of available memory and makes a ram disk swap however in both cases swap continued to show 0 available/used.   Is this a glitch or is it expected behavior?  I can't say the laptop is running terribly but I would have expected a little swap to be available.  I'm reasonably certain it's not because I have an ssd installed because the older IDE ssd's mimic being an IDE hard drive.

---

### Post by 23dornot23d on 2018-11-21
You might find your answer in this thread ....... [https://ubuntuforums.org/showthread.php?t=2392004](https://ubuntuforums.org/showthread.php?t=2392004)

Since Ubuntu 17.10 they are now using swap files ...........

You probably already have a swap file.

**cat /etc/fstab**

Someone else may be able to give more clarification ...... 

I have just heard its used now instead of a swap area in the partitioning - like we used to have.

---

### Post by ajgreeny on 2018-11-22
The command ```
free -mw
``` will show you exactly how much swap you have, and yes, it is now a swap file by default, not a separate partition,

If you have upgraded having previously had a swap partition, or clean installed and used"Something Else" in the installation, continuing to use old partitions, you may find that a swap partition is in use but it is no longer necessary.

---

### Post by famewolf on 2018-11-22
Appreciate the kind, on point feedback!

---

### Post by famewolf on 2018-11-22
Ok I finally got back to the actual laptop and did both the "free -mw" and the "cat /etc/fstab".  I'm not seeing anything to indicate a swapfile is in use.  

```

[FONT=monospace][COLOR=#000000]              total        used        free      shared     buffers       cache   available[/COLOR]
Mem:           1946         465         519          14         105         856        1256
Swap:             0           0           0
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a device; this may
# be used with UUID= as a more robust way to name devices that works even if
# disks are added and removed. See fstab(5).
#
# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
/dev/mapper/luks-97936e6b-df0e-41ed-ac10-2ec5730f5a2a /              ext4    defaults,discard 0 1
tmpfs                                     /tmp           tmpfs   defaults,noatime,mode=1777 0 0
[/FONT]
```

*conclusion*  As previously thought, no swap was allocated.  I followed the instructions here:  [https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)   to allocate a 2G swapfile and set a swappiness of 10.   I'd say this was a genuine bug.

---

