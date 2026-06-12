---
title: "Can't boot after failed update."
date: 2014-08-30
forum: Installation &amp; Upgrades
---

### Post by jsgarvin on 2014-08-30
I did a typical package update, after which there was a dialog that said some packages failed to update.  Then it asked to reboot.  Intending to click the "reboot later" button to try to investigate, I instead in a rush clicked the "reboot now" button.  :-(

Now the computer just gets past the bios spash screen and then goes to a blinking cursor and stays there.  No grub menu, or anything else.

I tried boot-repair from the live-CD and it said it was "successfull", and gave this url [http://paste.ubuntu.com/8188784/](http://paste.ubuntu.com/8188784/)  but upon reboot I get the same problem.

Next steps?

(FYI, I'm relatively experiend with linux and pretty well know my way around the terminal, apt, vim, etc, if that helps with shorter "to the point" questions/suggestions ;-)

---

### Post by TheFu on 2014-08-31
Boot off a liveCD.
Mount the partitions from the HDD(s).
Check the free storage on those partitions - 
* df -h
* df -i
If there isn't any more space on any of them, that is likely the issue.  I'm almost willing to bet you use LVM or encryption and /boot is full.  If that is the case, the /boot partition filled up while trying to rebuild the initrd file - which is catastrophic.  The default size created during installation for /boot is about 2G too small, IMHO.  There are a few other threads here about how to clean up /boot.

If storage isn't an issue - what do the log files show?
Can you boot the liveCD?

---

### Post by jsgarvin on 2014-08-31
Yup, /boot seems to be full (and yup, I'm using encryption).

I manually moved some of the older abi*, config*, initrd*, System.map*, and vmlinuz* files from /dev/sda2 (my /boot) to a backup folder on a different partition to make space in /boot (leaving the most recent 3 of each in place).  Then tried rebooting and still getting the same result.

All of the threads I can find regarding cleaning up the /boot partition seem to assume that the system is still bootable such as running `dpkg` and `apt-get remove` which I don't think is going to do anything for me running from the liveCD with my normal /boot partition mounted to /mnt.  (For instance, `sudo dpkg --list 'linux-image*'` lists what the liveCD has, not my regular system.)

Further suggestions on recovering my /boot?

---

### Post by jsgarvin on 2014-08-31
For reference, here's the current contets of my /dev/sda2...

```
total 114750
drwxr-xr-x 4 root root     3072 Aug 31 19:08 .
drwxr-xr-x 1 root root       80 Aug 31 18:23 ..
-rw-r--r-- 1 root root  1162712 Jul 15 04:29 abi-3.13.0-32-generic
-rw-r--r-- 1 root root  1162712 Aug 13 16:45 abi-3.13.0-34-generic
-rw-r--r-- 1 root root  1163858 Aug 15 02:56 abi-3.13.0-35-generic
-rw-r--r-- 1 root root   165611 Jul 15 04:29 config-3.13.0-32-generic
-rw-r--r-- 1 root root   165611 Aug 13 16:45 config-3.13.0-34-generic
-rw-r--r-- 1 root root   165652 Aug 15 02:56 config-3.13.0-35-generic
drwxr-xr-x 5 root root     1024 Aug 30 15:38 grub
-rw-r--r-- 1 root root 28467111 Jul 23 15:23 initrd.img-3.13.0-32-generic
-rw-r--r-- 1 root root 28469735 Aug 16 18:47 initrd.img-3.13.0-34-generic
-rw-r--r-- 1 root root 28470520 Aug 30 15:38 initrd.img-3.13.0-35-generic
drwx------ 2 root root    12288 May 21 23:31 lost+found
-rw-r--r-- 1 root root   176500 Mar 12 12:31 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12 12:31 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12 12:31 memtest86+_multiboot.bin
-rw------- 1 root root  3381262 Jul 15 04:29 System.map-3.13.0-32-generic
-rw------- 1 root root  3381262 Aug 13 16:45 System.map-3.13.0-34-generic
-rw------- 1 root root  3386444 Aug 15 02:56 System.map-3.13.0-35-generic
-rw------- 1 root root  5798112 Jul 15 04:29 vmlinuz-3.13.0-32-generic
-rw------- 1 root root  5797728 Aug 13 16:45 vmlinuz-3.13.0-34-generic
-rw------- 1 root root  5806368 Aug 15 02:56 vmlinuz-3.13.0-35-generic
```

---

### Post by jsgarvin on 2014-08-31
Well.... I tried following the instructions at [http://superuser.com/a/614347](http://superuser.com/a/614347) (with some minor modifications to mount the encrypted system partition).

When I get to step 6 though, I get...

```
root@ubuntu:/#  grub-install --recheck /dev/sda
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
```

---

### Post by jsgarvin on 2014-08-31
Realized I should try boot-repair again now that there's more space on /boot.... However, that still doesn't fix anything and gives the following notes.  [http://paste.ubuntu.com/8200542/](http://paste.ubuntu.com/8200542/)

This seems relevant...  Just not sure how a fix it.
```

Grub2 (v1.99-2.00) is installed in the MBR of /dev/sda and looks at sector 
    172674 of the same hard drive for core.img, but core.img can not be found 
    at this location.

```

---

### Post by TheFu on 2014-08-31
Wish I had an answer - encryption scares me enough to avoid it except on portable devices. On those, I don't keep anything important - I'm willing to wipe them daily, if necessary.  Of course, backups are a key thing too.

I'd cut my losses - assume everything is gone, repartition /boot to be 2G and deal with the other things as needed, reinstall with encryption again and restore all the programs/settings/data from the last backup.  That's just me. There might be some magical method to use chroot and get a new/old kernel into /boot, then be able to boot again - encryption puts a wrench into my lack-of-knowledge - sorry.

---

### Post by jsgarvin on 2014-09-01
Bummer.   Well, thanks for the help anyway.  At least I learned enough to hopefully keep it from happening again (keep /boot from filing up).  I swear that I recall years ago ubuntu or grub had a an option to set how many prior kernels to keep and automatically cleaned up the old ones.  What the heck happened to that feature?   Or was that from way back when I was using fedora?

---

