---
title: "Mounted Discs show up twice"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by acroporas on 2009-11-13
I just installed Karmic (clean install not upgrade) and after editing fstab to match how it was under Jaunty, all of my drives show up twice.

Can anyone tell me how to stop mounted drives from showing up 2x everywhere?  It looks like to me that when the drives get mounted they are not being taken out of the non-mounted drives list.

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#

#<file system> 					<mount point>				<type>	<options>			<dump>	<pass>
proc         					/proc        				proc	defaults		        0       0
/dev/scd0     					/media/cdrom0				udf,iso9660 user,noauto,exec,utf8	0       0
UUID=4408d510-b975-4f94-badd-39811ae4b9ad 	/					ext4	errors=remount-ro 		0       1
UUID=a11dd74b-02b5-42f1-ac52-ddd824ae12e3	/home/william/Videos/More		ext4	users,auto			0	0 
UUID=634605f8-a30b-4068-85d2-c3e44fc44f78	/home/william/Videos/Television		ext4	users,auto			0	0 
UUID=bd0afda3-5b79-48ef-bf5d-58346899dd86	/home/william/Videos/Movies		ext4	users,auto			0	0 
UUID=B09E-E509 					/home/william/Documents			vfat	users,rw,uid=1000,auto		0	0
```

---

### Post by Platypus123 on 2009-11-23
I'm having a similar problem:
[http://ubuntuforums.org/showthread.php?t=1335418]("http://ubuntuforums.org/showthread.php?t=1335418")

Help!

---

