---
title: "Ubuntu / Win 8 Dual boot - issues with booting into GRUB, boot-repair gets stuck"
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by surreal9 on 2013-03-21
Hello,

I have a recently purchased windows 8 laptop, which apparently has "EFI". I managed to successfully get Ubuntu installed (through some wrestling), and all seemed to be going well, until I broke everything trying to install my nvidia drivers, so now I'm trying to repeat the procedure that had me up and running.. but with no success this time around.

Basically, originally what worked, was setting my bios to 'legacy' mode, installing ubuntu, then setting my bios to "UEFI", and running "boot-repair" off of my live cd. This would fix the "skips straight into win 8" problem I was having, and would get me to my nice GRUB boot menu to be able to choose Ubuntu. Unfortunately, while this worked perfectly the first time, I can't seem to get it to work a second time.

For some reason, boot-repair won't actually complete with this recent re-install. It always gets stuck towards the last part. IE it asks me to type in a series of commands, which I do, but afterwards when I guess it should wrap everything up it gets stuck on "Reinstalling grub.. this may require a few minutes" I've seen a couple other people with similar issues (ie [http://ubuntuforums.org/showthread.php?t=2098014](http://ubuntuforums.org/showthread.php?t=2098014) or [http://ubuntuforums.org/showthread.php?t=2127261](http://ubuntuforums.org/showthread.php?t=2127261) , but those are unresolved and I'm not even sure if we have the same underlying issue) I've tried with a fresh re-install of ubuntu, and windows even, but can't seem to get it to work like it did at first.

In any case, I've now run boot-repair again just to get the boot-info printed out, which can be viewed here: [http://paste.ubuntu.com/5634359/](http://paste.ubuntu.com/5634359/)

I'm not really sure why boot-repair originally worked, and now it won't. I have tried a little bit of poking around the 'advanced options', but nothing seems to work. All that happens is my computer just boots to win8 and seems to ignore GRUB.

Any suggestions? Thanks in advance!

Edit:

To clarify my approach, I would install ubuntu and use the  "somewhere else" option to set up my own partitions, and I basically  just created a /boot partition and then lumped everything else in a /  partition for simplicity sake. I don't have a swap partition, since I  have 12 gb's of RAM.

---

### Post by surreal9 on 2013-03-21
Ok.. I think I figured it out.. I had to make a second "EFI" partition, as I guess the original one is used by windows. When I re-installed (yet again), this time I created an additional EFI partition and told Ubuntu to install the boot loader to that partition (instead of the /boot partition as I had before). It still wouldn't boot at first, but at least boot-repair finally ran and successfully completed :) I'm going to reboot now to double check but I'm assuming it did it's job this time if it finished.. thanks for reading!


Edit: Nope, still skips GRUB and goes right to Win 8. This is the latest boot-repair paste output: [http://paste.ubuntu.com/5634655](http://paste.ubuntu.com/5634655)

---

### Post by oldfred on 2013-03-21
Delete sda10. OR at least use gparted and remove boot flag which will make it a data partition.
You can only have one efi partition per hard drive. All systems use the same efi partition with different folders for their boot code. Each folder is like a MBR in the old MBR booting.

There have been a few efi partitions that have some issue that appears as read only, which should not be possible. One solution was to backup files, delete that partition, and recreate it. But your system has Ubuntu folder in all three efi partitions. It looks like sda1 is not labeled as efi, and some systems have a recovery partition with efi files but is not labeled as efi. 

Since all systems boot from efi partition, you have to go into UEFI directly not thru Windows and choose which system you want to boot. I think it will just say ubuntu in UEFI menu.

Line 1024 in Boot-Repair shows some info from your UEFI.


BootOrder: 0001,2001 
Boot0000* EFI DVD/CDROM (MATSHITADVD-RAM UJ8A7AS) 
Boot0002* EFI DVD/CDROM (MATSHITADVD-RAM UJ8A7AS) 
Boot0001* ubuntu

That says ubuntu is a choice.

---

### Post by surreal9 on 2013-03-21
Thanks, in the end I've finally gotten a Lubuntu install up and running with an appropriate fix through boot-repair. Indeed I had to scrap creating an additional EFI partition, and simply select 'sda1' for the 'additional efi partition' option in boot-repair.

Things are finally looking up :) Thanks for your response oldfred, and for being a general helpful guy, from what I've seen in my searches on this issue :)

---

