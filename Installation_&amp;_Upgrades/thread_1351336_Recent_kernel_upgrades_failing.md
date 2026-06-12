---
title: "Recent kernel upgrades failing"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by east2idaho on 2009-12-10
I was happily running with the 2.6.31-15-generic kernel when the 2.6.31-16-generic upgrade was pushed out.  Letting the update manager install 2.6.31-16-generic resulted in a failure to boot.  When I tried to tell grub to boot from the 2.6.31-15-generic kernel which had been working, it also failed.  Fortunately, telling grub to use the 2.6.31-14-generic kernel gave me a successful boot.  

I let the update manager install today's (12/10/2009) 2.6.31-16-generic kernel update, and I still am experiencing a boot failure under every installed kernel after the 2.6.31-14-generic kernel.

The failure I see is:
```
Boot from (hd1,0) ext3 <UUID> udevadm settle - timeout of 180 seconds reached, the event queue contains:
/sys/devices/pci0000:00/0000:00:08/host0/target0:0:/0:0:0:0 /block/sda(2313)
mount: mounting /dev/disk/by-uuid/<UUID> on /root failed: Invalid argument.
```

My interpretation of the error message is that the kernel loaded by the initrd created by the new kernel is not seeing my hard disk.  I checked the size of the initrd files in /boot to verify that their sizes looked reasonable, and they did.

```
/boot$ ls -l|grep initrd
-rw-r--r-- 1 root root 7003259 2009-11-02 13:45 initrd.img-2.6.28-16-generic
-rw-r--r-- 1 root root 7644643 2009-11-21 16:26 initrd.img-2.6.31-14-generic
-rw-r--r-- 1 root root 7893141 2009-12-02 11:07 initrd.img-2.6.31-15-generic
-rw-r--r-- 1 root root 7893322 2009-12-10 10:00 initrd.img-2.6.31-16-generic
```

Here are the relevant sections of grub's menu.lst showing the sections for the working and non-working boot options, confirming that the correct UUID is being passed:

```
title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		b8b6be22-bcb7-4159-a0ef-5e712ef1dfaa
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=b8b6be22-bcb7-4159-a0ef-5e712ef1dfaa ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		b8b6be22-bcb7-4159-a0ef-5e712ef1dfaa
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=b8b6be22-bcb7-4159-a0ef-5e712ef1dfaa ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		b8b6be22-bcb7-4159-a0ef-5e712ef1dfaa
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=b8b6be22-bcb7-4159-a0ef-5e712ef1dfaa ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		b8b6be22-bcb7-4159-a0ef-5e712ef1dfaa
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=b8b6be22-bcb7-4159-a0ef-5e712ef1dfaa ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		b8b6be22-bcb7-4159-a0ef-5e712ef1dfaa
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=b8b6be22-bcb7-4159-a0ef-5e712ef1dfaa ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		b8b6be22-bcb7-4159-a0ef-5e712ef1dfaa
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=b8b6be22-bcb7-4159-a0ef-5e712ef1dfaa ro  single
initrd		/boot/initrd.img-2.6.31-14-generic
```

Thanks in advance for any suggestions on how to proceed.

---

### Post by Yvan300 on 2009-12-10
I have the same problem as you, but i just ended up using startup manager to use the old kernel by default.

---

### Post by east2idaho on 2009-12-10
Yvan300:

Thanks for the pointer about startup-manager.  It is a nice alternative to hand editing the grub files that I had not tried before.

I am still looking for someone who can confirm that I am on the right track about what I think has gone wrong, and anyone who can make suggestions about how to go about creating a working initrd.img file, if that is what is really wrong.

---

### Post by sfryer on 2009-12-10
same problem here. using netbook-remix via wubi install. 31-14-generic works fine. anything newer just flips me right back to the grub menu.

---

### Post by ledenjes on 2009-12-11
I have to exact same problem as prescribed by **east2idaho**. Booting into kernel 2.6.31-16 ends up in a boot error. Booting into kernel 2.6.31-14 works just fine. Perhaps it's related to an incorrect configuration prior to compiling this new kernel. In that case, the Ubuntu guys need to recompile the kernel, this time with the correct settings/configuration.

---

### Post by east2idaho on 2009-12-13
Have I posted this on the wrong forum, or does my question about how I should go about trying to do my own repair make me sound too naive for anyone to want to risk giving me suggestions that could end up leading me to do something that would hose my system?

It looks like my problem is also being seen by other users.  Is there an appropriate place to offer information about my system hardware and configuration files to help the folks supporting the Ubuntu upgrades to try to sleuth out what is going wrong with their kernel upgrade installations?

