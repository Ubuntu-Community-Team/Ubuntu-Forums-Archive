---
title: "encrypted home login woe"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by psy-moon on 2010-02-07
Greetings all, heres my head-scratcher!
I installed ubuntu 9.10 to a fresh partition on a hd that already contains a windows xp.
During the install I opted to Require my password to login and to decrypt my home folder, (don't ask why, I regret it already).
The install went well, I think, but when it came to reboot time I wanted to check that I could start windows xp from the new grub boot loader. Windows started fine so I rebooted again to try my new install of ubuntu. Now the system seems to get stuck at the little spinning wheel icon. I tried to boot to recovery shell but after entering my name and password I get 
Unable to cd to '/home/myname'
I rebooted using live cd 
And mounted the file system as root
now I have chroot ed into the system but thats as far as my knowledge gets me.
I have googled to find the next step but am not finding a clear answer.
I have found this  [http://www.linux-mag.com/id/7568/2/](http://www.linux-mag.com/id/7568/2/)
And here I see I should have seen a screen entitled 


Record your encryption passphrase
But I didn't get to that screen.
So is there any elegant solution? or am I destined to wipe the install and start again?

Perhaps this problem is connected to the bug mentioned here [http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)
"quote"
**Optional encrypted partitions must be marked bootwait in /etc/fstab**

  
 In addition to the above, users who have configured any encrypted partitions in /etc/crypttab to start at boot time (i.e., not using the noauto option) should make sure that the filesystems on these volumes are listed in /etc/fstab if they are not mounted at a standard system mountpoint. Failure to do this on a desktop system will lead to problems from the X server and cryptsetup trying to control the console at the same time. At best, this will prevent the user from seeing the passphrase prompt; at worst it will also cause the X server to spin and consume 100% CPU. ([430496]("https://bugs.launchpad.net/bugs/430496")) 
"/quote"
I'm not sure, my /home is not on a separate partition.

/etc/crypttab is empty
# <target name>    <source device>        <key file>    <options>

/etc/fstab is
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=8e5f54dd-8d79-44da-9ddf-7f4e3bce2a64 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=32bcb9fc-ff2b-4e37-a259-1bfabee7cee7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by psy-moon on 2010-02-07
oh dear no help from the hive mind , no worrys then, its all fresh installs so wipe it and start again is the quick solution. pity seems like the sledge hammer to crack the nut :-(

---

