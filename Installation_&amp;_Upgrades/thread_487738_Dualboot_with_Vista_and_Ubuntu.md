---
title: "Dualboot with Vista and Ubuntu?"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by Nitrius on 2007-06-29
Gonna give Ubuntu a new try i think, but i got some question about dualbooting.

I got one harddrive to use(250gb, with about 180gb free space).
Vista x64 is already installed, so i wonder how i should proceed to install Ubuntu successfully without destroying Vista.
Found this link: [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first) is that a good method to use?


Got some off topic question, if you can answers feel free to do so.
Should i got for x64 or x86 version of ubuntu? whats the pros and cons?
Also, there is other versions of ubunut, something called kubuntu i believe? whats the difference?


Thanks in advance =)

---

### Post by confused57 on 2007-06-29
> **Nitrius said:**
> Gonna give Ubuntu a new try i think, but i got some question about dualbooting.

I got one harddrive to use(250gb, with about 180gb free space).
Vista x64 is already installed, so i wonder how i should proceed to install Ubuntu successfully without destroying Vista.
Found this link: [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first) is that a good method to use?


Got some off topic question, if you can answers feel free to do so.
Should i got for x64 or x86 version of ubuntu? whats the pros and cons?
Also, there is other versions of ubunut, something called kubuntu i believe? whats the difference?


Thanks in advance =)
First of all, it would be best to resize your Vista partition using the Vista partitioner...resize, then see if you can boot Vista.  Then you can install Ubuntu on the unallocated space, you'll probably need to use manual partitioning, so that you can install grub to the root partition(should be an "Advanced" button you can click to designate installing grub to the root partition)...then you can use the Vista bootloader to boot Ubuntu:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

