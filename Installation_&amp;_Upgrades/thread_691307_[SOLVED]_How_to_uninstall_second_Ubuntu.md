---
title: "[SOLVED] How to uninstall second Ubuntu?"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by fourthofjuly on 2008-02-08
I had a dual boot WinXP & Ubuntu 7.10 working very well. I have downloaded themes & other software + updates installed.

However, I accidentally installed a second Ubuntu 7.10 on my system, which seems to have taken over the XP drives, so I cannot access them from my first Ubuntu install, which I want to continue with. (Grub loader shows 2 Ubuntu & 1 XP OS.)

I want to remove the second install of Ubuntu since it is not updated.... please help...

Output of mount command:

**devang@devang-desktop:~$ mount**
/dev/sda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda6 on /media/disk type ext3 (rw,nosuid,nodev)


Thanks & Kind Regards,

Devang.

---

### Post by Rocket2DMn on 2008-02-08
OK, there are a few steps to this process.
First you need to boot from either the LiveCD or to the [GParted LiveCD]("http://gparted-livecd.tuxfamily.org/") through which you can open GParted.  If on the normal livecd go to System->Administration->Partition Editor.
Here you can wipe the Ubuntu partition that you don't want (make sure it's the correct one!).
Then you can reboot the computer normally.  If you have been using the GRUB on your initial install, you will be able to boot correctly, after which you should edit /boot/grub/menu.lst so that it only has the existing operating systems (no more new Ubuntu and no more XP it sounds like)
```
gksudo gedit /boot/grub/menu.lst
```
If it turns out you were using GRUB on the newer installation (not likely since it still showed XP), you can reinstall GRUB by this guide: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)

---

### Post by fourthofjuly on 2008-02-09
thanks, but using the live CD & deleting the new Ubuntu install did not work as grub did not work... 

I found out the following solution myself that did the job...

Boot the newly installed Ubuntu (NEW) & become su... open /boot/grub/menu.lst (NEW) for editing... & delete all its contents...

go to the file system of the original Ubuntu (OLD, that i want to continue with)

...copy the contents of /boot/grub/menu.lst in this OLD install & paste them in the above emptied menu.lst file (in NEW)... save & reboot ...

there you are...!!! my OLD Ubuntu with all themes, wallpapers, display & sound settings is back...

thank you for your support...

Regards,

Devang.

---

