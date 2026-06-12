---
title: "Upgraded Edgy to Feisty Now Won't Mount my mdadm RAID disk (root partition)"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by unperson on 2007-09-11
When I installed edgy, I went through great pains (described in [_an earlier post_]("http://ubuntuforums.org/showthread.php?t=343823")) to set it up to use a software RAID0 (using mdadm) for the / and /home paritions.  After resolving the initial install problems, this has worked great for months.  The other day I used the upgrade tool to upgrade to Feisty.   After rebooting it doesn't seem to be able to mount the RAID drive that contains my / partition.  It was working fine before the upgrade.  I'll go on to give some more detais.

After I rebooted, the splash screen came up but the progress bar didn't moved.  After a few minutes the splash screen went  away and it brought up a BusyBox shell with a prompt reading (initramfs).  When I booted in recovery mode, I found that the last message is about starting USB, then the system appears to freeze for a few minutes  after which I get the initramfs prompt and the following message:

```
 
check root= bootarg cat /proc/cmdline
or missing modules,  devices /proc/modules ls /dev
ALERT! /dev/md0 does not exist.  Dropping to shell!
```

The way my system has been setup is that the  / partition on /dev/md0 (which was made from /dev/sda3 and /dev/sdb3) and my home partition on /dev/md1 (made from /dev/sda5 and /dev/sdb5).  The boot options in GRUB show root=/dev/md0 as I'd expect, so presumably it can't mount that for some reason.

Looking around in this BusyBox shell there are no /dev/md*  devices.  I also looked for /proc/mdstat but no such file exists.  The file /etc/mdadm/mdadm.conf reads as follows:

```

DEVICE partitions
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=...
ARRAY /dev/md2 level=raid0 num-devices=2 UUID=...
```

where a the usual hex strings follow the UUID=, and these UUIDs appear to match those output if I run

```

mdadm --examine --scan
```

I tried running /scripts/local-top/mdadm which gives the output:

```

Begin: Loading MD modules...
Done.
./scripts/local-top/mdadm:./scripts/local-top/mdadm: 72: panic: parameter not set
```

and still no /dev/md* devices exist, nor does /proc/mdstat.  Running 

```

mdadm --assemble --scan
```

gives the output

```

mdadm: error opening /dev/md1: No such file or directory
mdadm: error opening /dev/md2: No such file or directory
```

Booting with older (pre-upgrade) kernels selected from the GRUB menu has the same result, the boot process appears to freeze for a few minutes and then you get the initramfs prompt.

At a loss for what else to do, I also tried changing the boot parameter root=/dev/md0 to root=/dev/md1, since all the info available in busybox seemed to show the two RAID devices as /dev/md1 and /dev/md2.  However, with root=/dev/md1 I still get the same result (except now the error when you're dropped into busybox says that /dev/md1 doesn't exist).

I was able to put in a Kubuntu Feisty LiveCD and boot from that.  I did apt-get install mdadm.  In the process it detected and configured the two RAID devices as /dev/md1 and /dev/md2, and I mounted them with no trouble.  So it seems that the RAID is still in tact; it just apparently can't  be mounted during boot of the Ubuntu OS on the hard drive for some reason.

---

### Post by unperson on 2007-09-13
No further progress with this issue yet.  If it's of help, here's my mdadm.conf from that / partition (mounted with the kubuntu live CD):

```

DEVICE partitions
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=8f70f6b8:9d592f92:c1f52857:531571d4
ARRAY /dev/md2 level=raid0 num-devices=2 UUID=0dfbcbc5:fb260eb3:0965b7df:7ab815ba
DEVICE partitions
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=8f70f6b8:9d592f92:c1f52857:531571d4
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=0dfbcbc5:fb260eb3:0965b7df:7ab815ba
MAILADDR root

```

Now, that looks a bit screwy to me.  It looks like there are a redundant and conflicting set of entries.  I presume that before the system was only using one set, which I guess was the latter one.  In any case it was working fine before the update.  I can't see that this explains my problem, though, because as I said when I try to boot after the update and it kicks me out to busybox, the mdadm.conf there looks fine to me (as described above).  Any ideas?

---

### Post by psusi on 2007-09-13
Yes, it looks like your mdadm.conf is messed up with a duplicate entry.  Get rid of the first half of it so you only have the md0 and md1 entries, not md1 and md2.  

