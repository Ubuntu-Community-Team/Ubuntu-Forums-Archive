---
title: "Some solution found about disappeared ide partitions"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by october1917 on 2007-04-20
As you can see here [http://ubuntuforums.org/showthread.php?t=414398](http://ubuntuforums.org/showthread.php?t=414398) there was a problem recognizing the /dev/hdx partitions after the upgrade.

It is because the 2.6.20 kernel uses the new PATA firmware which emulates the PATA drives to SATA drives. So in the /proc/partitions the PATA disks appear as SATA.

So, if you change the fstab, replacing the hdax to sdax the problems get solved!

Good luck. For more help about how to do this, post here.

---

### Post by realGaurab on 2008-04-28
> **october1917 said:**
> As you can see here [http://ubuntuforums.org/showthread.php?t=414398](http://ubuntuforums.org/showthread.php?t=414398) there was a problem recognizing the /dev/hdx partitions after the upgrade.

It is because the 2.6.20 kernel uses the new PATA firmware which emulates the PATA drives to SATA drives. So in the /proc/partitions the PATA disks appear as SATA.

So, if you change the fstab, replacing the hdax to sdax the problems get solved!

Good luck. For more help about how to do this, post here.
Can you please explain how to do this. I posted in your other thread ([http://ubuntuforums.org/showthread.php?t=414398](http://ubuntuforums.org/showthread.php?t=414398)) about me facing the same problem but got no help. 

Thanks.

---

### Post by ubnewbie2 on 2008-04-29
> **realGaurab said:**
> Can you please explain how to do this. I posted in your other thread ([http://ubuntuforums.org/showthread.php?t=414398](http://ubuntuforums.org/showthread.php?t=414398)) about me facing the same problem but got no help. 

Thanks.

I just discovered this problem myself.  You simply have to edit /etc/fstab and change any references to hdxy (where x is some letter and y is some number) to point to the device name that ubuntu now sees it as.  (I ran gparted to see what hard disks it though were in my machine and what it calls them - my /dev/hda1 had become /dev/sdb1)

---

### Post by realGaurab on 2008-04-30
> **ubnewbie2 said:**
> I just discovered this problem myself.  You simply have to edit /etc/fstab and change any references to hdxy (where x is some letter and y is some number) to point to the device name that ubuntu now sees it as.  (I ran gparted to see what hard disks it though were in my machine and what it calls them - my /dev/hda1 had become /dev/sdb1)
I edited my fstab but no luck. 

I checked gparted and noticed that the partition names had changed from /dev/hda1, /dev/hda2 to /dev/sda1, /dev/sda2.

Then I went to fstab. In fstab, instead of referring to the partition by name, it is referred to by uuid. So I looked up the uuid of /dev/sda1 by doing 'vol_id -u /dev/sda1' and it showed up the same uuid that was being used in fstab. Just to make sure I backed up my fstab and changed the uuid to corresponding partition name (like /dev/sda1) and then tried again and no luck. Looks like it doesn't want me to login in normal mode. :(

Do you want me to post my fstab info here?

---

### Post by ubnewbie2 on 2008-04-30
> **realGaurab said:**
> I edited my fstab but no luck. 

I checked gparted and noticed that the partition names had changed from /dev/hda1, /dev/hda2 to /dev/sda1, /dev/sda2.

Then I went to fstab. In fstab, instead of referring to the partition by name, it is referred to by uuid. So I looked up the uuid of /dev/sda1 by doing 'vol_id -u /dev/sda1' and it showed up the same uuid that was being used in fstab. Just to make sure I backed up my fstab and changed the uuid to corresponding partition name (like /dev/sda1) and then tried again and no luck. Looks like it doesn't want me to login in normal mode. :(

Do you want me to post my fstab info here?

Maybe.  Why not try mounting the drives using device names instead of UUID?

---

### Post by realGaurab on 2008-04-30
I tried replacing uuid with partition name as well and no luck. I manually added the line in red to see how it would act up if I replaced uuid with the partition name. I did comment out the uuid line when I had the red line uncommented.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>	<dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
[COLOR="Red"]# /dev/sda1	/		ext3	defaults,errors=remount-ro	0	1[/COLOR]
UUID=5ca1255d-4995-4c5b-8a23-167a96ac782e	/	ext3	defaults,errors=remount-ro	0	1
# /dev/sda7
# UUID=91e9c3d2-bd09-43b5-b8a2-b6da1eabce15	none	swap	sw	0	0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by ubnewbie2 on 2008-04-30
> **realGaurab said:**
> I tried replacing uuid with partition name as well and no luck. I manually added the line in red to see how it would act up if I replaced uuid with the partition name. I did comment out the uuid line when I had the red line uncommented.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>	<dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
[COLOR="Red"]# /dev/sda1	/		ext3	defaults,errors=remount-ro	0	1[/COLOR]
UUID=5ca1255d-4995-4c5b-8a23-167a96ac782e	/	ext3	defaults,errors=remount-ro	0	1
# /dev/sda7
# UUID=91e9c3d2-bd09-43b5-b8a2-b6da1eabce15	none	swap	sw	0	0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

I'm running out of ideas.  Are you sure the filesystem is ext3?

---

### Post by realGaurab on 2008-04-30
Yes, sda1 is ext3.

---

### Post by realGaurab on 2008-05-01
Ok, I finally found the solution to the problem. Problem was ATI driver had changed to envy. I did not have any driver installed previously for my display, neither resctricted nor using envy. After I installed EnvyNG and installed the ATI driver with automatic hardware recognition, everything was fine. I am now currently logged in in normal mode.

Thank you all for your help.

---

