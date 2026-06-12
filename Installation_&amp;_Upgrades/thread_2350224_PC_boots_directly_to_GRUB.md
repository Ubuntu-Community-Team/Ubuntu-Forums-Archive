---
title: "PC boots directly to GRUB"
date: 2017-01-22
forum: Installation &amp; Upgrades
---

### Post by daniel-clement on 2017-01-22
Hello,


My daughter came back this WE her PC only showing GRUB on startup.


It's a Dell laptop with Ubuntu (14.04) preinstalled. Le trouble happened after a forced reboot.


I could try some GRUB commands GRUB (results below--not what I expected). 


Also, I could start from an old USB bootable key (with 12.04). It doesn't look good, because I don't see the main partition (460 Go) which Gparted shows "unallocated". I can only see "ESP" (21 Mo) and "OS" (3 Go).


I still hope that I won't have to reinstall, but I could use some advice, as I'm not much of a GRUB expert.


Thanks in advance - best regards, Daniel
--------
(GRUB commands)
--------
```
ls (hd0,1)
(hd0,1): Filesystem is fat
ls (hd0,1)/
efi/ en-us/
ls (hd0,1)/efi
./ ../ Boot/ Microsoft/ ubuntu/
ls (hd0,1)/efi/ubuntu
./ ../ shimx64.efi grubx64.efi MokManager.efi grub.cfg
ls (hd0,1)/efi/Boot
./ ../ en-us/ bootx64.efi
cat (hd0,1)/efi/ubuntu/grub.cfg
search.fs_uuid 3d542f27-d5be-4f35-80ae-39fa72c802be root hd0,gpt3
set prefix=($root)'boot/grub'
configfile $prefix/grub.cfg
```

---

### Post by yancek on 2017-01-22
The computer is using the newer EFI system to boot but you will need to post more detailed information.  The best thing to do is to use another computer if the one in question can't boot.  You can download and burn boot repair to a CD and boot the CD.  When it boots, select the option to Create BootInfo Summary and post a link to the output here.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by daniel-clement on 2017-01-22
Thanks Yancek for replying so quickly. 
I'm sure this PC is EFI capable, but I had a look into the BIOS settings and everything appears set to "legacy boot".
Is there anything useful I could post before trying Boot-Repair? I'm downloading it right now, and I'll try it ASAP (from an USB stick, since this PC has no CD drive) and report here. BR, Daniel

---

### Post by yancek on 2017-01-22
> Is there anything useful I could post before trying Boot-Repair? 

Not really, other than reading the link above.  One of the major problems I've seen people with EFI machines do is have windows EFI and Ubuntu Legacy.  It it's set to legacy then both systems need to be installed legacy and you should have no EFI partition.  You could check that from the Ubuntu media in gparted.

---

### Post by daniel-clement on 2017-01-23
I was able to run Boot-Repair (but only from a Ubuntu live session - "2nd option" from [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)).

Anyhow, I had no success with the "recommended repair" choice. Same as before, PC boots directly to GRUB.

So before risking any advanced option in Boot-Repair, I'm linking to the boot info here:

[URL="http://paste.ubuntu.com/23852271/"]http://paste.ubuntu.com/23852271/
[/URL]
I don't understand every line of it, but I don't see any trace of the largest (460 Gb) partition :(

---

### Post by oldfred on 2017-01-23
It looks like to me that you put the installer live version onto the hard drive in effect erasing it.
Hope you have good backups. 

You show two FAT32 partitions, one as ESP - efi system partition and another with some files typically in the installer including more .efi boot files.
Never seen /factory/grubx64.efi, so is that some repair ISO? Or it could be from Dell as the recovery partition?

---

### Post by daniel-clement on 2017-01-23
> **oldfred said:**
> It looks like to me that you put the installer live version onto the hard drive in effect erasing it.
Well, I can't rule out a bad move, but I'm fairly sure my daughter brought back her PC to me as it is now. Maybe she tried to repair it herself, or with a friend...
>  Hope you have good backups. 
*She* has good backups-- at least she told me so!
>  You show two FAT32 partitions, one as ESP - efi system partition and another with some files typically in the installer including more .efi boot files.
Never seen /factory/grubx64.efi, so is that some repair ISO? Or it could be from Dell as the recovery partition?
You're probably right: the HD is partitioned as it came from Dell.

So... I'm preparing to reinstall... But in this case I think I'd better wipe the existing partitioning scheme, and have 2 separate partitions for "/" and "/home".

---

### Post by oldfred on 2017-01-23
Dell has its own drivers in Sputnik, but those often are included in the next release of kernel & support drivers in Linux.

If that is a Dell recovery partition I might make sure it is backed up.

Does latest live installer work ok in live mode?

---

### Post by daniel-clement on 2017-01-23
> **oldfred said:**
> Dell has its own drivers in Sputnik, but those often are included in the next release of kernel & support drivers in Linux.
I think "Sputnik" is for Dell XPS13, which is not the case--it's a very basic Inspiron 15, bought with Linux at a bargain price.
> If that is a Dell recovery partition I might make sure it is backed up.
Why not? That won't eat up much disk space. (However, my wife does have an XPS13 "Sputnik". It came with 12.04 installed. When I switched to 14.04, I wiped everything and we never had a problem.)
> Does latest live installer work ok in live mode?
Just everything seems to work OK in live mode, except that the WiFi card is not recognized. But then, the USB key I used is pretty (12.04), and of course I won't use for reinstalling. I'd bet that a recent Ubuntu will detect the WiFi card without problem-- I just didn't have time to try so far.

---

