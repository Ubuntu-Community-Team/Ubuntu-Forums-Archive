---
title: "Windows loader after lubuntu install"
date: 2015-04-14
forum: Installation &amp; Upgrades
---

### Post by boris6 on 2015-04-14
I have 3 hard drives on my PC, 1 i use for OS. When i was installing lubuntu i formated it to ext4 and installed without a problem. I restart and windows(8.1) recovery starts instead of lubuntu. I load lubuntu from a flash drive, install Boot-repair, run with recommended settings and it doesn't help. My urls is paste.ubuntu.com/10823618. I'm open to any suggestions you might have.

At one point during boot repair's run i am asked about deleting grub 2 - agreed to it.

---

### Post by oldfred on 2015-04-14
I do not see Windows anywhere??

You show a LVM install on sda. LVM is logical partitions inside the physical partitions. Required for full drive encryption, but is a full drive install normally. So if you chose that and did not specify anything else you erased entire drive.

Often with multiple drives better to have a different operating system on every drive. And have its boot loader on that same drive. Some suggest even disconnecting all other drives which makes each install separate. But you can do the same, but must have UEFI/BIOS settings correct and choose correct install options for each system.

---

### Post by boris6 on 2015-04-15
Like i said - i formated the drive Windows was using and installed Linux on it. Is it possible there is a windows loader on another drive somehow? (the other drives i use for storage/torrents - no software or OS has ever been installed there)

---

### Post by oldfred on 2015-04-15
You do have Windows boot loaders on sdb & sdc.

Do you not have sda as default boot in BIOS?

---

### Post by boris6 on 2015-04-15
It is default, even if it isn't there shouldn't be any loaders anywhere, on any hard drive... I know - it's weird.. :)

---

### Post by oldfred on 2015-04-15
Once a boot loader is added to a MBR, it is not deleted, just overwritten when needed with a new system.
But if you are getting Windows boot error then BIOS is booting from one of those drives. If for some reason BIOS does not see sda  correctly to boot from then it may be set to try the next drive?

---

