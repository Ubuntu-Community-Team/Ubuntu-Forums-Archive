---
title: "my /home is not monyed aftr 12.04 upgrade"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by sdblepas on 2012-04-26
Hi all
         I upgraded from 11.10 to 12.04 After finishing the upgrade when I rebooted the PC I get unable to mount /home press M or S I tried M then mount -a but it does not work in fstab I have
  **/etc/fstab: static file system information.**

  #
  **Use 'blkid -o value -s UUID' to print the universally unique identifier**

  **for a device; this may be used with UUID= as a more robust way to name**

  **devices that works even if disks are added and removed. See fstab(5).**

  #
  **               **

  proc            /proc           proc    nodev,noexec,nosuid 0       0
  **/ was on /dev/sda3 during installation**

  UUID=0d271cd9-4a95-4680-abd3-435bcad5eda4 /               ext4    errors=remount-ro 0       1 /dev/sda5       /home           ext4    defaults        0       2 /dev/sda1       none            swap    Filesystem      Size  Used Avail Use% Mounted on /dev/sdb3        28G   11G   16G  40% / udev            3.9G  4.0K  3.9G   1% /dev tmpfs           1.6G  1.2M  1.6G   1% /run none            5.0M     0  5.0M   0% /run/lock none            3.9G  164K  3.9G   1% /run/shm none            3.9G   57M  3.9G   2% /tmp/guest-k9fc5n /dev/sdb5       416G  256G  140G  65% /media/29990594-2993-429b-a4e0-7ed7c6c26966 /dev/sda1       1.9T  1.3T  575G  70% /media/sauvegarde /dev/sdc1       597G  517G   80G  87% /media/Serie /dev/sdd1       233G  117G  117G  51% /media/409423EB9423E260 sw              0       0
  while /dev/sdb5 should be the /home
  Any I dea? Thanks /dev/sda6       none            swap    sw              0       0 and in df -h

---

### Post by oldfred on 2012-04-26
Welcome to the forums.

You post of fstab seems to be missing line endings so it has run all together or is that how it is in your fstab?

From a terminal just copy & paste then highlight like you want to copy again and click on the # in the edit panel above your message to add code tags.

like this:

```
fred@fred-Precise:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd3 during installation
UUID=adc013e9-a23d-4a36-849b-3faeac005667 /               ext4    noatime,discard,errors=remount-ro 0       1
# swap was on /dev/sdc11 during installation
UUID=09367687-86d1-4fd0-9b81-2787d3196159 none            swap    sw              0       0
# swap was on /dev/sdc15 during installation
UUID=2c05178d-1e0e-4ae8-80e6-a700dc0d6eb9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05 /mnt/data ext3 relatime 0 2
# Entry for /dev/sda1 :
UUID=04B05B70B05B6768 /mnt/cdrive ntfs-3g ro 0 0
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657 /mnt/shared ntfs-3g defaults,uid=1000,nls=utf8,windows_names 0 0
fred@fred-Precise:~$ 

```

---

### Post by sdblepas on 2012-04-27
Hi
Thank you for your response, I'll try it tonight and will update the post 
Regards
Benjamin

---

### Post by sdblepas on 2012-04-27
Hi 
I fix it using 
#/dev/sda5       /home           ext4    defaults        0       2
UUID=29990594-2993-429b-a4e0-7ed7c6c26966	/home	ext4	defaults	0	2
Thanks all

---

