---
title: "Ubuntu cannot boot and boot-repair didn't repair th boot problem"
date: 2015-11-19
forum: Installation &amp; Upgrades
---

### Post by fotios3 on 2015-11-19
Hallo,

i had installed Windows 7 along with Ubuntu. I removed the windows 7 Installation with the help of this site [https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows). Everything was ok. I restarted the computer and i was able to boot to ubuntu 15.10. When i tried via GParted the "[COLOR=#333333][FONT=Ubuntu]SYSTEM RESERVED[/FONT][/COLOR]" partition to delete and resize the ubuntu partition, the resize ended with error and the only option was to restart the computer.

The computer restarted in rescue mode and i was not able to boot into ubuntu. I installed boot-repair in a live-usb and it was not able to repair the boot of the ubuntu and i have the following url [http://paste.ubuntu.com/13350745/](http://paste.ubuntu.com/13350745/).

I tried to see with testdisk, the status of the partitions. It seems to exist a partition in ext4 format and one in hpfs/ntfs format. The second partition is not accesible.

Can anyone help me?

Thank you for any help.

---

### Post by oldfred on 2015-11-19
While you show a lot of data in sda5, the script did not show any grub files or fstab??
Are those files there or do you need to run fsck on sda5?
Or did something change.

I would first try this with sda5.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by fotios3 on 2015-11-25
I tried what you have suggested. The first command didn't succeed. Then i tried the second command. It failed in some inodes with the error "Error storing directory block information (inode=..., block=0, num=...): Memory allocation failed". I tried to fix this with the advice from this forum [https://phz.fi/2014/11/23/error-storing-directory-block-information-memory-allocation-failed/](https://phz.fi/2014/11/23/error-storing-directory-block-information-memory-allocation-failed/).

The advice was to use "debugfs -w -R "clri <...>" /dev/...". To fix manually all the inodes that could not be repaired from e2fsck. Although now e2fsck is executed without errors, i cannot boot in ubuntu.

Now in boot-repair tool i see the following url [http://paste.ubuntu.com/13500896/](http://paste.ubuntu.com/13500896/).

Is it possible to repair this problem or is it besser to reinstall ubuntu?

Thanks for any help in advance.

---

### Post by yancek on 2015-11-25
Your boot repair output shows sda5 as an ext4 (Linux) filesystem but there is no sign that Ubuntu or any Linux system is installed and none of the files that normally show there are listed.  Also, the grub.cfg file, which is the grub menu does not show.  It would probably be simpler to reinstall.

---

