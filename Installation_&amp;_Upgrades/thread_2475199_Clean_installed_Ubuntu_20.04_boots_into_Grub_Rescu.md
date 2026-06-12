---
title: "Clean installed Ubuntu 20.04 boots into Grub Rescue"
date: 2022-05-19
forum: Installation &amp; Upgrades
---

### Post by lynx-f on 2022-05-19
Hello everyone!

Ubuntu 20.04 installation finished successfully, with no errors;
but after I restart my PC and push F12 to choose "ubuntu <TOSHIBA HDWD120>",
instead of booting the OS right away I see the "Grub Rescue" command line interface...

After I put the following lines into it:
```

insmod linux
linux (hd1, gpt3)/boot/vmlinuz root=/dev/sdb3
initrd (hd1, gpt3)/boot/initrd.img
boot

```
Ubuntu boots and everything works fine.

I've had Ubuntu 22.04 on the same "sdb3" partition before and that one booted correctly; But I've found out I need the 20.04, so I installed it, deleting 22.04.

Reinstalling 20.04 doesn't make the Grub Rescue go away.
[I]
fdisk -l[/I] command sees some problem with "Partition 1"...
```

Disk /dev/sdb: 1,84 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: TOSHIBA HDWD120 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 6AEDD52E-1879-4CEB

Device          Start        End    Sectors  Size Type
/dev/sdb1          34      32767      32734   16M Microsoft reserved
/dev/sdb2       32768 3697311743 3697278976  1,7T Microsoft basic data
/dev/sdb3  3697311744 3907028991  209717248  100G Linux filesystem

**Partition 1 does not start on physical sector boundary.**


Disk /dev/sda: 1,84 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: TOSHIBA HDWA120 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: D6290E33-FB31-413E

Device          Start        End    Sectors   Size Type
/dev/sda1        2048    1023999    1021952   499M Windows recovery environment
/dev/sda2     1024000    1228799     204800   100M EFI System
/dev/sda3     1228800    1261567      32768    16M Microsoft reserved
/dev/sda4     1261568 1024002047 1022740480 487,7G Microsoft basic data
/dev/sda5  1024002048 3907028991 2883026944   1,4T Microsoft basic data

```

My question is:
Is there something I can do to make Grub automatically execute the aforementioned several commands which I now have to enter manually every time I reboot?

---

### Post by lynx-f on 2022-05-19
I should add that
```

sudo update-grub
sudo grub-install /dev/sdb3

```

didn't help yet, it says:
```

grub-install: warning: File system `ext2' doesn't support embedding.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.

