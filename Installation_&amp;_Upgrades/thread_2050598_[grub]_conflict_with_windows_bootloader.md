---
title: "[grub] conflict with windows bootloader"
date: 2012-08-31
forum: Installation &amp; Upgrades
---

### Post by MuffinMan123 on 2012-08-31
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

originally I was using easybcd according to this tutorial to add linux, fedora to be specific.

so the harddrive looks like this

mbr windows loader
windows
/boot grub loader
/root
/home
/swap

but somewhere down the line I screwed up linux, and I used the easy way to reinstall fedora with "remove preinstalled linux"

now all those partitions were reset, but it didn't let me change the bootloader option this time and grub became dominant bootloader

**I want to change change the grub to use the /boot partition and give mbr back to windows loader and make it dominant**

my insistence to use windows loader is because my computer is still almost brand new and I want to make sure I can still return this with windows as the main option so they won't give me too much hassle.

as mentioned in the linked tutorial, this is another reason I decided to stick with windows loader as main
> When dual-booting Windows 7 and a Linux distribution on a computer with  one hard drive, the best option is to have Windows 7&#8242;s boot manager be  the primary boot manager. Why? Because whenever you reinstall or update  Windows 7, its installer will overwrite anything it finds in the portion  of the hard drive where critical boot-related programs are installed.

---

### Post by darkod on 2012-08-31
The part that says "updating windows" is a bit misleading. It will only overwrite the boot sector when you reinstall or upgrade to a new version. How often do new versions of windows come out?

Otherwise, doing the windows updates doesn't touch the bootloader.

Besides, you are talking about a fedora installation which might have differences with ubuntu. Why are you asking on this forum? Personally, I don't know fedora in details to advise you.

Since windows bootloader can't boot linux, usually the best solution is to use grub on the MBR, not insist on windows, unless you have a specific setup. If your only worry is putting back windows bootloader if you ever need to, that's easily done in 2 minutes.

---

### Post by MuffinMan123 on 2012-08-31
> **darkod said:**
> The part that says "updating windows" is a bit misleading. It will only overwrite the boot sector when you reinstall or upgrade to a new version. How often do new versions of windows come out?

windows 8 is about to come out

> 
Besides, you are talking about a fedora installation which might have differences with ubuntu. Why are you asking on this forum? Personally, I don't know fedora in details to advise you.
this is strictly a grub question, I want to know how to move grub to another partition, and then have windows loader using easyBCD to chain to grub 2 loader

> 
Since windows bootloader can't boot linux, usually the best solution is to use grub on the MBR, not insist on windows, unless you have a specific setup. If your only worry is putting back windows bootloader if you ever need to, that's easily done in 2 minutes.again, I am considering returning this computer if everything doesn't work out, I need to have it as master loader so the store clerk won't give me a hassle about it when I return it.

and I don't have and cannot use windows live CD to do it the easy way because the small size notebook form factor doesn't allow DVD drive.

---

### Post by darkod on 2012-08-31
> **MuffinMan123 said:**
> 
this is strictly a grub question, I want to know how to move grub to another partition, and then have windows loader using easyBCD to chain to grub 2 loader

Again, the commands are not always identical in all distros. In ubuntu, what you would do to install grub2 on a partition is boot ubuntu, open terminal and do:
sudo grub-install -f /dev/sdXY

Replace the XY with the correct device letter and partition number (since you didn't specify the partitions more precisely with device names).

But I can't guarantee you that will work on fedora.

> again, I am considering returning this computer because it's crap, I need to have it as master loader so the store clerk won't be a jerk about it

and I don't have windows live CD to do it the easy way.And yet you don't mind installing dual boot on it while planning to return it?

I never said you needed the windows DVD. First of all, most computers would come with recovery partition or recovery DVDs. That's usually the best way to return it to factory state before you return it. In that case, it doesn't matter what the bootloader was, the recovery process will wipe everything.

Second, you can use linux tools even without windows DVD to write a generic MBR which does the same job as the windows bootloader. If they just turn it on, they will see windows booting. Unless they start looking in details with linux tools, they won't even notice the MBT is slightly different.

---

### Post by MuffinMan123 on 2012-08-31
the recovery tool doesn't wipe the harddrive, it only restores partition based stuff unfortunately.

> **darkod said:**
> Second, you can use linux tools even without  windows DVD to write a generic MBR which does the same job as the  windows bootloader. If they just turn it on, they will see windows  booting. Unless they start looking in details with linux tools, they  won't even notice the MBT is slightly different.

this is the part that I can't find.

damn it, still can't get linux to work the way I want it to. I will just recover mbr 1st, and then use grub bootdisc to wipe out the partitions.

---

### Post by MuffinMan123 on 2012-08-31
never mind this. I used easybcd and windows disc tools to restore to previous settings.

---

### Post by darkod on 2012-08-31
> **MuffinMan123 said:**
> the recovery tool doesn't wipe the harddrive, it only restores partition based stuff unfortunately.



this is the part that I can't find.

damn it, still can't get linux to work the way I want it to. I will just recover mbr 1st, and then use grub bootdisc to wipe out the partitions.

For future reference, if what you wanted is to write generic MBR with linux tools, you can boot the ubuntu cd in live mode and use lilo:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

That will write generic MBR which acts the same as windows bootloader, in other words, continues booting the partition with the boot flag on it.

While running the first command I think lilo will throw some warnings about configuration at you, ignore them, you are using only part of lilo to write a MBR, not the full bootloader.

Another package about installing a MBR, but I don't know if you need to install it first, is:
```
sudo install-mbr /dev/sda
```

---

