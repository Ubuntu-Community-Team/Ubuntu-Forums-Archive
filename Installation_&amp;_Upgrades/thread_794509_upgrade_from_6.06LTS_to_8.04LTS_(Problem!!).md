---
title: "upgrade from 6.06LTS to 8.04LTS (Problem!!)"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2008-05-14
Hi. I upgraded from Dapper to Heron and when i reboot, i get the information that it can't find my user in the home-folder.

I hade my home-folder on an own partition on my first hda (hda2) i Dapper.

When I look on my hdd from a live-session I see that the hda1 have a home-folder that is empty and on hda2 there are the user-folders and they have a lock-symbo on the folders. Under the upgrade I kept all configuration files.

Why can't I reach my home-folder and the my user in the second partition (hda2) it? How to fix that Ubuntu check on other partition than it is booting from.

/Azyx

---

### Post by Azyx on 2008-05-15
Mine FSTAB

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=b38f33f4-66e5-4fe4-bbef-00f88a494478 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=93ce9162-fb61-46d7-ac0c-58c29809cd84 /home ext3 defaults 0 2
# /dev/hdg1 -- converted during upgrade to edgy
UUID=a1d838c2-5b99-495e-a97e-bb63392f1978 /media/100GB_F ext3 defaults 0 2
# /dev/hde1 -- converted during upgrade to edgy
UUID=feb51e21-b316-4f18-b1d1-d161c3a646f7 /media/280GB_C reiserfs defaults 0 2
# /dev/hdf1 -- converted during upgrade to edgy
UUID=a598b288-df32-4404-8348-a47aa0fcd150 /media/280GB_D reiserfs defaults 0 2
# /dev/hdh2 -- converted during upgrade to edgy
UUID=1c7a4002-4a38-4e0d-9c1c-1b047ccb156c /media/280GB_E ext3 defaults 0 2
# /dev/hda3 -- converted during upgrade to edgy
UUID=f956f07f-9c3f-43d0-9d21-98ae673ef407 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

Here is my home-partition

# /dev/hda2 -- converted during upgrade to edgy
UUID=93ce9162-fb61-46d7-ac0c-58c29809cd84 /home ext3 defaults 0 2

but It don't seem to be mounted.

The mtab look like this:

/dev/sde1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-386/volatile tmpfs rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0


Why have I and emty home-folder in dev/sda1 /home, then It should bee in /dev/sda2 /home/  ?

---

### Post by mxg01 on 2008-05-15
I think that because it's mounting / first and that contains /home then it must be failing to mount /home from your other partition.

Try renaming the /home on /dev/hda1 to /xhome using your live CD. Then reboot and see what happens.

---

### Post by Azyx on 2008-05-15
After a nights sleep, I reboot to "normal-boot" and suddenly it have being solved autamagical. I did not do anything.

:)

---

