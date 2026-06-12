---
title: "Swap"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by marzfel on 2011-08-23
There is simply no hibernate option in my power  drop down menu, I do not have a swap partition and I think that is the reason, I dont have a SWAP partition because for some reason  my hard disk wouldn't accept having more than 4 partitions .. I have got  one already for the stupid windows (which I need to keep) and 1 for its  recovery and its loader. So I have no space for a swap partition, and I  would really love it if ubuntu can hibernate. Any suggestions on how to create a SWAP partition without losing data?

---

### Post by lmarmisa on 2011-08-23
> **marzfel said:**
> There is simply no hibernate option in my power  drop down menu, I do not have a swap partition and I think that is the reason, I dont have a SWAP partition because for some reason  my hard disk wouldn't accept having more than 4 partitions .. I have got  one already for the stupid windows (which I need to keep) and 1 for its  recovery and its loader. So I have no space for a swap partition, and I  would really love it if ubuntu can hibernate. Any suggestions on how to create a SWAP partition without losing data?

Your hard disk wouldn't accept having more than 4 **primary** partitions. But you if you define an **extended** partition, you will be able to define several **logical** partitions inside. An extended partition counts as one primary partition. So, you can define 3 primary partitions, 1 extended partitions and several logical partitions if you wish.

Please, post the output of this command in order to check if you could reconfigure your hard drive for supporting more than 4 partitions:

```

sudo fdisk -l

```

Do you have an external hard drive?.

---

### Post by marzfel on 2011-08-24
That is great to know..if it would work please let me know how to do that.. here is the output:


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x43ef5841

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         196     1572864   12  Compaq diagnostics
/dev/sda2   *         196       11230    88629248    7  HPFS/NTFS
/dev/sda3           11230       37608   211878913    f  W95 Ext'd (LBA)
/dev/sda4           37608       38914    10486784   12  Compaq diagnostics
/dev/sda5           11230       37608   211878912   83  Linux

---

### Post by oldfred on 2011-08-24
You already have the one extended partition sda3 and it has one sda5 partition inside it. You can either shrink your sda5 to make room for swap, or shrink windows and expand the extended partition left into the unallocated you create. Then you can inside the extended create swap partition sda6. They will not be in order but do not have to be.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by lmarmisa on 2011-08-25
> **marzfel said:**
> That is great to know..if it would work please let me know how to do that.. here is the output:


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x43ef5841

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         196     1572864   12  Compaq diagnostics
/dev/sda2   *         196       11230    88629248    7  HPFS/NTFS
/dev/sda3           11230       37608   211878913    f  W95 Ext'd (LBA)
/dev/sda4           37608       38914    10486784   12  Compaq diagnostics
/dev/sda5           11230       37608   211878912   83  Linux

You have already defined an extended partition. This is **/dev/sda3**. So, no problem for defining logical partitions. But you will need some free space for it.

You will need to shrink the partitions /dev/sda5 or /dev/sda4 in order to release some space for the swap partition. If you shrink the Ubuntu root partition /dev/sda5 the procedure for creating the swap partition will be a little bit easier.

How much RAM do you have?.

---

### Post by marzfel on 2011-09-01
I have 2 GB of RAM,I will try doing this.. a 4GB SWAP would be fine right?

---

### Post by marzfel on 2011-09-01
right now from ubuntu the only options available for sd3 and sd5 is unmount and information..I am sorry I am a beginner but I am not sure how how am I supposed to shrink the volume/excise a part of this partition and then format it for swap..so I need to know how to shrink the ubuntu volume without affecting the running system and then creating a SWAP from the that space..can anybody help?

---

### Post by oldfred on 2011-09-01
You cannot from the running system. You have to use a liveCD so things are not mounted. If you had the swap the liveCD uses it and then you still have to unmount it with swap off.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)


I have swap partition but these are other choices.
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)
I prefer sleep and shutdown to hibernate.
'Dynamic Swap Space Manager' from the Ubuntu Software Center

---

### Post by marzfel on 2011-09-01
Thanks a lot..


I have done it... 


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         196     1572864   12  Compaq diagnostics
/dev/sda2   *         196       11230    88628224    7  HPFS/NTFS
/dev/sda3           11230       37608   211878913    f  W95 Ext'd (LBA)
/dev/sda4           37608       38914    10486784   12  Compaq diagnostics
/dev/sda5           11230       36825   205586432   83  Linux
/dev/sda6           36825       37608     6291456   82  Linux swap / Solaris


does that look better??



Now there is still no hibernation option..I thought this was because there was no swap, so what is it now?

---

### Post by zealibib slaughter on 2011-09-01
You need to activate swap and hibernation, here is how (from the swapfaq at ubuntu.com)
```


Activating the swap partition 
(If your swap is on your primary hard drive, you don't need to do anything here.) Now you need to find what partition your swap is on and what its UUID is. UUID?! you say? Well that's the Universally Unique IDentifier for the partition so you can reference it even if it's on a different mount point from boot-to-boot due to adding disks, etc. [LIST=1]
[*]Pull up a terminal and run gksu gparted & and enter your root password. The & lets this process run while still giving you access to the command line. 
[*]Right-click on your swap partition and choose *Information*. You should see the **Path** and **UUID** listed there. Keep this open for further reference. 
[*]
Run gksu gedit /etc/fstab & and look for the line that has *swap* in it. It should be the third column, separated by spaces or tabs. You can either use the path or the UUID to tell Linux where to find your swap partition. I recommend UUID because it'll stay constant even if you move the partition around or the disk somehow becomes sdb instead of sda or something like that. Make the appropriate edits and save the file. Your line should look something like this if you used UUID (with your UUID instead, of course): 
[LIST]
[*]UUID=41e86209-3802-424b-9a9d-d7683142dab7 none swap sw 0 0 
[*]or this if you used path: /dev/sda2 none swap sw 0 0 
[/LIST]
[*]Save and reboot to make sure the new swap gets activated properly at startup 
[/LIST]
Making the swap partition work for hibernate (optional) 
You only need to do this if you want to use your new, bigger swap partition to hibernate your computer. [LIST=1]
[*]Pull up a Terminal again and run cat /proc/swaps and hopefully you see the path to your swap partition listed there. If not chances are something went wrong in the steps above. Here's my output: 
[/LIST]
Filename                                Type            Size    Used    Priority/dev/sda2                               partition       2676732 73380   -1[LIST=1]
[*]gksu gedit /etc/default/grub & to pull up the boot loader configuration 
[*]Look for the line GRUB_CMDLINE_LINUX="" and make sure it looks like this (using your UUID of course) GRUB_CMDLINE_LINUX="resume=UUID=41e86209-3802-424b-9a9d-d7683142dab7" and save the file 
[*]sudo update-grub and wait for it to finish 
[*]gksu gedit /etc/initramfs-tools/conf.d/resume & and make sure its contents are resume=UUID=41e86209-3802-424b-9a9d-d7683142dab7 (with your UUID of course in place of mine). Save the file! 
[*]sudo update-initramfs -u 
[*]Reboot! 
[/LIST]Now you should be able to hibernate and resume! 

```

---

### Post by marzfel on 2011-09-01
it worked, thanks a million..

---

### Post by zealibib slaughter on 2011-09-01
NP just mark the thread as solved.

---

