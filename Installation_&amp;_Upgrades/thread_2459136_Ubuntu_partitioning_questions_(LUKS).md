---
title: "Ubuntu partitioning questions (LUKS)"
date: 2021-03-11
forum: Installation &amp; Upgrades
---

### Post by crpz41 on 2021-03-11
I wish to install ubuntu on a specific SSDon the system, so I have to manually create the partitions otherwise the installer would wipe other SSD on the system.
On top of that I need to encrypt the partition with LUKS. can someone guide me in the partitioning process so I know how many partition and what kind.
 thanks

---

### Post by oldfred on 2021-03-11
UEFI or BIOS based system.
If UEFI or BIOS with only Ubuntu use gpt partitioning.
[http://www.rodsbooks.com/gdisk/whatsgpt.html](http://www.rodsbooks.com/gdisk/whatsgpt.html)

[https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019) & 
[https://help.ubuntu.com/community/ManualFullSystemEncryption/](https://help.ubuntu.com/community/ManualFullSystemEncryption/)
Full-system encryption with manual control and dual-booting Paddy Landau
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) & 
[https://ubuntuforums.org/showthread.php?t=2399092](https://ubuntuforums.org/showthread.php?t=2399092)

---

### Post by TheFu on 2021-03-11
So ... setting up whole disk encryption through the installer is really easy.  Just disconnect any storage you don't want touched.  Then the remaining drive will be encrypted and all is fine.  Post install, you can mount the other storage in the normal way through the fstab.

If you want to dual boot, this is a non-trivial effort. Expect to work through it a number of times before you get it correct. Paddy has been working on his how-to for years.  For me, anything that is so complex that it needs more than 10 steps to accomplish will be a maintenance nightmare that I'd rather avoid.

Rather than dual booting, I've strongly suggest encrypting everything and running any other OS under a virtual machine.  That simplifies all sorts of things.  Or you could go the other way and put Ubuntu inside a VM, choose whole drive encryption for that VM install and only worry about the risks of the hostOS being compromised, but your Ubuntu OS and data would be secure - provided the VM is off.

The disk layout post-install with whole drive encryption is something I modify.  It lays down a simple partitioning solution, then creates an encrypted container on the largest partitions, then creates an LVM PV and VG inside that LUKS container.  All great. Love it. Perfect, so far.  Where the installer fails is with setting up different LVs for 
[LIST]
[*]/
[*]/home
[*]swap
[/LIST]
Immediate after the install finishes, I boot again using a *try ubuntu* ISO, unlock the LUKS container, activate the LVM stuff and reduce the / LV from whatever size they create (dependent on the total available storage) down to about 30G.  Then I setup 4.1G for a swap LV and setup whatever is left for /home and a "data" LV for stuff that doesn't need to be backed up ever - like TV shows, music, videos.  
Here's an example: [https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)

An LV can almost always be considered a partition. We use them exactly the same way, but LVs are extremely flexible and LVM brings all sorts of kewl features to storage, but you have to use it properly.  The keys to LVM are:
[LIST]
[*]Never allocate all the storage to LVs. 
[*]Only use what you need for the next few months.
[*]With SSDs try to leave 20% unused, always.
[*]Extending an LV is trivial. Takes 5 seconds on an actively use, running, file system. If ext4 is the file system, extending the LV and the file system can be done with 1 command.
[*]Reducing an LV is a pain. Takes rebooting and running from a **Try Ubuntu** setup. Avoid this.
[/LIST]
When LVM is used, we can make perfect backups thanks to LVM snapshots, but only if some storage hasn't been allocated and can be used for the snapshot area.

LVM is extremely powerful. Having it means all sorts of things that are nearly impossible with normal partitions become possible on a running, active, system. But with this power, comes a little complexity, as you may expect.

---

### Post by tea for one on 2021-03-11
> **crpz41 said:**
> I wish to install ubuntu on a specific SSDon the system, so I have to manually create the partitions otherwise the installer would wipe other SSD on the system.
On top of that I need to encrypt the partition with LUKS. can someone guide me in the partitioning process so I know how many partition and what kind.
 thanks

As mentioned by [COLOR="#0000FF"]TheFu[/COLOR], I think that it is essential to isolate any SSD which you do not want to be affected by a new OS.

The installer will create the partitions for you unless you have very specific requirements.

You should then be able to access either OS via the UEFI boot menu.

Ensure that all installations are in UEFI mode.

Finally, always have restorable backups at all times, especially when installing a new system.

---

### Post by crpz41 on 2021-03-13
> **TheFu said:**
> So ... setting up whole disk encryption through the installer is really easy.  Just disconnect any storage you don't want touched.  Then the remaining drive will be encrypted and all is fine.  Post install, you can mount the other storage in the normal way through the fstab.

.

I cannot unplug other SSDs on the system. I just need to know how to create partitioning manually for encrypted disk (only a specific SSD, not the others)

---

### Post by CelticWarrior on 2021-03-13
You can disabled/enable any drive in UEFI or BIOS.

---

### Post by TheFu on 2021-03-13
> **crpz41 said:**
> I cannot unplug other SSDs on the system. I just need to know how to create partitioning manually for encrypted disk (only a specific SSD, not the others)

Manually encrypting a data partition is really easy.

But manually encrypting part of the OS is not. Letting the OS install handle that is 1 or 2 checkboxes during install, but it will wipe everything on the disk.  

I've never allowed more than 1 disk to be connected when encrypting a new install - well that isn't quite true. The target SSD/HDD and then there's a USB flash install disk, but I'm not counting the install disk.  I suppose if you want to try all this stuff out a few times first, you could gain some experience doing a few installs into a virtual machine.  VMs are very handy for trying out new skills with zero risk.

---

### Post by crpz41 on 2021-03-13
with my BIOS you cannot. even if asus bios are full of options

---

