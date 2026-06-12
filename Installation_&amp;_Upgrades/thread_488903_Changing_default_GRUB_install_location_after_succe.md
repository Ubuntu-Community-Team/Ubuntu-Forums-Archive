---
title: "Changing default GRUB install location after successful install"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by Milamber_Cubed on 2007-06-30
Hi All,

I recently installed Fiesty on my MacBook Pro and by mistake chose (hd0) as the location for GRUB. Now I have managed to fix the settings by booting off the live CD and remounting the installed system and running "grub-install /dev/sda3" to get it installed on the correct partition. Everything is now fine and my booting works perfectly.

What I am worried about is what will happen if through installing some package (maybe a kernel update or even an update to the GRUB package) the system decides that GRUB needs to be re-installed. Will it see that the last place it was installed to was /dev/sda3 or will it remember the value chosen on install and use that?

Thanks for any pointers in the right direction.

Regards,

Milamber_Cubed

---

### Post by confused57 on 2007-06-30
> **Milamber_Cubed said:**
> Hi All,

I recently installed Fiesty on my MacBook Pro and by mistake chose (hd0) as the location for GRUB. Now I have managed to fix the settings by booting off the live CD and remounting the installed system and running "grub-install /dev/sda3" to get it installed on the correct partition. Everything is now fine and my booting works perfectly.

What I am worried about is what will happen if through installing some package (maybe a kernel update or even an update to the GRUB package) the system decides that GRUB needs to be re-installed. Will it see that the last place it was installed to was /dev/sda3 or will it remember the value chosen on install and use that?

Thanks for any pointers in the right direction.

Regards,

Milamber_Cubed
I don't think you have anything to worry about...update-grub is run when there is a kernel update, which shouldn't change any of your current menu.lst settings due to installing grub to the root partition.

---

### Post by Milamber_Cubed on 2007-07-01
I'm not worried about menu.lst changing - I am worried that the MBR of the drive will be overwritten instead of the boot sector of /dev/sda3 in the case of an update to the kernel or grub, because this is the location I chose when installing. If the MBR gets overwritten then my triple booting setup will get messed up. 

How does grub choose where to install itself after kernel/grub package updates, if at all?

---

### Post by Levander on 2007-07-01
Sounds like it's time for you to start digging through the grub documentation.  That's what most people do when they have problems issues with grub.  It's just something that runs, and no one uses often enough to remember answers to questions like that.

There might be someone to just tell you.  But, I'd start digging through the grub manual if I were you.

[http://www.gnu.org/software/grub/manual/html_node/index.html](http://www.gnu.org/software/grub/manual/html_node/index.html)

---

### Post by Milamber_Cubed on 2007-07-01
I've had a look through the man pages already and all of the commands require you to specify what device GRUB gets installed on. 

Based on that, I assumed that there is probably some kind of post-install script included in debs that will do all of this automatically. Sure enough there are post-install scripts if you unpack them, but can I figure out what the heck is going on in them? That would be a no. :p

That's why I'm asking here... maybe someone knows the answer already. Or so I hope :)

EDIT: Because this is part of the deb files that are pused out specifically for ubuntu, I am guessing that it's very distro sepcific. Probably why I havent been able to find anything very easily

---

### Post by Levander on 2007-07-01
I think the scripts that are run are part of the stand grub distribution.  grub-update is one of them.  Is that in the gnu manual?  I really don't think it's Ubuntu or Debian specific.

---

### Post by confused57 on 2007-07-01
> **Milamber_Cubed said:**
> I've had a look through the man pages already and all of the commands require you to specify what device GRUB gets installed on. 

Based on that, I assumed that there is probably some kind of post-install script included in debs that will do all of this automatically. Sure enough there are post-install scripts if you unpack them, but can I figure out what the heck is going on in them? That would be a no. :p

That's why I'm asking here... maybe someone knows the answer already. Or so I hope :)

EDIT: Because this is part of the deb files that are pused out specifically for ubuntu, I am guessing that it's very distro sepcific. Probably why I havent been able to find anything very easily
See the "Mbr" and "Grub" sections here:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

update-grub won't overwrite another bootloader on the mbr, even if you installed grub's IPL to the mbr when you installed Ubuntu, it will update the IPL you installed on the root partition...that's what I wasn't saying in my initial reply.

---

