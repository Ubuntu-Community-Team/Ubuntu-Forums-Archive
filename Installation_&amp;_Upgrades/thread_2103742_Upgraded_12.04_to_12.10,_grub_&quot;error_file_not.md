---
title: "Upgraded 12.04 to 12.10, grub &quot;error: file not found&quot;, Boot Repair not working"
date: 2013-01-11
forum: Installation &amp; Upgrades
---

### Post by michael-wd21 on 2013-01-11
Hi,

I just upgraded my home server from 12.04.1 to 12.10. During the  upgrade, I got a message that GRUB could not be installed. I found some  web pages suggesting to ignore the message and carry on. So I did.

Now the system won't boot :sad:  I get:

```
error: file not found
grub rescue>
```I'm not very good with GRUB, so I am  trying to solve the problem with Boot Repair, which looks like it should  help. I use LVM so I am using "Ubuntu Secure Remix 12.10 64-bit" with  Boot Repair.

I booted from the CD, selected "Try Ubuntu". I made sure the network connection is active and then started Boot Repair.

I got a message:

> RAID detected. You may want to retry after installing the [mdadm]  packages. (sudo apt-get install -y --force-yes mdadm  --no-install-recommends)I clicked OK and the main Boot Repair  window appeared. Then I clicked "Recommended Repair" and got this  message:

> Please close all your package managers (Software Center, Update  Manager, Synaptic, ...). Then try again.I'm not running any  package managers. Strange message!

I quit Boot Repair and installed the mdadm packages as suggested then ran boot-repair again.

This time it said:

> [dmraid] packages may interfere with MDraid. Do you want to  remove them?I clicked Yes, and chose Recommended Repair but  again I get the message about package managers. I'm really confused!

Boot Repair has provided this diagnostic URL: [http://paste.ubuntu.com/1519188/](http://paste.ubuntu.com/1519188/)

Thanks in advance.

Michael


EDIT
I tried running grub-install manually. I mounted the server's root volume at /mnt/root, chdir'd into it and created bind mounts for /sys, /proc and /dev:

```

# mount /dev/mapper/os-root /mnt/root
# cd /mnt/root
# mount -o bind /dev/ dev
# mount -o bind /proc/ proc
# mount -o bind /sys/ sys
# chroot .
# grub-install /dev/sda
/usr/sbin/grub-bios-setup: warning: your core.img is unusually large. It won't fit in the embedding area.
/usr/sbin/grub-bios-setup: error: embedding is not possible, but this is required for RAID and LVM install.

```I'm thinking this is why the grub-install failed in the first place.


EDIT 2

So, it seems I either need to get my /boot onto non-LVM disk or have a smaller core.img. I don't have any non-LVM disk in this server, so I would have to free some up from LVM which will be a bit of a project, and seems a bit risky; the other option is to have a core.img that is not unusually large!

Why is my core.img unusually large? Is it possible to have a smaller core.img?

---

### Post by oldfred on 2013-01-11
Grub2 auto creates core.img based on your system configuration. I do not know details, but it seems to be getting larger. It always was larger than the old grub legacy stage 1.5.

Core.img is written into the area after the MBR but before the first partition. All partition tools for the last  couple of years start partitions at sector 2048. Windows XP and Linux until about 2 years ago started at sector 63 which is what you have. 

I did see the same issue where someone had a format other than ext4, and there was a recent thread with a similar issue.

You could file a bug report, but they just may say make more room at beginning of drive?
I do not see any with your issue.
[https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2)
       bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by darkod on 2013-01-11
You should stop making the first partition starting at sector 63. Use 2048 at least (1MiB). I guess you have these disks a while and the partitions were just left as they were earlier when they were starting at sector 63.

With the new versions of ubuntu you don't need separate /boot outside the LVM. Earlier you needed it.

Did you notice that parted -l gives error about /dev/sdb and doesn't show it at all? fdisk -l does the same.

Is it possible you have a problem with the disk, so it can't really find the root partition especially if part of it is on /dev/sdb because the LVM spans both disks.
I would focus on those messages.

---

### Post by michael-wd21 on 2013-01-11
> **oldfred said:**
> Grub2 auto creates core.img based on your system configuration. I do not know details, but it seems to be getting larger. It always was larger than the old grub legacy stage 1.5.

Core.img is written into the area after the MBR but before the first partition. All partition tools for the last  couple of years start partitions at sector 2048. Windows XP and Linux until about 2 years ago started at sector 63 which is what you have. 

I did see the same issue where someone had a format other than ext4, and there was a recent thread with a similar issue.

You could file a bug report, but they just may say make more room at beginning of drive?
I do not see any with your issue.
[https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2)
       bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

> **darkod said:**
> You should stop making the first partition starting at sector 63. Use 2048 at least (1MiB). I guess you have these disks a while and the partitions were just left as they were earlier when they were starting at sector 63.

With the new versions of ubuntu you don't need separate /boot outside the LVM. Earlier you needed it.

Did you notice that parted -l gives error about /dev/sdb and doesn't show it at all? fdisk -l does the same.

Is it possible you have a problem with the disk, so it can't really find the root partition especially if part of it is on /dev/sdb because the LVM spans both disks.
I would focus on those messages.


Yes this system is about two years old and came to me from a vendor with the existing disk configuration, I've had no reason to change it.

I'd be happy to make more room at the start of the drive, but I've no idea how to do it, I can read up but I won't be confident. I haven't done much low-level stuff like this for a few years, and it scares me a bit :)

