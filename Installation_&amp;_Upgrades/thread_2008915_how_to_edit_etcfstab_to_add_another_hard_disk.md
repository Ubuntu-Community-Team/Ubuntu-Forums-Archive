---
title: "how to edit /etc/fstab to add another hard disk?"
date: 2012-06-23
forum: Installation &amp; Upgrades
---

### Post by galactica147 on 2012-06-23
Hi All,

Recently I reinstalled Ubuntu 12.04 on one hard drive and now want to attach another one (containing all my previous data under /home) to the system. 

Although I found some tips and updated the /etc/fstat file as follows, rebooting the system shows that Ubuntu is unable to mount the new /home for me. 

Does anyone know how to fix this? 
I only add the very last line based on the original fstab file. 
Also, I think the very last line was the one appeared in my fstab file in the old Ubuntu system. 

Please advise. Thanks!

>>>>>>>>>

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=20bb8fa3-cf30-4a1d-8a3d-2d15511421f2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=61054ccf-ed5d-4495-b574-c0f11f8b57da none            swap    sw              0       0
UUID=8e4fca1b-15fd-460c-b995-1dfdd408bfff /dev/sdb1 /home ext relatime,user_xattr 0 2

---

### Post by darkod on 2012-06-23
1. You either use the UUID or /dev/sdb1, not both. Delete the /dev/sdb1.

2. The filesystem is written as 'ext' when it should be ext4 or ext3 or ext2 depending what you have. Probably ext4 but check it first if you can. So, you are missing the number.

3. I am not sure the options 'relatime,user_xattr' are correct to be used with /home, but if that was in the previous /etc/fstab, I guess it should work.

Delete the /dev/sdb1 and edit the ext to the correct filesystem, and give it a go.

---

### Post by galactica147 on 2012-06-23
Darkod,

Thanks a lot for your quick reply!

Just one question, how to check the number of the ext file system? This is an old hard drive and I will guess it is ext2, but not sure. Is this critical? 

Appreciate!

> **darkod said:**
> 1. You either use the UUID or /dev/sdb1, not both. Delete the /dev/sdb1.

2. The filesystem is written as 'ext' when it should be ext4 or ext3 or ext2 depending what you have. Probably ext4 but check it first if you can. So, you are missing the number.

3. I am not sure the options 'relatime,user_xattr' are correct to be used with /home, but if that was in the previous /etc/fstab, I guess it should work.

Delete the /dev/sdb1 and edit the ext to the correct filesystem, and give it a go.

---

### Post by steeldriver on 2012-06-23
Persnally I would re-check BOTH the fs type AND the UUID:

1. run fdisk to check the double check the /dev/sdxN designator

```
sudo fdisk -l
```2. run blkid to find the UUID for that block device

```
sudo blkid /dev/sdxN
```(where sdxN is the device identified from Step 1 e.g. /dev/sda1, /dev/sdb2 etc.)

3. find the filesystem type

```
sudo file -s /dev/sdxN
```In fact I think 'file -s' will give you the blkid as well so you can probably skip step 2

FWIW I have an 'old home' mounted in this way and the full fstab entry is:

```
# post-install re-map of shared /home on /dev/sda2
UUID=680778ec-f545-4c12-a8b5-1a03e6287fa6 /home           ext4    errors=remount-ro 0        2 

```Hope this helps.

**NB note that this will override any current /home that you have - if you want to mount this old partition _in addition to_ your current /home you will need to make a separate mount point for it e.g. /mnt/oldhome and use that in your fstab** - in fact you might want to do that initially anyhow just to make sure it mounts OK (since login will be difficult with a broken /home dir)

---

### Post by mfouwaaz on 2012-12-31
I did exactly as shown by steeldriver and it worked fine.  Thanks.  Now df -k shows as follows:

```
/dev/sda1       11391768 10279424    533608  96% /
udev              502628       12    502616   1% /dev
tmpfs             205120      788    204332   1% /run
none                5120        0      5120   0% /run/lock
none              512796      152    512644   1% /run/shm
/dev/sda3        9675828   152660   9031600   2% /mnt/oldhome
gparted        151027064 77142908  73884156  52% /media/sf_gparted
temp           151027064 77142908  73884156  52% /media/sf_temp
```

/dev/sda3 is the new partition.

But I yet get a 'This computer has only 546.4MB disk space remaining' warning.  Any idea on what maybe happening?

12.04 running on VirtualBox here.

---

### Post by dino99 on 2012-12-31
yeah, see that 96 % on the first line; you need to make room.

here is how to do a standard install:

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)


you can boot on a livecd/liveusb then use gparted to set the partitions as needed. Then run:

sudo update-grub

---

### Post by mfouwaaz on 2012-12-31
I booted with gparted live cd.  Then select /dev/sda1, right-clicked and selected Resize/Move.  How do I make room here?  Can you please explain the steps invovled?


Thanks!

---

### Post by mfouwaaz on 2013-01-01
It is all good now. 

The problem I had was that the SWAP partition was sandwiched in between.  I booted with gparted live cd, deleted SWAP and now I was able to extend dev/sda1 to the full possible extent.  Then I re-created SWAP.

Thanks for this great forum!

---

