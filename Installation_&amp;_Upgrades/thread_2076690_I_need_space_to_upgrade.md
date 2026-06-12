---
title: "I need space to upgrade"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by wsfield99 on 2012-10-26
Hi,

I have included a screen shot showing my current hard drive configuration.  I would like to upgrade to the new version of Ubuntu but I do not have enough space on my active partition.  As you can see I have about 23 gigs of unformatted room left on my hard drive.  What do I need to do to move my current settings (which took me a long time to configure), so that I can create more space and perform a successful upgrade?  Thanks in advance, Scott

---

### Post by funicorn on 2012-10-26
You need to reboot and boot into ubuntu livecd.

In the livecd, open terminal, type `sudo gparted`, then in gparted:

1. You need to shrink the extended partition and enlarge the root partition, both of which can be done by right-clicking on the target partition and choosing 'resize partition'. 

1. Shrink the extended partition to a smaller size. Make sure the RESULTED blank space is  in front of the extended partition, NOT after it. 

2. Enlarge the root partition. Make sure the new blank space is added to the TAIL of the root partition, NOT to the head of it.

3. How large your root partition can be depends how much of the extended partition is shrank. 

4. Do that with CAUTION. Make sure every single click is without mistake. After the steps, remember to click on the 'Apply' button in the gparted panel, then reboot your compute.

---

### Post by dino99 on 2012-10-26
what you should do:

-inside sda2 extended partition, create a swap partition and a /home partition
- then set /etc/fstab with the new uuids

Formatting/creating partition(s) need to be done on unmounted partition. So from a livecd/usb, use gparted to do it. Later you will be able to move your data & settings into the new /home partition instead of actual home folder.

here is how i do installation:
[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

and here my fstab as an example to set yours: (sudo gedit /etc/fstab)

proc                                       /proc  proc  nodev,noexec,nosuid 0 0 
# 
UUID=9e61e83e-bca9-43cf-aa90-5a68892213fa  /      ext3  errors=remount-ro  0  1 
UUID=5d8d1ee1-f5af-40a1-a45d-dbc570808523  /home  ext3  defaults,relatime  0  2  
UUID=0a9ca7f0-6eeb-4b21-b70f-670fa600de16  none   swap  sw                 0  0

---

### Post by lykwydchykyn on 2012-10-26
If you don't already do it regularly, it may be sufficient just to do:
```

sudo apt-get clean

```

This cleans out the package cache, which can get quite huge after doing updates for a long time.

Otherwise, this may be a good time to move /home to a separate partition.  I recommend doing this in case you ever need to reinstall Ubuntu from disc.

See this link for a how-to:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by wsfield99 on 2012-10-27
> **lykwydchykyn said:**
> If you don't already do it regularly, it may be sufficient just to do:
```

sudo apt-get clean

```This cleans out the package cache, which can get quite huge after doing updates for a long time.

Otherwise, this may be a good time to move /home to a separate partition.  I recommend doing this in case you ever need to reinstall Ubuntu from disc.

See this link for a how-to:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)


I've run sudo apt-get clean and still do not have enough space.  I have been trying to follow the instructions in the above link but I am stuck on the Setup Fstab step.  This step requires that you add the following lines however I do not understand exactly what is required.  # (identifier) (location, eg sda5) (format, eg ext 3 or 4) (some settings)  UUID=??????? /media/home ext 3 nodev, nosuid 0 2.  This is my information /dev/sda1: UUID="3536ac82-a5a0-42ec-96f3-4861cc4dff44" TYPE="ext4"  
/dev/sdb1: LABEL="KINGSTON" UUID="FE2E-8B8B" TYPE="vfat"  
/dev/sda5: UUID="7f2a3e16-6d15-452a-a1cf-7eb8e72c12c3" TYPE="ext4" , I just don't know how to format it correctly for the Fstab.  Thanks again in advance, Scott

---

### Post by wsfield99 on 2012-10-28
I've run sudo apt-get clean and still do not have enough space.  I have  been trying to follow the instructions in the above link but I am stuck  on the Setup Fstab step.  This step requires that you add the following  lines however I do not understand exactly what is required.  #  (identifier) (location, eg sda5) (format, eg ext 3 or 4) (some settings)   UUID=??????? /media/home ext 3 nodev, nosuid 0 2.  This is my  information /dev/sda1: UUID="3536ac82-a5a0-42ec-96f3-4861cc4dff44"  TYPE="ext4"  
/dev/sdb1: LABEL="KINGSTON" UUID="FE2E-8B8B" TYPE="vfat"  
/dev/sda5: UUID="7f2a3e16-6d15-452a-a1cf-7eb8e72c12c3" TYPE="ext4" , I  just don't know how to format it correctly for the Fstab.  Thanks again  in advance, Scott

---

### Post by critin on 2012-10-28
What I have done successfully is boot into live cd/usb and delete the extended partition.  Then resize the main to take up the unused space.

There is always danger of losing something when messing with partitions, but this has worked for me.

---