```

Also I seem to have the ext4 filesystem, not ext2 on sdb3

---

### Post by Impavidus on 2022-05-19
My guess is that Ubuntu 20.04 installed grub in a different place than Ubuntu 22.04 and, when booting, you still run 22.04's grub, which can't find its configuration file. I wonder whether there may be an UEFI/legacy mix-up...

There appears to be a Windows system installed (which you didn't mention) and there is an EFI partition. Is this an UEFI system? In that case, grub should be installed in the EFI partition. Only in very rare cases on legacy systems should grub be installed in a partition boot record, like you attempted (and failed) with the grub-install command.

It may be best to look at the details. Try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). Use the second option (install boot repair in Ubuntu) and create a boot info summary. Share the link with us.

---

### Post by tea for one on 2022-05-19
It is not good practice to install Grub to a partition, indicated by [COLOR="#0000FF"]sudo grub-install /dev/sdb3[/COLOR].

Also as you have two drives, have you considered each OS installed separately in UEFI mode?
Each OS will have its individual boot manager and will be easier to manage in the future.

---

### Post by seminiva on 2022-05-19
Most likely the author has exactly two disks

---

### Post by yancek on 2022-05-19
What option for the installation of Grub did you select during the install of Ubuntu 20.04.  The default would have been to install to the EFI partition (sda2).  If you selected to install to /dev/sda it should have installed the Grub EFI files to /dev/sda2.  I believe you could also have selected to install to /dev/sda2 but I've never used that option.  

The error you show is trying to install to a partition.  You can do that during the installation but the only reason to do that is if you have another Linux OS installed and want to use that OS's bootloader as the primary bootloader.

You could try mounting the EFI partition (sda2) from the Ubuntu install USB and checking the grub.cfg file there.  Check the UUID there and compare it to the output of blkid.  THe UUID in that grub.cfg file should be the same as the UUID for sdb3.  If it is not, change it.  If you do not have an Ubuntu directory on the EFI partition, that means you did not install Grub in EFI.

>  **Partition 1 does not start on physical sector boundary**

That's a common warning and won't affect booting.  If this doesn't help, download and run bootrepair suggested in post 3.  Use option 2 explained on 
the page and select Create BootInfo Summary option and do not try to repair.  Post the link you get when it finishes here.

---

### Post by lynx-f on 2022-05-20
Here is my BootInfo Summary:
[https://paste.ubuntu.com/p/CcW9y4Fzcn/](https://paste.ubuntu.com/p/CcW9y4Fzcn/)

It seems the **sdb3** Grub is broken or something, and there is a Grub at **sda2** - I didn't know Ubuntu puts anything on the **sda** drive, thats my Windows HDD...

I do not know whether the **sda2** Grub is the correct one or the one from 22.04...

Should I try boot-repair in a live-session?

Yes, I've got 2 HDD's and an SSD, but I need the SSD for some programming stuff for which the i/o speed really matters, so I've installed Ubuntu on **sdb3**

---

### Post by tea for one on 2022-05-20
> **lynx-f said:**
> Should I try boot-repair in a live-session?

As you already know how to boot into Ubuntu from Grub Rescue, probably worth a shot.

In my post 4 about each OS on a separate drive, it is necessary that each drive has an EFI partition to control each drive booting independently.
You only have one EFI partition on sda, therefore it is more difficult to manage especially when one OS updates and it may interfere with the boot of the second OS.

---

### Post by lynx-f on 2022-05-20
> I restart my PC and push F12 to choose "ubuntu <TOSHIBA HDWD120>"

Ah, I'm sorry: the option I actually choose after rebooting and pressing F12 is labeled "P0: ubuntu <TOSHIBA HDW**A**120>", this suggests my first HDD, **sda**

So I guess I see the Grub from **sda2**

Can I configure it somehow to know to load the kernel from **sdb3**?

---

### Post by tea for one on 2022-05-20
> **lynx-f said:**
> Can I configure it somehow to know to load the kernel from **sdb3**?

The following lines from the boot-repair report indicate that the repair will perform the desired result.

[COLOR="#0000FF"]Line 327[/COLOR] - The default repair of the Boot-Repair utility would purge (in order to fix packages) and reinstall the grub-efi of
[COLOR="#0000FF"]Line 328[/COLOR] - sdb3
[COLOR="#0000FF"]Line 329[/COLOR] - using the following options:  sda2/boot/efi

---

### Post by oldfred on 2022-05-20
Line 240 shows an UUID that does not exist. That is the issue.
Grub was not properly reinstalled.
You can edit /EFI/ubuntu/grub with correct UUID, but if you can boot, but do not have a mount of correct ESP in fstab line 255.
Full reinstall of grub when booted in UEFI mode will correct both of those issues.
Or as tea for one sugests the total reinstall with Boot-Repair should work.

You almost never install grub to a partition, I think the installer must have let you do that with a BIOS install, but it assumes you know you need another grub to chain to that grub to make it work. No system can directly boot a partition.

---

### Post by lynx-f on 2022-05-20
Many thanks to everyone!

Running Recommended Repair in boot-repair from live-USB in UEFI mode did help: also I smh have two "Ubuntu" options in F12 menu now, at least one of them successfully boots the OS without tedious incantations)

---

### Post by oldfred on 2022-05-20
I thought new ubuntu entry would have overwritten the incorrect one.

But you can delete one entry, just be sure to delete one that does not work.

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

UEFI uses partUUID/GUID to know which ESP to boot from.
You can check partUUIDs:
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

---

