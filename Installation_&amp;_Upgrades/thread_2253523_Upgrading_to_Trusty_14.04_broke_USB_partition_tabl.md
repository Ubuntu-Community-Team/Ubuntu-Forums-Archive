---
title: "Upgrading to Trusty 14.04 broke USB partition table"
date: 2014-11-20
forum: Installation &amp; Upgrades
---

### Post by biocyberman on 2014-11-20
I am having a serious problem. I installed Ubuntu 12.04 on an USB and plugged the USB to the back of my workstation. I have a RAID array attached to the workstation, it is dedicated for data storage. The setup has been running fine, and I could update the it normally. Recently I run 'do-dist-upgrade' to upgrade the OS to Trusty 14.04. The upgrade seems to finish alright. But when I tried to reboot the server, it could not boot at all. At first I thought it is something about GRUB. But running "rescue system" or live Desktop DVD could not detect the USB. "**parted**" command could not detect the partition table in the USB. The the USB somehow was rendered to "read-only" device and I can't even format it.  How could things have gone that bad?

---

### Post by oldfred on 2014-11-20
USB hard drive or USB flash drive?

Flash drives have more limited lives. You do want to set to minimize writes, but probably need to have a backup/duplicate.

In another thread sudodus posted that often a flash drive changing to read only is the first sign of failure.

---

### Post by irv on 2014-11-20
If you jumped from 12.04 to 14.04 this might have been the problem. First when doing an upgrade you need to make sure you have all the latest updates then you have to upgrade in steps like 12.04 - 12.10 - 13.04 - etc. I find it easier to just backup all my data and then do a clean install.

---

### Post by oldfred on 2014-11-20
After errors system also typically mounts file system read only.
Did you try full e2fsck on / partition?

Did you have any ppa or proprietary drivers installed. Those almost always cause issues with upgrade, so upgrade never fully completes.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by ajgreeny on 2014-11-20
> **irv said:**
> If you jumped from 12.04 to 14.04 this might have been the problem. First when doing an upgrade you need to make sure you have all the latest updates then you have to upgrade in steps like 12.04 - 12.10 - 13.04 - etc. I find it easier to just backup all my data and then do a clean install.
Sorry but you are wrong about the update procedure having to be from 12.04 ->12.10 ->13.04 etc etc.

It is possible (and some people use it with no problem) to update from LTS to the next LTS, ie, in this case, 12.04 to 14.04. However, I agree with you that it is easier, and probably less likely to cause problems, to do a clean install; it also means you can get rid of some cruft from the OS, which always seems to build up if you try applications out, find you don't like them or need them, and later remove them.

Have a separate /home or /data partition and the whole clean install becomes even easier, though you should always have backups, just in case.

---

### Post by biocyberman on 2014-11-20
Thank you all very much for you replies. I think the suggestion that the USB failure is a plausible explaination. I have been using it for about a year as a system root drive. With intensive read/write operations it has been worn out. And the upgrade also involved alot of read/write has burst the drive. I have tried many different ways to recover it, i.e doing recovery with TestDisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)), parted and removing read-only flag. None of them works. I did not care to try boot-repair because the partion table is broken and boot-repair won't help.  So I tossed the drive. It is a Verbatim Store 'N' Go 16GB, USB 3.0 by the way. One lesson learnt, USB is not for regularly used root file system. 

Regarding some comments about upgrading process, I have done four upgrading for servers from 12.04 to 14.04, one from 10.04 -> 12.04 -> 14.04, all of these went well and I am very happy for the upgrade process. There was some issue with upgrading LDAP though, but I manage to solve it. SAMBA, MySQL, SSH, Apache servers all went smoothly. I set preference to only upgrade from one LTS version to next LTS version, so the suggestion of upgrading to non-LTS is not appicable.

---

