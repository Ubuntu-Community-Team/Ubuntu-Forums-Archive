---
title: "My Lucid 10.04 seems to be running original GRUB"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by sixstringtiger on 2010-06-05
Hi there,
I'm running 10.04. Been doing consecutive upgrades since 8.04. When I upgraded from 9.10 to 10.04 the new kernel (32-22) was hanging up on boot. Would hang on a blank screen.

So I determined 31-21 was the most recent kernel that booted successfully (albeit with several error messages). I wanted to edit my Grub boot menu to basically comment out the 2 newer kernels (that don't work) and make 31-21 default.

Here's the strange part. I know we've been on GRUB 2 since Karmic. However, for some reason, I still have a live, working /boot/grub/menu.lst! Even stranger, I have none of the new files, such as:
 /boot/grub/grub.cnf
/etc/default/grub

I've tried running update-grub, and here is the output:
> Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-22-generic
Found kernel: /boot/vmlinuz-2.6.32-21-generic
Found kernel: /boot/vmlinuz-2.6.31-21-generic
Found kernel: /boot/vmlinuz-2.6.31-20-generic
Found kernel: /boot/vmlinuz-2.6.31-19-generic
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-10-rt
Found kernel: /boot/vmlinuz-2.6.31-9-rt
Found kernel: /boot/vmlinuz-2.6.28-17-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.28-3-rt
Found kernel: /boot/vmlinuz-2.6.27-14-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... doneIs it possible I've somehow reverted back to the original GRUB? My Update Manager has downloaded at least 2 updates for kernel 32-22 in the last few days but they aren't being implemented. I still have a menu.lst file with 32-22 and 32-21 commented out (making 31-21 the top of the list).

Thanks!

---

### Post by sixstringtiger on 2010-06-05
Update:

The output of grub-install -v:

grub-install (GNU GRUB 0.97)

Yup, GRUB legacy. So I'm not sure how I "missed" the update to GRUB 2, but I'm assuming I should upgrade GRUB manually at this point. Any objections? Is there anything I should look out for since GRUB 2 was supposed to be in effect on my computer 2 upgrades ago?

---

### Post by kansasnoob on 2010-06-05
Routine distribution upgrades keep the same version of grub. If legacy grub is working OK I'd leave it be :)

Should you desire to change to grub 2 you should first be familiar with it:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You should also understand drive and partition designations in Ubuntu:

Drives are designated as /dev/sda, /dev/sdb, /dev/sdc, etc. the last letter indicates the drive number, eg:
/dev/sda = drive #1
/dev/sdb = drive #2
/dev/sdc = drive #3

Partititions are designated with a number following the drive designations, eg:
/dev/sda1 = drive #1/partition #1
/dev/sda2 = drive #1/partition #2
/dev/sdb1 = drive #2/partition #1

And package names:

grub = legacy grub
grub-pc = grub 2
grub-common is shared by both legacy grub and grub 2
os-prober is particularly necessary for the proper function of grub 2

I see you already know about "grub-install -v" but other useful commands to determine package versions:

```
grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

Also since you've been upgrading you may not have a 9.10 or newer Live CD so this may be of interest:

[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

But changing from legacy grub to grub 2 should be as simple as:

```
sudo mv /boot/grub /boot/grub_legacy
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub grub-common
```

```
sudo apt-get install grub-pc
```

```
sudo update-grub
```

```
sudo grub-install /dev/sd**[COLOR="Red"]X[/COLOR]**
```

Of course the X must be replaced with the proper drive designation. It's almost never a good idea to install grub to a partition rather than a drives MBR!

---

### Post by sixstringtiger on 2010-06-08
Sorry for the delay in responding -- took me a few days to get back to the computer.

Thanks very much for the help, kansasnoob! I didn't realize Grub would remain the legacy version since I'm doing the automated upgrades. I appreciate all the extra info about upgrading to Grub 2 as well.

Unfortunately Lucid is hanging on the 2 newest kernel versions so I'm stuck with 31-21 for now. It boots fine despite several error messages in the process.

Thanks again!

---

