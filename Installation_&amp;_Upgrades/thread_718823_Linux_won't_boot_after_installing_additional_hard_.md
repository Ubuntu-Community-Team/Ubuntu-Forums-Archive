---
title: "Linux won't boot after installing additional hard drive"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by nookkin on 2008-03-08
Hello

I have Kubuntu 6.06 installed on an external USB hard drive, and it used to work perfectly. I have an internal drive running XP as well. Here is my configuration:
160gb internal drive:
Partition 1 (/dev/sda1): Windows XP MCE
Partition 2 (/dev/sda2): HP recovery partition
80gb external USB drive:
Partition 1 (/dev/sdb1): File backup (NTFS)
Partition 2 (/dev/sdb2): Kubuntu boot partition
Partition 3 (/dev/sdb3): Second ext3 partition (not used)
Partition 4 (/dev/sdb4): Home
Partition 5 (/dev/sdb5): Swap

I recently got a new 500gb internal drive. Now, Linux refuses to boot. It starts loading but before it gets to the splash screen it displays messages like "cannot mount proc to /proc: no such directory". Then I get a BusyBox shell.

I used Ex2FS within Windows to change the boot partition in menu.lst from /dev/sdb2 to /dev/sdc2. Now it boots normaly, up to the login prompt. However when I try to log in it says that it can't load some critical files. Even a failsafe session does not work.

The problem here is the fact that upon installing the 500gb drive, the identifier of the drive Linux is on changed (sdb became sdc). I cannot change this in the BIOS, since there is no option for it (boot device priority doesn't help). Plus internal drives take precedence over external.

How can I get Linux to boot again? I basically need to tell Linux that it is now installed on sdc and not sdb.

---

### Post by defmomo on 2008-03-10
Can we assume that /dev/sdb2, or your Kubuntu boot partition is also the root partition?


Also,  on another matter, that is a pretty old  version of the distro, I suggest you upgrade to 7.10 as soon as possible, it is so far the *best ubuntu distro.


*The best as in features

---

### Post by nookkin on 2008-03-10
Yes, /dev/sdb2 is the root partition (/ in linux). I just need to somehow tell Linux that the drive configuration has changed. (You could say that half of it thinks it's installed on sdb and the other half thinks its installed on sdc)

I guess I might as well just reformat and install Kubuntu 7.10. But a reinstall for something as simple as this... what if I get a 3rd drive or I get rid of one? Then I have to reinstall again? I'm not looking forward to that! :(

---

### Post by froy02 on 2008-03-10
You might want to check your fstab file to verify that the UUID and /dev/sdc matched.  The fstab file might still be referring to your Kubuntu installation as sdb.

---

### Post by nookkin on 2008-03-11
Thanks froy02, I edited my fstab file (changed all occurences of sdb to sdc) and it worked. I'm in Linux right now :)

---

