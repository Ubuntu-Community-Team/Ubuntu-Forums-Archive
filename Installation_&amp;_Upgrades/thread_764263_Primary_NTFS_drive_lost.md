---
title: "Primary NTFS drive lost"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by markmcc on 2008-04-23
I installed Hardy on my new Dell laptop yesterday using Wubi  (It's working really well, the only thing I needed to mess a little with was using ndiswrapper to get my Broadcom wireless to work)

However, I took down my first batch of updates - about 91 of them I think - today, and since I did the reboot it asked me to do I've lost my primary NTFS drive (called OS).

Is doesn't appear on the desktop as an icon or anywhere else (e.g. 'Places').  The other two NTFS partitions that Dell put on MEDIADIRECT and RECOVERY are still shown.

I'm sure updating caused this, but I'm confused as to what try to get it back.

Any ideas?  Anyone else got a similar issue after their first internet updating?

Cheers,
Mark.

---

### Post by dstew on 2008-04-24
Post the output of```
sudo fdisk -l
cat /etc/fstab
```Maybe the update changed something in fstab, and the disk is not mounting automatically like before.

---

### Post by amd-64 on 2008-04-24
If your NTFS is hibernated, linux will not mount it as read/write. 

I usually mount it read-only manually using 
```
sudo mount -o ro /dev/sda1 /media/sda1 
```
In my case sda1 is the NTFS drive and /media/sda1 is an empty folder to mount it in.

You could also delete the hibernation file to mount it read/write.

---

### Post by slick_nick on 2008-04-24
I have a similar problem.  I have an NTFS drive called "Storage" with a bunch of music, which I still haven't gotten around to formatting to ext3. Under 7.10 I would have to go into Computer and mount it with my sudo password each time I rebooted. I just upgraded to Hardy Heron, and the drive has completely disappeared. It's not in fstab or mtab.
Gparted sees it, at /dev/sdb1, and gives the following warning:

[I]The device /dev/sdb1 doesn't exist.
ntfsresize v1.1.3.1 (libntfs 9:0:0)
ERROR(2): Failed to check '/dev/sdb1' mount state: No such file or directory.
Probably /etc/mtab is missing. It's too risky to continue.
You might try an another Linux Distro.
Unable to read the contents of this filesystem!
Because of this, some operations may be unavailable.[/I]

Is there some command to run to fix this, or am I just going to have to manually edit my fstab & mtab?

---

### Post by markmcc on 2008-04-25
Firstly, thanks for the replies up to now.

As for /etc/fstab, I had a look in there but there is no lines relating to any of my fixed hdd partitions.  Unfortunately, I didn't save a copy off *before* I upgraded, so I don't know what it looked like when the drive was shown OK.

I burnt the Wubi-downloaded ISO to a CD-RW and ran Hardy via LiveCD and my drive appears in that one.  So...

As I don't have any user configuration/data, apart from the ndiswrapper stuff (which I can repeat easy now I know what to do) I think I'll try re-installing BUT from the latest official Hardy via Wubi again, do the update again, and see what happens to my drive.

Thanks again for help,
I'll post my further results here (I hope it's the right place!).

Mark.

---

