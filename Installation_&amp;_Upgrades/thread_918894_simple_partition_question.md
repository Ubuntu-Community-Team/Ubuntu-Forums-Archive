---
title: "simple partition question"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by tone33 on 2008-09-13
I've got a dual boot setup with vista/kubuntu and want to add another distro (gentoo) to the mix to make it a tri-boot.  I've maxed out my 4 primary partitions so i will have to use a logical partition for gentoo.  Can i do this?  Can a logical drive be a boot drive?

---

### Post by jpkotta on 2008-09-13
You have to kill one of your primaries to create the logical ones.  

You can have up to 4 primaries, and at most one can be and extended primary.  The extended partition can hold up to 15 (or 16?) logical partitions.  So pick the biggest primary and make the logicals from that.

Grub should be able to boot logical partitions.

I like to make a separate /boot partition, so grub (or me) doesn't get confused.

---

### Post by tone33 on 2008-09-13
i accidently double posted this and think i got my answer on the other post first.  But you mentioned something that caught my attention - using a boot partition?  Can you tell me a little bit about how this keeps things simple for you?  I'm coming up with a partition plan to multiboot to several windows and linux distros and this might be very helpful if i can understand the reasoning behind boot partitions.

---

### Post by jpkotta on 2008-09-14
It's about putting common things together.  Clearly we need one and only one grub configuration, so there can only be one /boot/grub/.  Might as well put all the kernels in that same /boot.  Then most automatic grub configuration tools will work just fine on each OS, because they can see all the kernels.  See also [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto).

---

### Post by tone33 on 2008-09-19
So I have my 300GB drive partitioned out like follows:

70GB Windows Server 08 and developer stuff (NTFS)
50GB Data Drive (NTFS)
10GB Ubuntu (EXT3)
15GB Gentoo (EXT3)
155GB Free for future partitions.

But from what you are saying i could have one partition that is...say 2GB as my boot partition, that will have grub for all my linux distros...  and my other windows bootloader as well (or a pointer to it anyway). I still install the distro of choice to its own root partition though.

---

