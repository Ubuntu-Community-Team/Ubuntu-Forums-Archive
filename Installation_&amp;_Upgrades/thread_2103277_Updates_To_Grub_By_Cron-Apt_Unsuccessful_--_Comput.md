---
title: "Updates To Grub By Cron-Apt Unsuccessful -- Computer Doesn't Boot"
date: 2013-01-09
forum: Installation &amp; Upgrades
---

### Post by Kirk Schnable on 2013-01-09
Earlier this week, I started this thread:
[http://ubuntuforums.org/showthread.php?p=12447070](http://ubuntuforums.org/showthread.php?p=12447070)

I have determined now what the issue is at least, and now I am ready to start troubleshooting it.

**_Here are the steps to reproduce this issue:_**
**1. Start with a fresh image of Xubuntu 12.04, with GRUB 1.99-21ubuntu3.4**
Our fresh image installed on all of our computers is Xubuntu 12.04.1 LTS with grub-common 1.99-21ubuntu3.4 selected in DPKG.

**2. Have an old-style partition setup.**
We have never had a problem with this traditional partition layout before, but it doesn't seem to comply with the new UEFI standards.  Most of our hardware here is very old, and the thought of UEFI support hasn't been a priority for us.
```
# fdisk -l /dev/sda
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ca480

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1    78165359    39082679+  ee  GPT
```
[img]http://binaryimpulse.com/wp-content/uploads/2013/01/gparted.png[/img]

**3. Attempt to update all packages with cron-apt.**
```
# /etc/cron.d/cron-apt
0 *	* * *	root	test -x /usr/sbin/cron-apt && /usr/sbin/cron-apt /etc/cron-apt/config2
```

```
# /etc/cron-apt/action.d/0-update
update -o quiet=2
```

```
# /etc/cron-apt/action.d/3-download
autoclean -y
dist-upgrade -y -o APT::Get::Show-Upgraded=true
```

**4. Cron-Apt Upgrades GRUB to 1.99-21ubuntu3.7**
After the upgrade (automated by cron-apt) to GRUB 1.99-21ubuntu3.7, if the computer is restarted, it never boots again.  Instead, you see a blinking cursor on the upper-left corner of a black screen.


So far, our only success was finding a Super GRUB boot CD, which scanned the drive for Linux kernels, and allowed us to choose to boot into the latest one.  When using GRUB from the CD, the computer booted, which confirmed our belief that there was a GRUB problem.


After a successful boot, we found a command to fix the problem:
```
sudo grub-install --boot-directory=/boot /dev/sda --force
```

If this command is run **without** the --force, GRUB doesn't succeed in installing because of our partition layout.  This causes the next boot to fail, the same way as the cron-apt update did.

```
# Failed Output (without --force)
# grub-install  --boot-directory=/boot /dev/sda
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
```

My suspicion is that cron-apt is not using the --force option when updating GRUB.  Changing the partition layout on 800 computers is *not* a preferred option, so I need to come up with a way to have the cron-apt GRUB updates succeed, now and in the future.

Do you think this is a problem with GRUB 1.99-21ubuntu3.7, or a common part of all future GRUB updates?

We have not been able to find anyone else who has had this issue... sifting through Google for countless hours, and working a 16 hour shift on Monday.  We feel very victorious today for finding out how to fix the problem, but now we'd like to determine the best way to create a patch to keep our machines updating and running for the foreseeable future.

We'd appreciate any information or suggestions anyone might have!

Thanks,
Kirk

---

### Post by TheFu on 2013-01-09
Do not use** fdisk** unless you are POSITIVE that an MSDOS partition is there.  fdisk is **warning you** (see the 2nd line?) that it is a GPT partition table.  You should be using either **gparted **or **parted **to manage or eve view the partitions.[B] 

Using fdisk is dangerous to your partitions, so all the data on the disk is at risk.[/B]

For boot issues, I try **boot-repair **first. It will handle almost anything, provided the partition table hasn't been screwed up. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) has instructions.

---

### Post by Kirk Schnable on 2013-01-09
> **TheFu said:**
> Do not use** fdisk** unless you are POSITIVE that an MSDOS partition is there.  fdisk is **warning you** (see the 2nd line?) that it is a GPT partition table.  You should be using either **gparted **or **parted **to manage or eve view the partitions.[B] 

Using fdisk is dangerous to your partitions, so all the data on the disk is at risk.[/B]

We were merely using fdisk output as a demonstration of our partition table.  We were not using it to modify partitions, we used parted to create our layout.



> **TheFu said:**
> For boot issues, I try **boot-repair **first. It will handle almost anything, provided the partition table hasn't been screwed up. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) has instructions.
I am aware of Boot-Repair, but I am not really interested in running Boot-Repair on 800 computers every few months when a new GRUB update comes out...

I am looking for a more permanent update solution, not fixing the boot record on a single computer.

---

### Post by Kirk Schnable on 2013-01-09
I have written a workaround which will hopefully patch this issue for us.

I am testing it on a lab of computers tonight, and we'll see if we put it further into production tomorrow...

If it works well for us, I'll gladly post it here, although I am by no means suggesting a workaround as a permanent solution.

In the long-term, I think we need to re-evaluate our partition layout, but hopefully this patch will last us until summer break when we will have the extra staff and time when the computers aren't in use to reimage them.

---

### Post by TheFu on 2013-01-10
> **Kirk Schnable said:**
> We were merely using fdisk output as a demonstration of our partition table.  We were not using it to modify partitions, we used parted to create our layout.

But it may not be showing all the partition data.  fdisk only shows what it can read - the MSDOS partition table that GPT disks put in place as a backup.

> **Kirk Schnable said:**
> I am aware of Boot-Repair, but I am not really interested in running Boot-Repair on 800 computers every few months when a new GRUB update comes out...

I am looking for a more permanent update solution, not fixing the boot record on a single computer.

I was under the impression that this was a 1-time problem and that you would be re-imaging all the HDDs through automatic methods.  Fix it on 1 PC, then push that image out using Clonezilla or PartImage to all the other systems.  I don't know your logistics, so you may not have yet setup a partition that you can force to reboot into which will update all the other partitions automatically.  If I had 800 desktops at a college, I'd setup something like that ASAP.

---

### Post by Kirk Schnable on 2013-01-10
> **TheFu said:**
> But it may not be showing all the partition data.  fdisk only shows what it can read - the MSDOS partition table that GPT disks put in place as a backup.
It showed the partition on the drive so I figured it was decent enough for the purpose.

> **TheFu said:**
> I was under the impression that this was a 1-time problem and that you would be re-imaging all the HDDs through automatic methods.  Fix it on 1 PC, then push that image out using Clonezilla or PartImage to all the other systems.  I don't know your logistics, so you may not have yet setup a partition that you can force to reboot into which will update all the other partitions automatically.  If I had 800 desktops at a college, I'd setup something like that ASAP.
We do have an automated imaging solution here based on CloneZilla, but the computers have to be manually PXE booted, and then we have the boot screen password protected to prevent computer vandalism through the system.  The computers then request a name and we enter it.  It's not 100% automated, it could be, but we've found that we can't reliably rename computers as they're moved around if it's automated, etc... so it's as automated as made sense for us.

Of our Linux computers, we now have two desktop labs of 31 computers.  The rest of them are laptops and netbooks, which need to be manually plugged in to network ports in order to PXE boot them.  When I imaged them, I used a mobile imaging cart with switches on wheels.
[[img]http://binaryimpulse.com/wp-content/uploads/2013/01/ZBcHg40FZpLsVZv3dUMxrE0hV9YeJgc7j7u843gNIiU-800x597.jpeg[/img]]("http://binaryimpulse.com/wp-content/uploads/2013/01/ZBcHg40FZpLsVZv3dUMxrE0hV9YeJgc7j7u843gNIiU.jpeg")

Kirk

---

### Post by Kirk Schnable on 2013-01-10
I have started a new thread to contain my evolved question on proper GPT partitioning:
[http://ubuntuforums.org/showthread.php?p=12448305](http://ubuntuforums.org/showthread.php?p=12448305)

I am presently testing my workaround script on all computers in our building today, and I will publish it here if it is successful.

---

