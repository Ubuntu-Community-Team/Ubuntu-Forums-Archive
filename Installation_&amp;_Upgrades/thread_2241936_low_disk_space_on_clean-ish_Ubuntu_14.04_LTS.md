---
title: "low disk space on clean-ish Ubuntu 14.04 LTS"
date: 2014-08-29
forum: Installation &amp; Upgrades
---

### Post by janda29 on 2014-08-29
Hi. I got the low disk space error message stopping me installing updates and went through Grub menu to get more space but cannot clear more now.  Am not able to manually delete files of old updates as 'am not the owner'.  Anyone able to help.  Ideally want to create a bigger boot folder but have the same problem.

How do I become 'root'?

---

### Post by ajgreeny on 2014-08-29
Do you have a separate /boot partition, which is sometimes the reason for your problem?

I don't understand what you are saying about the grub menu to get more space; that is not what you will need to do, but it would help to know in detail what you have already done in proper detail.

Can you also show us the output of the terminal commands ```
sudo fdisk -l
mount
``` which will help us sort out what is going on.

---

### Post by varunendra on 2014-08-29
Probably a bug as mentioned in this post ? : [http://ubuntuforums.org/showthread.php?t=2240240&p=13102512#post13102512](http://ubuntuforums.org/showthread.php?t=2240240&p=13102512#post13102512)

---

### Post by TheFu on 2014-08-29
```
df -i
df -h
```
output please.  I wrote a script a few yrs ago that builds the command to purge old kernels. It doesn't actually run the script - just creates it, so we can copy/paste into a terminal.  Has been working here for years.

[http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt) explains.

Would be really nice if there were a system-wide setting for how many old kernels to retain, so that kernel updates would delete any older kernels automatically.

---

### Post by grahammechanical on 2014-08-29
The recovery mode has an option called Clean that is a script that runs apt-get clean and apt-get autoremove.

You will find the script at /lib/recovery-mode/options/

Regards

---

### Post by TheFu on 2014-08-29
> **grahammechanical said:**
> 
 /lib/recovery-mode/options/clean

Doesn't do what I thought it should here.
Current kernel: linux-image-3.13.0-34-generic
So, I'd like to retain 34 and 32 kernels - the last 2 on the system.

The "clean" script: 
```
The following packages will be REMOVED:
  linux-headers-3.13.0-29 linux-headers-3.13.0-29-generic
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-image-3.13.0-29-generic linux-image-3.13.0-32-generic
  linux-image-extra-3.13.0-29-generic linux-image-extra-3.13.0-32-generic
```

My "kernel-cleanup.sh" script makes this output:
```
/usr/bin/sudo /usr/bin/aptitude purge linux-image-3.13.0-29-generic linux-image-3.13.0-30-generic linux-image-3.13.0-32-generic
/usr/bin/sudo /usr/bin/aptitude autoclean
```

So ... why does the "clean" ignore 3.13.0-30?

---

