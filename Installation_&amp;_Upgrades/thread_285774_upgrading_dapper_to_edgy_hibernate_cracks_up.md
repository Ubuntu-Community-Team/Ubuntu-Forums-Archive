---
title: "upgrading dapper to edgy: hibernate cracks up"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by vikasrawal on 2006-10-27
I had dapper drake on my laptop. After I upgraded to edgy, on my second restart, the swap partition did not mount. dmesg says unable to find swap-space signature. 

I see that edgy upgrade has changed by /etc/fstab. This is what it looks like now.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=6c063a7d-e8aa-413b-871b-f580c8a7d40a / ext3 defaults,errors=remount-ro 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=e1dd9847-b175-41f0-81f5-f8b51c6d7c21 none swap sw 0 0
# /dev/hda5 -- converted during upgrade to edgy
UUID=44E4-AFE3 /mnt/dwin vfat users,owner,rw,umask=000 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /mnt/sda1       vfat    users,owner,rw,umask=000 0 0
/dev/sda2       /mnt/sda2       vfat    users,owner,rw,umask=000 0 0
172.16.12.2:/nfs/home  /nfs/home  nfs rw,rsize=8192,wsize=8192   0   0
172.16.12.2:/nfs/data  /nfs/data  nfs rw,rsize=8192,wsize=8192   0   0
172.16.12.114:/home  /mnt/backup  nfs rw,rsize=8192,wsize=8192   0   0
#//fas2/d  /mnt/samba  smbfs users,rw,uid=1000,gid=100  0   0

The uuid references were added by the upgrade.

When I say "swapon -a", it gives me the following error.

/dev/disk/by-uuid/e1dd9847-b175-41f0-81f5-f8b51c6d7c21: Invalid argument


When I say e2label /dev/hda6, it says

e2label: Bad magic number in super-block while trying to open /dev/hda6

It looks like /dev/hda6 needs to be repaired.

I don't know where to go from there. Any idea where to look for a solution?

VR

---

### Post by vikasrawal on 2006-10-28
It looks like the same problem as reported in [bug 42299]("https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/42299")

I can't understand what solution should one use in edgy. Please help. If I add resume=/dev/hda6 hibernation works okay. But is that the right way of doing it? The discussion on the bug seems to suggest a different way. Can somebody explain?

How is it that an old bug has survived in edgy?

Vikas

---

### Post by vikasrawal on 2006-10-28
It turns out the problem is there in Dapper Drake and is not cleared up if you upgrade to Edgy (instead of doing a fresh install). 

The solution to the problem was provided by Baishampayan Ghosh on [ILuGD mailing list]("http://article.gmane.org/gmane.user-groups.linux.delhi/13814").

Ubuntu developers may want to note and clear up the upgrade scripts to solve the problem.

VR

---