I did notice that gparted didn't correctly report the available disk, but I put that down to it being on LVM, I have no idea if parted/gparted understand LVM.

---

### Post by darkod on 2013-01-11
It usually can't look inside the LVs so fdisk for example reports like "no valid partition table" for the LVs, but it should definitely report the partitions on the disks as LVM members.

With parted I have actually prepared partitions for mdadm software raid or LVM. It should show the lvm flag on the partition.

Run sudo parted -l and compare /dev/sda with /dev/sdb. You will clearly see the lvm flag reported on sda1.

Did you add the second disk yourself recently, or it was installed long ago? If you did it yourself, did you maybe joined the whole disk as physical device for LVM instead of creating partition on it and using that as physical device?

LVM will accept a whole disk device but it's strongly recommended to make a single partition on the whole disk of LVM type, and use the partition as physical device.

You can easily see if something is wrong with the LVM from live mode. Boot the live cd and add the lvm2 package since it's not included. Activate the LVM and it will list all LVs it activated. If you know all your LVs you will easily see if all are reported as activated correctly:
```
sudo apt-get install lvm2
sudo vgchange -ay
```

Don't forget that the cd doesn't remember the installed lvm2 package since it's read-only. After you reboot and load the live session again, you need to add the package again.

If things turn out for the worse, working from live mode with activated LVs can at least give you the opportunity to backup the data before doing a new clean install.

And I don't know what the reason to upgrade to 12.10 was, but I would stick with LTS releases only for stability and long support. That means the latest 12.04 LTS which you had.

---

### Post by michael-wd21 on 2013-01-11
> **darkod said:**
> It usually can't look inside the LVs so fdisk for example reports like "no valid partition table" for the LVs, but it should definitely report the partitions on the disks as LVM members.

With parted I have actually prepared partitions for mdadm software raid or LVM. It should show the lvm flag on the partition.

Run sudo parted -l and compare /dev/sda with /dev/sdb. You will clearly see the lvm flag reported on sda1.

Did you add the second disk yourself recently, or it was installed long ago? If you did it yourself, did you maybe joined the whole disk as physical device for LVM instead of creating partition on it and using that as physical device?



No I've not made any changes to the disk layout. The machine has hardware RAID, four 1TB disks configured in RAID5 then presented as two volumes of 100GB and 2900GB, which appear to the system as sda and sdb. sda is intended for operating system files and sdb is intended for storage. It has always been that way.

