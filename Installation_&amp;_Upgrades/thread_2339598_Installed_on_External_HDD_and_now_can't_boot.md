---
title: "Installed on External HDD and now can't boot"
date: 2016-10-10
forum: Installation &amp; Upgrades
---

### Post by tonma on 2016-10-10
I had a PC with dual boot: Windows 10 and Ubuntu 16.04. Then I found an old 500GB HDD and connected it via USB 3.0 hard drive dock to the PC.
I then installed Ubuntu on it as well, so that I have 2 Ubuntus: one on the internal hard drive alongside Windows, and another one on the external.

I partitioned it like that: "/" partition with 496GB and SWAP with 4GB.

The problem is that it seems like the external hard drive installation overwrote the internal bootloader,
and now I can only see the GRUB menu, if I plug the external hard drive.

What I see is just a GRUB command line when I turn on the PC with Ubuntu bootloader ("minimal bash" or something like that)

Currently I disconnected the hard drive, and am using Windows boot loader so I can't access the first Ubuntu if the external hard drive is unplugged.

Is there a way to fix? And what do I need to do next time, so that the external hard drive will just be added to the original GRUB menu?

Thanks!

---

### Post by oldfred on 2016-10-10
If UEFI it is an issue, grub always installs to drive seen as sda.
And then it overwrites /EFI/ubuntu/ but only real change is the 3 line grub.cfg that is a configfile to load the full grub.cfg in your install.
You can edit that grub config, but may have to change settings in fstab as newer Ubuntu sets ESP - efi system partition as read only (the 0777). Older versions used defaults and one of the first things Boot-Repair changes is to defaults so it can update ESP.

I have Multiple installs on sda, sdb and flash drives and no matter what I say during install it overwrites sda. It even will say installing to sdb during install, but overwrites sda.
I quickly learned to backup ESP, but then found just copying grub.cfg worked.

You should be able to boot into main working install and just reinstall grub to sda.

Did you put an ESP on external? Before updating ESP on internal copy ESP from sda to external drive. Then copy again to /EFI/Boot and rename shimx64.efi to bootx64.efi. External drives only boot from /EFI/Boot/bootx64.efi. But the full version of grub installed to sda, needs to find the rest of grub's files in /EFI/ubuntu, so you need both.

I now have multiple folders in /EFI/ including default Ubuntu but then one for every install's version. Then easy to just copy correct grub.cfg.

You also can manually edit grub.cfg in ESP. It just has UUID and drive, so change to correct drive. It can even be one line where you have correct drive, path (What $prefix is) & grub.cfg.

```
search.fs_uuid 255a2800-b871-4fdf-a809-16987e64b8b3 root hd0,gpt6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

---

### Post by tonma on 2016-10-11
Thank you! That's exactly what happened! I checked to install the bootloader on sda and it seemed like it didn't, so I found a simple fix:

I re-plugged the external hard drive, so that the GRUB menu will work, then I logged into the Ubuntu that's on the internal hard drive, and then I ran a sudo install-grub /dev/sdaX (X is the number I needed, just can't remember now :P) and then sudo update-grub

*Btw, looking at the partitions, it seems like Windows installs a bootloader in a different small partition, but I did sudo install-grub on the same partition as the root (in my case root is not separated from /home) - is that ok?

**IMPORTANT IF SOMEONE ELSE HAS THIS ISSUE: DON'T FORGET 'sudo update-grub' !!! < At first I forgot and thought it doesn't work and I almost reinstalled everything.

---

### Post by oldfred on 2016-10-11
You always install grub to a drive like sda or sdb, not to a partition like sda2.
But with UEFI, it knows it must install to the ESP on sda, so it only installs there. 

With multiple installs, each install may on major grub updates, reinstall grub. Or it may switch again. Just be aware.

---

### Post by tonma on 2016-10-12
sda = the main drive? the first drive? For example in my case sda would be the internal PC hard drive? the one that had Ubuntu + Windows in dual boot before I installed the external one? Because if so, I did want it to install on sda, I did want GRUB to remain in the internal hard drive, but id didn't? So in my case it seems like it didn't install on sda? Or I'm mixing a few things together

---

### Post by sudodus on 2016-10-12
Usually yes, sda = the main drive.

But in order to be sure, please post output from the following commands within CODE tags in a reply

[noparse]```

your output line 1
line 2
line 3
...

```[/noparse]

Commands:

```

df -h
sudo lsblk -f
sudo lsblk -m
sudo parted -ls

```

---

### Post by tonma on 2016-10-13
Yep, I just did these commands and sda is the main :)!

But just to let you know: Every time you remove the external hard drive, and then plug it back, you have to do sudo update-grub again, because otherwise the entry for it will not show up

---

