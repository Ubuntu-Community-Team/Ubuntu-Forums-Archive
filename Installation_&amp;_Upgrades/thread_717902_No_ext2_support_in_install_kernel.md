---
title: "No ext2 support in install kernel???"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by drachs on 2008-03-07
I can't install off of CDROM drive because I don't have access to a SATA CDROM and the IDE controllers on the motherboard I'm using don't support linux.

I've copied the install over to a flash chip,made it bootable using the install kernel and initrd image and booted the unit off the flash chip using a usb compaq flash reader.

Unit boots fine, can't "Detect the cdrom drive".   Flash chip is working fine and available as sdc1.   Can't mount the flashchip, so I cat /proc/filesystems and there's no ext2 support???  As a matter of fact, there isn't support for anything other than cramfs and isofs.   

That is pretty frustrating, I mean, who saves space on a CDROM by stripping ext2 support out of the kernel?"  I tried the workstation kernel too but no luck.

Are there any options here other than cracking open the initrd image and putting the modules in there?

---

### Post by ssj3strife on 2008-03-08
Have you tried doing a network install? I don't remember how it works off the top of my head, but I have done it before so I know it's possible. As long as you can get the kernel and initrd to boot (which it doesn't sound like you're having a problem with), you should be in business. I'm sure a quick google search will turn up a couple of good resources for you.

I *think* how it worked was you booted the alternate install kernel and initrd to a bootable location, and then when the system boots, it magically downloads everything else it needs. Anyways, good luck!

---

