---
title: "Installer just asumed I wanted RAID..."
date: 2012-04-10
forum: Installation &amp; Upgrades
---

### Post by sorceror on 2012-04-10
I'm 'recommissioning' a machine to be used by my kids. It's got an ECS A770M-A motherboard, and two identical 120GB drives. It *could* be used in a RAID configuration, but wasn't. (No critical data was stored on it.) It had a Windows XP installation, and an older Linux installation.

The first drive had the Windows boot partition and a bunch of Linux partitions (it had been running Ubuntu 11.04). The second drive had some larger Windows partitions, and a swap partition. I'd gotten the Windows system where I wanted it, and then went to install Xubuntu 11.10 amd64.

I ran the installer, and set it to wipe out the Linux partitions, create a new Linux and swap partition, and kicked off the install. I never looked at the second disk in the installer, as I didn't intend any changes there.

Once the install was done and I rebooted, I discovered that the installer had apparently assumed I wanted a RAID setup, and overwrote the partition table on the second disk with a copy of the first. I haven't had a chance to determine if it actually overwrote data on the second disk, but since I didn't have a backup of the old partition table it's a moot point anyway.

I didn't lose any data 'cause I'd already moved off whatever I wanted/needed, but still - *yikes*. Did I miss the installer asking about RAID at some point? Or did it just think, "Hey - two identical disk! Let's do some RAID!"

---

### Post by darkod on 2012-04-10
No, it never creates RAID for you, BUT.... If it detects raid meta data on the disks (maybe from earlier setup), it can activate that array although it is asking you before that.

Another option is that the board BIOS is set to RAID in the SATA options. Make sure it's AHCI (or IDE mode if you need it for XP to recognize the disks).

If you are sure you don't want to use raid (and you seem sure), boot into live mode first with the cd and in terminal try:
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

If that asks you if you want to remove raid meta data, you HAD (HAVE) raid meta data remains on the disk(s). That will get rid of it.

That command works from ubuntu, I hope it works from Xubuntu too.

---

### Post by roelforg on 2012-04-10
> **sorceror said:**
> I'm 'recommissioning' a machine to be used by my kids. It's got an ECS A770M-A motherboard, and two identical 120GB drives. It *could* be used in a RAID configuration, but wasn't. (No critical data was stored on it.) It had a Windows XP installation, and an older Linux installation.
 
The first drive had the Windows boot partition and a bunch of Linux partitions (it had been running Ubuntu 11.04). The second drive had some larger Windows partitions, and a swap partition. I'd gotten the Windows system where I wanted it, and then went to install Xubuntu 11.10 amd64.
 
I ran the installer, and set it to wipe out the Linux partitions, create a new Linux and swap partition, and kicked off the install. I never looked at the second disk in the installer, as I didn't intend any changes there.
 
Once the install was done and I rebooted, I discovered that the installer had apparently assumed I wanted a RAID setup, and overwrote the partition table on the second disk with a copy of the first. I haven't had a chance to determine if it actually overwrote data on the second disk, but since I didn't have a backup of the old partition table it's a moot point anyway.
 
I didn't lose any data 'cause I'd already moved off whatever I wanted/needed, but still - *yikes*. Did I miss the installer asking about RAID at some point? Or did it just think, "Hey - two identical disk! Let's do some RAID!"
If it's a second disk:
Golden rule: if it ain't a blank win hd, unplug it during install and use update-grub to insert the windows entry later

---

### Post by sorceror on 2012-04-11
> **darkod said:**
> If you are sure you don't want to use raid (and you seem sure), boot into live mode first with the cd and in terminal try:
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

If that asks you if you want to remove raid meta data, you HAD (HAVE) raid meta data remains on the disk(s). That will get rid of it.

That seems to be the issue. Neither Windows XP nor my prior install were using that data, but the data seems to have existed. At some point I'll try a reinstall and see what happens now that it's been removed.

I still don't recall being asked about RAID during the install, though. Oh, well.

---

### Post by darkod on 2012-04-11
I might be wrong about the question. Because usually the Alternate CD is used for raid installs, I know for sure it asks you if you want to activate the existing array (for fakeraid, bios raid).

But since the standard, live CD also contains the package to recognize the raid, it might not ask you anything. And depending what install method are you using, it actually could install automatically on the raid.

If you used manual method, you would notice the device is called dev/mapper/bla-bla and that will warn you that the destination is a raid device.

But if you use the auto methods, I am not really sure what will happen. It should say it will install on /dev/mapper/.... but maybe it's not that obvious.

---

### Post by sorceror on 2012-04-16
> **darkod said:**
> But if you use the auto methods, I am not really sure what will happen. It should say it will install on /dev/mapper/.... but maybe it's not that obvious.

It *did* say /dev/mapper, but - since I haven't played around with RAID - I didn't know that meant "RAID". With the metadata removed, I was able to put different data and partitions on each drive.

Not sure how (or if) to rework the installer for what's admittedly a corner case... oh, well. Live and learn.

---

### Post by darkod on 2012-04-16
> **sorceror said:**
> It *did* say /dev/mapper, but - since I haven't played around with RAID - I didn't know that meant "RAID". With the metadata removed, I was able to put different data and partitions on each drive.

Not sure how (or if) to rework the installer for what's admittedly a corner case... oh, well. Live and learn.

Well, for future reference, the device names also differ depending on:

- software raid -> /dev/md0, /dev/md1, etc
- fakeraid, hardware raid -> /dev/mapper/XXXXXX
- LVM -> /dev/mapper/VolumeGroup-LogicalVolume

If you have it set up the way you want it, please mark the thread as Solved. You can do this in Thread Tools above the first post.

Cheers.

---