---

### Post by shazzer on 2009-12-13
Cant even get a boot form the earliest kernel. Help I need to sort this problem. I can get to a prompt in recovery which is (initramfs) where do I go from here to fix the broken kernel. Instructions needed from this prompt. 

Can I run live from the USB to access the things I need first? Not even sure if it will work but until I get things fixed. 

Anyone who is reading, please reply asap as I will lose another days work from a faulty Ubuntu upgrade and this isnt the first time. 

Thanks

---

### Post by shnurui on 2009-12-13
2.6.31-16 to 2.6.31-17 with my athlonXP 1.5 and an nvidia gforce 6200 is doing the fail thing.

It'll boot to TTY and refuse to load X.  I've got a bunch of IO errors and I'm not sure how to make it log the failure.

This instance was caused by my using a Non "Released" NEWEST POSSIBLE DRIVER for my Nvidia.

Reinstalling it allowed the newest kernel to up to X.

For the love of Pete, someone slap who ever decides what drivers get distro through the driver distro and get 190.x listed?

---

### Post by east2idaho on 2009-12-16
This problem could be related to bug 403408
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408")

---

### Post by east2idaho on 2010-01-07
A non-kernel patch that was pushed out by the Ubuntu Update Manager caused the update-initramfs tool to kick off during installation.  This caused my last remaining working kernel to also fail to boot, but with a new error message: "group descriptors corrupted".

When I tried to run fsck from the 9.10 Ubuntu install CD, I found that the 9.10 CD was unable to mount any partitions on either of my two hard drives.  The CD saw the sda and sdb devices, but had not created the sda1 or sdb1 device files as it booted.

However, the 9.04 Ubuntu install CD had no problem mounting the partitions on either of the drives, and pronounced the partitions clean when I did a fsck.  However, I still found myself unable to boot from these partitions.

I decided to back up and reinstall Ubuntu 9.10 from scratch, but I found that the partitioner tool on the 9.10 installation CD was unable to recognize that my drives existed.

My system's motherboard has a Promise Technology RAID bus controller which I had configured in the BIOS to treat the installed drives as discrete drives instead of as a RAID drive.  I had originally installed Ubuntu 9.04 which was perfectly happy respecting this BIOS configuration. When I later upgraded that installation to 9.10, the 9.10 upgrade had worked fine until I installed the later patches that Update Manager pushed out.  These patches have apparently caused the system to ignore my BIOS settings and insist on treating my drives as if they should be a RAID array resulting in a nonbootable system.  

I guessed that my problem with the Ubuntu 9.10 installation CD was a result of the same "feature", so I reconfigured the BIOS to treat the drives as a RAID array, and the Ubuntu 9.10 install succeeded.

After the install I let the Update Manager install all the latest patches, and again found that I had an unbootable system.

I reinstalled, but went into the advanced settings on the final screen of the install and told grub to use the first /dev/mapper choice for the boot sector location instead of my sda drive.  After letting the Update Manageer install all the latest patches, the system is bootable, but the boot process takes about 10 minutes.  Evidently there are a number of timeouts occurring as Linux tries to boot my hardware.

I booted up the latest Fedora installation CD, and found that it behaved similarly to the Ubuntu 9.10 CD.

So I am going to call this problem solved, but not entirely to my satisfaction, since I think I understand the problem but I do not see how to reliably fix the issue in the sense of setting up my system so that I can count on it surviving the next attack from the Update Manager.  It looks like the kernel developers are trying to improve their handling of RAID, but at this point their efforts have made my hardware only marginally usable under Linux.

---

### Post by east2idaho on 2010-01-29
Looks like this is related to bug 67299 which describes a problem with how grub trying to scan for possible raid configurations.

---

### Post by east2idaho on 2010-02-05
Getting closer to a real solution.  The kernel update pushed out today gave me a system that would not boot again, even after waiting for 10 minutes.

I had had a USB HDD mounted while the upgrade manager was doing its thing.  So I removed the USB drive from the system, booted from my 9.10 install CD (using the "boot from first hard drive" option), and invoked:
```
sudo dpkg-reconfigure linux-image-`uname -r`

```

When I rebooted (without the USB HDD connected, my system booted quickly for the first time since I saw this problem.

---

### Post by KPDXHAM on 2010-02-05
Re: Upgrade to 2.6.31-19-generic

My reboot went fine, although I was holding my breath as I watched it run through grub, then this new kernel, and then displayed my login.

So far, so good. ;)

---

