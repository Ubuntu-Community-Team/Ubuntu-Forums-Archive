---
title: "Ubuntu 16 won't boot"
date: 2017-07-31
forum: Installation &amp; Upgrades
---

### Post by aquel on 2017-07-31
Hello all, 

I have an hosted dedicated server at Online.net. Today at 2PM, the server crashed and doesn't boot since (no ping, no ssh). It took me some time to figure out why but I think I know now: 4 days ago, I have upgraded my distribution (apt upgrade) but the upgrade failed on some linux headers packages, probably a Kernel upgrade ([COLOR=#000000][FONT=&quot]No space left on device[/FONT][/COLOR] on /boot as I can remember). I was very surprised by this error and I told to myself that I had to check this out but then I forgot and 4 days later, the server rebooted for some reason and it is now stuck. 

As it is hosted, I have no physical access the server. I can boot on the rescue mode on a Ubuntu 16 live cd, I can mount my partitions and access all my data. So the hard drive is fine. 
How can I fix the boot ? Can I revert the failed upgrade ? 

Here is what I have into my /boot partition
```

*-rw-r--r-- 1 root root  1246246 avril 20 14:02 abi-4.4.0-75-generic*
*-rw-r--r-- 1 root root  1246313 avril 26 12:30 abi-4.4.0-77-generic*
*-rw-r--r-- 1 root root  1246312 avril 27 20:24 abi-4.4.0-78-generic*
*-rw-r--r-- 1 root root  1246670 juil. 18 17:00 abi-4.4.0-87-generic*
*-rw-r--r-- 1 root root   190214 avril 20 14:02 config-4.4.0-75-generic*
*-rw-r--r-- 1 root root   190355 avril 26 12:30 config-4.4.0-77-generic*
*-rw-r--r-- 1 root root   190355 avril 27 20:24 config-4.4.0-78-generic*
*-rw-r--r-- 1 root root   190356 juil. 18 17:00 config-4.4.0-87-generic*
*drwxr-xr-x 5 root root     1024 juil. 27 11:33 grub/*
*-rw-r--r-- 1 root root 34083124 juin   2 15:15 initrd.img-4.4.0-75-generic*
*-rw-r--r-- 1 root root 34083243 juin   2 15:15 initrd.img-4.4.0-77-generic*
*-rw-r--r-- 1 root root 34086183 juin   2 15:16 initrd.img-4.4.0-78-generic*
*drwx------ 2 root root    12288 avril 28 19:53 lost+found/*
*-rw------- 1 root root  3883390 avril 20 14:02 System.map-4.4.0-75-generic*
*-rw------- 1 root root  3883390 avril 26 12:30 System.map-4.4.0-77-generic*
*-rw------- 1 root root  3882872 avril 27 20:24 System.map-4.4.0-78-generic*
*-rw------- 1 root root  3884173 juil. 18 17:00 System.map-4.4.0-87-generic*
*-rw------- 1 root root  7081872 avril 20 14:02 vmlinuz-4.4.0-75-generic*
*-rw------- 1 root root  7081808 avril 26 12:30 vmlinuz-4.4.0-77-generic*
*-rw------- 1 root root  7089552 avril 27 20:24 vmlinuz-4.4.0-78-generic*
*-rw------- 1 root root  7095888 juil. 18 17:00 vmlinuz-4.4.0-87-generic*
```





Thanks a lot, 

Axel

---

### Post by aquel on 2017-07-31
Trying to fix my issue. I edited the grub.cfg and replaced all occurrences of 4.4.0-87 by 4.4.0-78 in order to rollback kernel but it doesn't seem to boot either. 
Any idea? 
Thanks

Axel

---

### Post by vocx on 2017-07-31
> **aquel said:**
> Hello all, 

I have an hosted dedicated server at Online.net. Today at 2PM, the server crashed and doesn't boot since (no ping, no ssh). It took me some time to figure out why but I think I know now: 4 days ago, I have upgraded my distribution (apt upgrade) but the upgrade failed on some linux headers packages, probably a Kernel upgrade **(insufficient disk space on /boot as I can remember)**. I was very surprised by this error and I told to myself that I had to check this out but then I forgot and 4 days later, the server rebooted for some reason and it is now stuck. 

As it is hosted, I have no physical access the server. I can boot on the rescue mode on a Ubuntu 16 live cd, I can mount my partitions and access all my data. So the hard drive is fine. 
How can I fix the boot ? Can I revert the failed upgrade ? 
...
Thanks a lot, 

Axel
Many people in this forum report having "/boot" full as they create a small, say, 200 MB boot partition. After three or four kernel updates it's full, and they start getting errors. There is no reason to keep a "/boot" partition if you are using your system as a home computer, like most users in this forum do. I don't use encryption or fancy stuff, so I wonder if your specific server use requires having this "/boot" partition, as stated in some answers here [https://unix.stackexchange.com/questions/256/is-it-good-to-make-a-separate-partition-for-boot](https://unix.stackexchange.com/questions/256/is-it-good-to-make-a-separate-partition-for-boot)
Apparently in 2010, a Grub bootloader couldn't boot a partition using ext4, and LVM, but now it can obviously. So, the need of having a separate "/boot" is disappearing.

In any case, the solution would be to remove old kernels so that they don't take all the space inside "/boot".

Boot into recovery mode, mount your partition, "change root" into it, and remove at least one old kernel to get space. Then you can see if you can boot and continue cleaning up your system.
```

sudo mount /dev/sda1 /mnt
sudo mount --bind /boot /mnt/boot
sudo chroot /mnt
sudo apt purge linux-image-4.4.0-75-generic
sudo apt purge linux-headers-4.4.0-75-generic

```

A more brute force approach is to simply delete the old kernel files to make space. Obviously this will not remove the package cleanly, but you first need to be able to boot, afterwards you can remove the package properly with "apt".
```

sudo mount /dev/sda1 /mnt
sudo rm /mnt/boot/abi-4.4.0-75-generic
sudo rm /mnt/boot/initrd.img-4.4.0-75-generic
sudo rm /mnt/boot/vmlinuz-4.4.0-75-generic

```

Of course, you need at least one kernel to boot your system. I would delete "4.4.0-75", and "4.4.0-77", and leave "4.4.0-78" and "4.4.0-87". Presumably your last working kernel was "4.4.0-78", so you should be able to boot using this one. And probably "4.4.0-87" is the kernel that didn't finish updating properly. You may not be able to boot with this one, so you may want to remove it as well. Later you can reinstall it properly.

If you get to boot "4.4.0-78" normally, then I would update and upgrade to get the new kernel correctly.
```

# to remove old packages and kernels not needed anymore
sudo apt autoremove

# to correctly update and upgrade the rest of the packages
sudo apt update
sudo apt upgrade

```

---

### Post by aquel on 2017-07-31
@voxc thank you for your very long and complete answer. You are absolutely right. The boot partition was set by Online.net when installing the distribution, I didn't not change the value but I certainly will next time... 
I was executing the process when you were writing your reply and it worked like a charm. Thank you again for this. 

Kind regards

---

