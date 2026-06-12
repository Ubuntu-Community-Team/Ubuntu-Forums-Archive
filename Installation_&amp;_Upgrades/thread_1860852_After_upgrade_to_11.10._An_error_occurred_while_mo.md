---
title: "After upgrade to 11.10. An error occurred while mounting / root filesystem"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by Gec1 on 2011-10-15
Guys,

I upgraded my os to 11.10 this morning but the beast won't boot. I get an error message saying

"An error occurred while mounting /" and I can Skip it (which of course doesnt make sense), or Manually fix it.

I tried the latter and see a message "Root filesystem check failed" but when I do fsck on a partition that holds root filesystem, it says it's fine

I cannot find any hint in dmesg exept of an information:

```
init: mountall main process (xxx) terminated with status 3
```What is this status 3? Why fsck on the fs works but when it boots it complains it cannot check it?

What I did so far, was playing with /etc/fstab - I thought it's due to my non-standard configuration - I have /tmp and /var/tmp  in ram filesystem and /var/log on a completely separate disk. But I',m not sure... I double checked the fstab passno field, made sure my / is before any filesystem that depends on / structure (/mnt/* /var/tmp)

I'm completely stuck. How can I investigate this further? Where to look for clues?

Here's an excerpt of my /etc/fstab

```

proc            /proc           proc    nodev,noexec,nosuid 0       0
none    /tmp    tmpfs   nodev,nosuid,noatime,size=1000M,mode=1777       0       0

UUID=0965ec25-xxxx-xxxx-xxxx-xxxxxxxxb9       /               ext4    defaults,noatime,nodiratime,data=writeback 0       1

none    /var/tmp    tmpfs   nodev,nosuid,noatime,size=1000M,mode=1777       0   0
#var log to a separate drive to lower writes to SSD
UUID=6a21aebc-yyyy-yyyy-yyyyyyye0 /var/log      ext2    defaults,noatime,nodiratime      0       2

# /home was on /dev/sda6 during installation
UUID=f1f8d401-xxxx-xxxx-xxxxxxxxxxd7 /home           ext4    defaults,noatime,nodiratime,data=writeback        0       2

```Thanks for help in advance!

Gec1

---

### Post by Gec1 on 2011-10-23
Just in case someone else bumps into the thread. The problem was that the root partition had data=writeback option in fstab (even though the journaling was on on that partition). After removing the option the system started fine.
When investigating the problem, the system complained about changing data mode on already mounted partition during booting (the message was displayed when booting in recovery kernel, so I didn't see it the first time). I'm not sure why root partition needs to have special treatment when it comes to journaling mode.

Hope it helped anyone having the same problem,

Gec1

---

### Post by rarendes on 2011-12-01
I encountered the same problem.

Obviously, with Ubuntu it is not easily possible to change the root-filesystem to data=writeback.

The initial mount, done in some ramdisk-mountscript, is data=ordered (default value).

The root filesystem is then, some time later, remounted rw with the parameters in the actual /etc/fstab file. For data= this fails, because this parameter can't be changed during a remount.

I thought that running update-initramfs -u helps because it regenerates the initial ramdisk, but it does not check for this parameter. 

I'll do some further investigation later.


EDIT: I unpacked the initial ramdrive and checked the init-script there. I found that it takes the linux kernel parameter "rootflags" and passes its parameter to the initial mount.

That means, that this should be a (upgrade-safe) solution for Ubuntu:

in /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="splash rootflags=data=writeback"

run sudo update-grub(2) afterwards and reboot. 
After reboot, my root file system was data=writeback. 

For this to work reliable, please remove any data= parameter from the root filesystem in /etc/fstab.

I hope this helps.

---

### Post by BluePanther on 2012-06-06
Thanks, this really helped me with same problem.

As a hint: I believe my mounting error started from playing with Mountmanager...

---

