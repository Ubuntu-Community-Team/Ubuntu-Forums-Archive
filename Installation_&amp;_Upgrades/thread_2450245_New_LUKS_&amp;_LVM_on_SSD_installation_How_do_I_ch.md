---
title: "New LUKS &amp; LVM on SSD installation: How do I check discard (trim) is enabled?"
date: 2020-09-10
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2020-09-10
I freshly installed Ubuntu 20.04 using full-disk encryption on an SSD.

I have tried to check whether trim (discard) is enabled, as I understand that this is necessary to reduce wear on the SSD (so I've read — please correct me if I'm wrong).

The installation created three partitions.

[LIST=1]
[*]EFI System Partition, formatted as FAT32
[*]/boot, formatted as ext4
[*]Partition 3, LUKS encrypted.
[/LIST]
I can see that partition 3 uses discard, because it's mounted with that option in /etc/crypttab:
```
nvme0n1p3_crypt UUID=... none luks,discard
```
However, I find neither *trim* nor *discard* in /etc/fstab or /proc/mounts, so I wonder if it has been enabled on the first two partitions?

/etc/fstab contains the following two lines for those partitions:
```
UUID=... /boot      ext4 defaults   0 2
UUID=... /boot/efi  vfat umask=0077 0 1
```
/proc/mounts also says nothing about trim or discard:
```
/dev/nvme0n1p2 /boot ext4 rw,relatime 0 0
/dev/nvme0n1p1 /boot/efi vfat rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
```

I've struggled to make sense of what I've googled, so I need to know: Is everything set up correctly, or do I need to make a change for the health of my SSD?

Thanks

---

### Post by Dennis N on 2020-09-10
trim is controlled by systemd.
How to enable, check status (if enabled or not, and when it checks), and find out results of recent trim operations:
[https://ubuntuforums.org/showthread.php?t=2422973&p=13873318#post13873318](https://ubuntuforums.org/showthread.php?t=2422973&p=13873318#post13873318)

---

### Post by oldfred on 2020-09-10
I do not have LVM.

But discard is not recommended and noatime is recommended for SSD & relatime for HDD. Although some have used noatime on HDD also.

I mount tmpfs in fstab also.
# Reduce SSD wear
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

[https://wiki.archlinux.org/index.php/Solid_state_drive/NVMe#Discards](https://wiki.archlinux.org/index.php/Solid_state_drive/NVMe#Discards)
> Discards are disabled by default on typical setups that use [ext4]("https://wiki.archlinux.org/index.php/Ext4") and [LVM]("https://wiki.archlinux.org/index.php/LVM"), but other filesystems might need discards to be disabled explicitly. 



---

### Post by Paddy Landau on 2020-09-10
> **Dennis N said:**
> trim is controlled by systemd.
How to enable, check status (if enabled or not, and when it checks), and find out results of recent trim operations:
[https://ubuntuforums.org/showthread.php?t=2422973&p=13873318#post13873318](https://ubuntuforums.org/showthread.php?t=2422973&p=13873318#post13873318)
Thank you, Dennis. I receive results with a slightly different format from the link shown. I include only the relevant lines below:
```
$ journalctl --since=yesterday --grep=fstrim --case-sensitive
Sep 09 15:33:20 Fiamma systemd[1]: fstrim.timer: Succeeded.
Sep 09 15:53:50 Fiamma systemd[1]: fstrim.timer: Succeeded.
Sep 10 12:42:06 Fiamma systemd[1]: fstrim.timer: Succeeded.
Sep 10 16:04:55 Fiamma systemd[1]: fstrim.timer: Succeeded.
```
Thus, it seems, trim is enabled and working.
> **oldfred said:**
> …  discard is not recommended and noatime is recommended for SSD & relatime for HDD.
Thanks, oldfred. On reading your response and googling around a bit, I realise now that trim and discard are different (I had thought that they were synonyms).

It seems that trim (but not continuous trim) is recommended for NVMe, whereas discard is unwise (I can't find a definitive confirmation of this, but there seems to be quite a bit of supporting commentary, including from Intel itself).

So, my questions need to be revised.

**Trim and discard:**

[LIST]
[*]Periodic (not continuous) trim is enabled for all partitions (as per @Dennis N above).
[*]Partitions 1 and 2 seem to be correct by not using discard.
[*]Partition 3 seems to be incorrect, using discard. Therefore, I should remove "discard" from /etc/crypttab.
[/LIST]
Do you concur?

Am I correct that the periodic trim will correctly trim partition 3 even though it's encrypted?

**noatime vs relatime:**

The use of noatime and relatime on an SSD seems a [little contentious]("https://superuser.com/q/1156868/227686"). I have a couple of scripts and apps that use inotifywait or similar, so I think that in my case, it's best to keep relatime.

Thanks again

---

### Post by oldfred on 2020-09-10
From this, you then may be one that does need relatime:
man mount
>        relatime
              Update  inode  access  times  relative to modify or change time.  Access time is only updated if the
              previous access time was earlier than the current modify or change time.  (Similar to  noatime,  but
              it doesn't break mutt or other applications that need to know if a file has been read since the last
              time it was modified.)


I used to have a link to a google site with info on SSDs. That discussed many settings, but link is now not working. Arch tends to also have good documentation  on just about any subject.

Because trim is run, then old deleted data is gone from SSD. With HDD that info would stay until overwritten. Or some of the methods to recover data will not work with SSDs and good backups even more essential. And if encrypted, vital.

---

### Post by Paddy Landau on 2020-09-11
> **oldfred said:**
> &#8230; good backups even more essential. And if encrypted, vital.
Thank you for all that, oldfred. For many years, I have kept both online and offline encrypted backups, and I regularly test the restore process, so that's all in order!

---

