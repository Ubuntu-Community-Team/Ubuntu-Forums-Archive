---
title: "Multiple swap partitions?"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by jhnhskll on 2011-05-02
After running Disk Utility today, I noticed that I has not one, but three different swap partitions. This is likely due to several fresh Ubuntu installs in the past. Now, I only need to be able to choose between Natty and Windows 7 on boot, and I'd like to get rid of the unneeded swaps. So how do I know which one is the one I want to keep?

---

### Post by BrockStrongo on 2011-05-02
> **jhnhskll said:**
> After running Disk Utility today, I noticed that I has not one, but three different swap partitions. This is likely due to several fresh Ubuntu installs in the past. Now, I only need to be able to choose between Natty and Windows 7 on boot, and I'd like to get rid of the unneeded swaps. So how do I know which one is the one I want to keep?



I'm having a similar problem. I have attached a shot of my partitions in case anyone want to take a look. Also, what's up with the unallocated spaces.

P.S. I installed 11.04 but then reverted to 10.04. This problem didn't exist in the original install of 10.04

Thanks

---

### Post by lechien73 on 2011-05-02
After booting Ubuntu, I would open a terminal and type:

```
swapon -s
```

This will display which partition is currently used as swap space.

---

### Post by ratcheer on 2011-05-02
I think Ubuntu will use all available swap partitions, simultaneously. You can use swapoff to deactivate the ones you don't want, then you should be able to delete them with a partitioning utility.

Tim

---

### Post by Dutch70 on 2011-05-02
I believe the installer goes by your hdd space to create your swap partition, it's likely that the one your using is the smallest one you have. 
Your swap partition should be equal to, or slightly larger than your phyisical RAM if you want to be able to hibernate successfully.

Please open Gparted & take a screenshot of your partitions. Use the "Select area to grab" function to get a good sized screenshot & attach it to your next post using the paper clip in the toolbar.

Also post the output of...
```
sudo fdisk -l 
```
That's a lower case L

---

### Post by Uewd on 2011-05-02
I have a question, can we use the Ubuntu CD and run the setup and delete Swap partitions?

---

### Post by oldfred on 2011-05-02
Fstab auto mounts your swap. It may be only mounting one or both and usually by UUID.

#To see your UUID and partitions:
sudo blkid
sudo fdisk -l
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

To make sure you did not make any errors remount fstab, if no errors it just returns, or it will tell you what it has a problem with. Do not reboot until you resolve errors.
```

sudo mount -a
```Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive. 
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by Dutch70 on 2011-05-02
BrockStrongo

Myself along with many other people would be happy to help you if you start your own thread. Trying to help more than one person in a single thread makes it more complicated than it has to be, and is unfair to the OP.

Uewd, Yes you can. If you want more info on it, see the message above.

---

### Post by BrockStrongo on 2011-05-02
> **Dutch70 said:**
> BrockStrongo

Myself along with many other people would be happy to help you if you start your own thread. Trying to help more than one person in a single thread makes it more complicated than it has to be, and is unfair to the OP.

Uewd, Yes you can. If you want more info on it, see the message above.

Sorry about the hijack.
I started a new thread.
Thanks

---

### Post by jhnhskll on 2011-05-03
Well, uh, I ran swapon -s and it gave me dev/sda8. So i deleted the other swaps with Disk Utility. :( Bricked my startup for some reason. Just trying to restore grub now somehow (can only boot into windows using a boot cd.

---

### Post by Dutch70 on 2011-05-03
Well that was no where near what I asked you to do.

---

