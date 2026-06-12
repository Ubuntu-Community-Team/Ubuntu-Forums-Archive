---
title: "ext4 to ntfs"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by rswaraj on 2010-09-19
Hi,
I had installed windows 7 in my laptop earlier, but later switched to UBUNTU. I formatted the  main drive (boot drive) to EXT4 and other drives as NTFS itself during the partition. Now, i again want to format the main drive to NTFS from EXT4. 
Using GParted, i tried to do so, but it doesn't seem possible. I have to unmount the boot drive first, but it did not give any permissions for that. Due to some reasons, i have to install windows in my laptop again. But EXT4 format doesnt allow to do so for boot drive. 

So, what can I do to overcome this problem.......please HELP !!

---

### Post by Rubi1200 on 2010-09-19
Are you using GParted from the LiveCD?

You also have to unmount the swap partition: right-click > Swapoff

---

### Post by maestrobwh1 on 2010-09-19
Boot from an Ubuntu Live cd, do 

sudo apt-get update && sudo apt-get install gparted.  Run gparted.

Reformat / recreate a partition for Windows.

Boot from the Windows disk. Install Windows to that partition (It really needs to be the FIRST partition or booting Windows is tricky).

Assuming you want to keep Ubuntu and do a dual boot, you will lose the option to boot into Ubuntu so...

You could then run the live CD again, and chroot into the Ubuntu partition and once that is accomplished run

sudo dpkg-reconfigure grub-pc 

which will cause grub to reinstall itself to the MBR, add itself to the boot menu along with the Windows OS on the disk.

Rather than chroot, you could run some grub commands from the live cd and get your boot back, but that is more detailed to me.  Someone else here might disagree, but it really is a preference on how to put grub back onto the MBR.

---

### Post by Rubi1200 on 2010-09-19
GParted is installed on the CD by default; no need to try and install it again.

---

### Post by rswaraj on 2010-09-19
Thank you for the suggessions...
I tried to swapoff the swap memory too....but still cannot be unmounted....
Is it necessary to run it from live CD???

---

### Post by Rubi1200 on 2010-09-19
> **rswaraj said:**
> Thank you for the suggessions...
I tried to swapoff the swap memory too....but still cannot be unmounted....
Is it necessary to run it from live CD???
Yes, in most cases it is better to work with partitions from a LiveCD. Turning off swap from GParted on the LiveCD should not be a problem.

---

### Post by Mark Phelps on 2010-09-21
Are you trying to reformat your main Ubuntu (Ext4) partition to NTFS?

You can't format a partition while it's in use, and you can't unmount the partition you're running from.

As said, you will have to boot using a LiveCD, ensure the partition you want to reformat is unmounted, and do it that way.

---