> 
LVM will accept a whole disk device but it's strongly recommended to make a single partition on the whole disk of LVM type, and use the partition as physical device.

You can easily see if something is wrong with the LVM from live mode. Boot the live cd and add the lvm2 package since it's not included. Activate the LVM and it will list all LVs it activated. If you know all your LVs you will easily see if all are reported as activated correctly:
```
sudo apt-get install lvm2
sudo vgchange -ay
```Don't forget that the cd doesn't remember the installed lvm2 package since it's read-only. After you reboot and load the live session again, you need to add the package again.

If things turn out for the worse, working from live mode with activated LVs can at least give you the opportunity to backup the data before doing a new clean install.

And I don't know what the reason to upgrade to 12.10 was, but I would stick with LTS releases only for stability and long support. That means the latest 12.04 LTS which you had.I will try your suggestions, thank you. I have got hold of a new 2TB disk to backup my data for a reinstall if necessary.

EDIT: I've just checked and the machine correctly reports the LVM configuration:

```
$ sudo vgchange -ay
  2 logical volume(s) in volume group "storage" now active
  3 logical volume(s) in volume group "os" now active

```

---

### Post by darkod on 2013-01-11
If the grub packages are OK inside the installation, you don't need chroot just to add grub2 to the MBR.

Try something like this (BUT this assumes grub2 files are OK inside the install):
```
sudo apt-get install lvm2
sudo vgchange -ay
sudo mount /dev/os/root /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

You should use the 12.10 cd since the system is already upgraded to 12.10 and the grub2 versions need to match. If you are confused about the /dev/os/root I used, a LV can be refered to in two ways:
/dev/mapper/VGname-LVname
/dev/VGname/LVname

I prefer the second. I believe your VG is 'os' and LV is 'root'. See if the above commands help install grub2 to the MBR.

---

### Post by michael-wd21 on 2013-01-11
> **darkod said:**
> If the grub packages are OK inside the installation, you don't need chroot just to add grub2 to the MBR.

Try something like this (BUT this assumes grub2 files are OK inside the install):
```
sudo apt-get install lvm2
sudo vgchange -ay
sudo mount /dev/os/root /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```You should use the 12.10 cd since the system is already upgraded to 12.10 and the grub2 versions need to match. If you are confused about the /dev/os/root I used, a LV can be refered to in two ways:
/dev/mapper/VGname-LVname
/dev/VGname/LVname

I prefer the second. I believe your VG is 'os' and LV is 'root'. See if the above commands help install grub2 to the MBR.


Thanks, I tried that but I still get the error about core.img being too large to embed. 

I think I'm just going to bite the bullet and reinstall. Seems the safest option, although it means hours of work I wasn't expecting :cry: But it would probably have happened on the next LTS upgrade, don't you think? So I don't really feel like it's entirely my fault even if I did do an "unnecessary" upgrade. Just feels like one of those corner case gotchas that go with computers ;)

---

### Post by darkod on 2013-01-12
Don't forget to leave 1MiB in front of the first partition when partitioning this time. Depending on how you install, some tools will already do this for you even without telling you. Other tools like parted where you specify exactly the start/end points of the partition, you have to tell it to start at 1MiB.

Since parted has excellent control, I would use it, even from live mode preparing the partitions in advance. Open the disk with it, change the unit to MiB, print the details to note how much MiB capacity the disk has, and create a single partition on the whole disk, activating the lvm flag later. If you want to create ext4 /boot partition in front, you can do that too. So, without the /boot it would be something like:
```
sudo parted /dev/sda
mkpart msdos (new clean msdos partition table)
unit MiB
print
mkpart primary 1 <total MiB size of disk>
set 1 lvm on (set lvm flag on partition #1, adjust if the partition number is different)
quit
```

Don't forget if you use gpt table that you need a 1MiB partition with NO filesystem and the bios_grub flag, so that grub2 can install properly. For msdos tables you don't need this.

---

