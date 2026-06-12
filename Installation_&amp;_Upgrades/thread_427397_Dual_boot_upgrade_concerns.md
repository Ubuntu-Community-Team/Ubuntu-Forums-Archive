---
title: "Dual boot upgrade concerns"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by adastra23 on 2007-04-29
I have a dual-boot xp and ubuntu machine, I know that I should to backup menu.lst and grub.conf at least for reference when upgrading from edgy to feisty.  I have heard that it went smooth for other 'dual-booters' that have one drive. I have a SATA drive with ubuntu and a EIDE drive with xp. Anyone have any idea if this will make a difference with the upgrade? (I can't lose xp right now, my wife uses it for school.)
What concerns me, I guess, is the fact that Feisty uses UUIDs for the drives now. Will this make a difference, or will I be able to modify the menu.lst and grub.conf accordingly.

---

### Post by confused57 on 2007-04-29
> **adastra23 said:**
> I have a dual-boot xp and ubuntu machine, I know that I should to backup menu.lst and grub.conf at least for reference when upgrading from edgy to feisty.  I have heard that it went smooth for other 'dual-booters' that have one drive. I have a SATA drive with ubuntu and a EIDE drive with xp. Anyone have any idea if this will make a difference with the upgrade? (I can't lose xp right now, my wife uses it for school.)
What concerns me, I guess, is the fact that Feisty uses UUIDs for the drives now. Will this make a difference, or will I be able to modify the menu.lst and grub.conf accordingly.

I wouldn't be in a hurry to upgrade to Feisty, especially since your wife needs XP, and I'm not sure you'd see any performance increase.  Feisty will recognize both hard drives as SATA and Feisty uses UUID's in the kernel root designation...Edgy also used UUID's to identify partition filesystems in fstab.

If you have a Window's install cd, you can always restore your Window's drive mbr if something goes wrong with the upgrade:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You might want to burn a copy of the Super Grub Disk before upgrading:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD would be able to help recover if there is a problem

Also, here's how I have my system set up:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by bulldog on 2007-04-29
When you gonna upgrade check your sources.list to see if there are no 'alien' sources active,they can't be upgraded so you have to comment them out ##
Only the official repositories for ubuntu can be listed there,otherwise your heading for a lot of trouble.

The UUID is a new way to identify your partitions,you can easily find them your self and modify them if necessary.
```
ls /dev/disk/by-uuid -lh
``` in a terminal is sufficient to find them.

If you are very concern about your windows,you can disconnect this hdd when you do the upgrade,so nothing can happen with it.
If you have GRUB installed on the windows hdd,I would advice you to reinstall GRUB to the Sata hdd,**and make this Sata hdd your master boot device**
You only have to change the windows entry in the menu.lst a little to get windows to boot,but that's a minor thing.

---

