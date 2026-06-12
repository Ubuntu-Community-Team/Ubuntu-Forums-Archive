---
title: "GRUB fails to install on sata disk"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by nonutopia on 2005-08-14
Hello.

Im trying to reinstall ubuntu on a Maxtor Diamondmax 10 sata disk on a asus a8n-sli premium using the nvidia sata controller. Install runs nicely untill i get to the grub part. Somehow it wont install grub to the mbr.

When i chroot my /target partition and try it manually with grub-install /dev/sda it keeps saying 'The file /boot/grub/stage1 not read correctly'

I tryed disabling my pata disk in the bios but no luck. Still the same error.

So is there some grub guru who can help me with this one cause i seem to be lost. And my knowledge of the grub shell is not a lot. 

Some details:

I dont have a /boot partition
my root partition is /dev/sda6
motherboard is an Asus a8n-sli premium
sata disk Maxtor Diamondmax 10
pata disk (disabled)  Maxtor Diamondmax 10
my /etc/fstab file seems fine.

Please help. I really miss my primairy operating system at the moment.
I could try lilo or try reinstalling ubuntu on my pata disk but I really want it to work like this. (This is the setup i usually use and i like standards)
Grub worked fine on my pata disk.

Thanks in advance.

ps. Ofcourse im willing to file a bug report on this one if needed. But first i wanna know if its fixable.

edit: This is what happends when trying it with the grub shell:

$ root (hd0,5)
Filesystem type unknown, partition type 0xe

So no wonder it cant find the stage1 file. But the partition seems fine.

---

### Post by nonutopia on 2005-08-15
Ok i solved the problem by using a /boot partitiion as the first on on the boot harddisk. 
This solved the strange stage1 not read correctly problem. 

Only problem i got this time was that the ubuntu installer mistaked my hd0 (wich is think is the bootable disk at grub startup) for hd1. Also it automatically installed itself to the MBR of the wrong disk.
So edited the device.map and installed grub manually. It works like a charm yet again.

So should i bug report this anyway? I'm no grub expert but i think it behaved a bit weird on me. Also maybe the ubuntu installer should ask what the bootable disk is in a configuration like this cause it seems logic that a primary master ide disk is the bootable disk. But together with a sata disk you just cant tell wich one is the bootable disk and should be called hd0.

Correct me if im wrong just a suggestion.

---

