---
title: "Install results in old Linux kernel"
date: 2015-11-12
forum: Installation &amp; Upgrades
---

### Post by jim_stevenson on 2015-11-12
Hi,  I have installed Ubuntu 15.10 by using a DVD burnt from an ISO image via the Ubuntu site.

Installation successfully completed but I expected to have a Linux kernel 4.2.x. Instead I have Linux kernel 3.16.x.

Any idea what is going wrong?

Installation used manual disk partitioning with the installer reformatting the empty space and allocating this as the mount point.  The disk is an SSD partitioned as GPT with an EFI system partition.  Gparted reported no problems with the disk or partition.  The only unexpected aspect of the install was I expected  an EFI system but actually was asked to provide an boot location as per an MBR disk.  This should not in my view have influenced the Linux kernel version but I include this info in case it is relevant.  I am not bothered about the problem of EFI versus MBR as I will investigate this further but I am totally lost where to begin finding out why an earlier kernel was used.
Any ideas of where to start looking would be appreciated.

Jim

---

### Post by Bashing-om on 2015-11-12
jim_stevenson; Hello;

I would question what release is installed:
```

lsb_release -a
cat /etc/issue

```
as indeed an install of 15.10 (wily) would have the 4.2 series:
You have searched for packages that names contain linux-image in suite(s) wily,
> 
linux-image-4.2.0-16-generic,


[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by jim_stevenson on 2015-11-12
Thanks for the very quick response.  Will follow your suggestions tomorrow when I get access to the PC.  Isb_release will at least verify I have installed the correct version.  Or not as the case may be.

---

### Post by jim_stevenson on 2015-11-13
Hi Bashing-Om

Did as you suggest and I am indeed using ver 15.10 and it is using kernel version 4.4 as it should.

I was looking in the efi/boot directory and the kernel and initrd files there are version 3.16.0.  

This is most likely to do with my boot setup in my machine and nothing to do with the Ubuntu installer as I first suspected.  I will investigate this further using terminal commands.  I am no longer familiar with these but it will not take me long to research them as I used Unix in the 70's.  If i remember correctly there are excellent string search commands with powerful search facilities and extensive support for wildcard characters etc.

Thanks a lot for your assistance and I hope the weather is better in Arkansas than it is in sunny Scotland today!

I consider this thread closed and will attempt to mark it so in the forum.

All the best  
Jim

---

### Post by Bashing-om on 2015-11-13
jim_stevenson; Great !

Making good progress. UEFI is something new we all have to learn .

As you progress and have questions or concerns, feel free to ask . We are here to help. Here there are no dumb questions, only the one(s) that are not asked.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-11-13
> The only unexpected aspect of the install was I expected  an EFI system  but actually was asked to provide an boot location as per an MBR disk.   This should not in my view have influenced the Linux kernel version but I  include this info in case it is relevant.

I am guessing. If we have an existing version of Ubuntu that was installed in EFi mode then we would get an efi boot partition with Linux boot files. If we then installed another version but in BIOS/legacy mode we would then have the old efi boot partition left in place with its boot files for the older version. The Linux 3.16 kernel would suggest 15.04. And then we get a strange Grub boot menu.

Regards.

---

