---
title: "does my disk keep moving?"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by davidmaxwaterman on 2010-05-10
Hi,

I have a 1TB disk with a single partition that I mount via an entry in fstab.

Since upgrading to lucid, it usually fails to mount at boot time and I have to edit fstab to change the device.

Am I going crazy or does it keep moving around from device to device?

Max.

---

### Post by quadproc on 2010-05-10
> **davidmaxwaterman said:**
> Hi,

I have a 1TB disk with a single partition that I mount via an entry in fstab.

Since upgrading to lucid, it usually fails to mount at boot time and I have to edit fstab to change the device.

Am I going crazy or does it keep moving around from device to device?

Max.
The device identifiers such as /dev/sda1 are assigned by the operating system acccording to its own rules.   This means that the same hardware can get different /dev identifiers at different times.  For example, plugging in or unplugging a USB device may change the /dev identifier(s).

The UUID was invented to get around this problem.  UUIDs are effectively unique.  You can find the UUIDs of your hardware by doing ```
sudo blkid
```You can use the UUID in fstab: here is what mine looks like
> cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=df533fe8-68c3-41f6-b030-e955feb580d9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=b071f4d5-5384-4267-9f78-99e163d6ea4a none            swap    sw              0       0
#/dev/sdc1
UUID=e61d892a-0341-4f99-a87b-c9345d9f9eb1 /home        ext3    relatime,errors=remount-ro    0    2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdg        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
Hope that this helps.

quadproc

---

### Post by davidmaxwaterman on 2010-05-11
> **quadproc said:**
> 
Hope that this helps.


Yes, I think it will help - time will tell though :)

One bonus question : I have an array with 10 disks. In my mdadm.conf file I have a DEVICE line specifying the devices. It seems that the DEVICE line is now pointless, and the ARRAY line can only work with a UUID. Is that correct? I suppose it might work if all the devices are used in an array, but otherwise, if they keep moving around, how can the DEVICE line be accurate?

---

### Post by quadproc on 2010-05-11
> **davidmaxwaterman said:**
> Yes, I think it will help - time will tell though :)

One bonus question : I have an array with 10 disks. In my mdadm.conf file I have a DEVICE line specifying the devices. It seems that the DEVICE line is now pointless, and the ARRAY line can only work with a UUID. Is that correct? I suppose it might work if all the devices are used in an array, but otherwise, if they keep moving around, how can the DEVICE line be accurate?
I am not using mdadm so I can't say from firsthand experience but, according to the way I read the documentation, you would need to specify the drives in the ARRAY declarations.  But the documentation is a bit vague so it just might be possible to use a UUID in a DEVICE declaration; perhaps an experiment is in order?

quadproc

---