I suggest you do this by booting the livecd, mounting the / partition, chrooting into it, edit mdadm.conf, then run update-initramfs before rebooting.

---

### Post by unperson on 2007-09-13
Thanks psusi, that's got it!  Just in case anyone else can use the information, I'll detail what I did below.  I do have one question, though, which is at the end of this post.

I booted with the kubuntu Feisty live CD, and did 'apt-get install mdadm' so I could mount my / RAID partition.  After mounting the partition at /mnt/raiddisk, I did 'sudo chroot /mnt/raiddisk' saved a backup of /etc/mdadm/mdadm.conf (in the chrooted environment) and edited it to read simply

```

ARRAY /dev/md0 level=raid0 num-devices=2 UUID=8f70f6b8:9d592f92:c1f52857:531571d4
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=0dfbcbc5:fb260eb3:0965b7df:7ab815ba
MAILADDR root

```

I then opened a non-chrooted shell and mounted my boot partition to /mnt/raiddisk/boot.  Back in the chrooted shell I then ran

```

update-initramfs -c -v -k 2.6.20-16-generic

```

I found that it was giving a warning about not using the mdadm.conf file because it had not been checked since the update of mdadm.  After reading /usr/share/doc/mdadm/README.upgrading-2.5.3.gz, I ran 

```

rm -f /var/lib/mdadm/CONF-UNCHECKED

```

to tell the system I'd check the file, then I re-ran update-initramfs as above.  I then rebooted and the system booted fine!

The only question now is whether I should create a new mdadm.conf file and re-arrange things so that the two RAID devices are /dev/md1 and /dev/md2 (rather than /dev/md0 and /dev/md1 as they are now).  It seems like the info actually on the RAID has them as /dev/md1 and /dev/md2.  For example 'sudo mdadm --examine --scan' gives the output

```

ARRAY /dev/md1 level=raid0 num-devices=2 UUID=8f70f6b8:9d592f92:c1f52857:531571d4
ARRAY /dev/md2 level=raid0 num-devices=2 UUID=0dfbcbc5:fb260eb3:0965b7df:7ab815ba

```

and running 'sudo /usr/share/mdadm/mkconf' gives

```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=8f70f6b8:9d592f92:c1f52857:531571d4
ARRAY /dev/md2 level=raid0 num-devices=2 UUID=0dfbcbc5:fb260eb3:0965b7df:7ab815ba

```

So what I'm considering is replacing my current mdadm.conf with the the output of mkconf, changing the menu.lst to reflect that / would now be on /dev/md1 and then updating initramfs.  Good idea or bad idea?  Is there anything else I'd have to change?  My /etc/fstab already refers to disks by UUID not device name, so that's not an issue.

---

### Post by psusi on 2007-09-13
Normally the first raid device is md0.  It sounds like when you were originally messing around getting the system up, you had some other md0 which you later removed, but not before creating md1 and md2.  You then manually built your mdadm.conf to make them md0 and md1, but the disks themselves still indicate that they are supposed to be md1 and md2 still, so when you upgraded, it tried to rebuild the conf file using that information, and tried to merge it with your old information, causing the conflict.

---

### Post by unperson on 2007-09-13
> **psusi said:**
> Normally the first raid device is md0.  It sounds like when you were originally messing around getting the system up, you had some other md0 which you later removed, but not before creating md1 and md2..

Well, I don't remember there ever being a 3rd RAID partition, but otherwise that explanation seems to make sense.  There was some weirdness with the installer and locations of the RAID disks, which I talked about here

[http://ubuntuforums.org/showthread.php?t=343823]("http://ubuntuforums.org/showthread.php?t=343823")

Anyway, if the standard is for the first RAID disk to have the location /dev/md0, is there a way for me to change the info on the RAID (in the MD superblock, I guess) so that it reflects the device names I'd like (rather than md1 and md2) so that everything is consistent?  If I did that then I could presumably just use the mdadm.conf output by mkconf.

---

### Post by psusi on 2007-09-13
There SHOULD be a way to do that yes, but looking at the mdadm man page, I can't figure it out.

---

### Post by unperson on 2007-09-13
Ok.  Well, thanks for all your help!  That part I can pursue on my own without too much difficulty.  The main thing is that now I have a working system again.

---

