---
title: "Strange setup problem: Install in extended partition with grub 1"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by dake22 on 2010-12-05
Hi mates, I'd like to ask you about a problem I have with my laptop. I had Windows 7 and Chakra linux (Arch Linux) installed, and Grub 1 as boot manager. Today I've decided to install Linux Mint XFCE in order to have a triple-boot, but keeping Grub 1 as boot manager, so I haven't installed LM's grub 2. 

I've installed LM in an **extended partition**, and the filesystem is **ext4**.


**Here I put the error I get when I try to boot the grub entry I created:**
-------------

Booting "Linux Mint XFCE"

root (hd1,4)
Filesystem type is ext2fs, partition type 0x83
chainloader +1

Error 13: Invalid or unsupported executable format

Press any key to continue...

-------------

**And here I put my menu.lst:**

default 0
timeout 5
color light-blue/black light-cyan/blue

title Chakra GNU/Linux
root (hd0,0)
kernel /boot/vmlinuz26 resume=/dev/disk/by-uuid/521ea6e2-0d32-4703-90e4-2d0b613e20e3 root=/dev/disk/by-uuid/3802997b-754f-46cf-942f-1a6f6da66f57 ro
initrd /boot/kernel26.img

title Chakra GNU/Linux Fallback
root (hd0,0)
kernel /boot/vmlinuz26 resume=/dev/disk/by-uuid/521ea6e2-0d32-4703-90e4-2d0b613e20e3 root=/dev/disk/by-uuid/3802997b-754f-46cf-942f-1a6f6da66f57 ro
initrd /boot/kernel26-fallback.img

title Linux Mint XFCE
root (hd0,4)
chainloader +1

title Windows 7
root (hd0,2)
chainloader +1

-----------

I don't exactly know if the problem is because I've installed LM in an extended partition, or because the entry I've added is not correct. If somebody could help me I would appreciate it very much.


Thanks in advance.

---

### Post by ronparent on 2010-12-05
LinuxMint isn't booted by chainloading. You need to use a command set similar to that used for Chakra GNU/Linux (with the correct uuid for the Mint partition with correct the vmlinuz and kernel lines as well).

---

### Post by dake22 on 2010-12-05
Here I got the UUID of the sda5 partition where LinuxMint is installed, I used "sudo blkid"

/dev/sda5: UUID="3eed4109-79ac-4510-85d2-cc123f499619" TYPE="ext4" 

I've found that initrd.img and vmlinuz are "boot/initrd.img-2.6.32-21-generic" and "boot/vmlinuz-2.6.32-21-generic"

I tried to "assemble" the entry and I got this:

title Linux Mint XFCE
root (hd0,4)
kernel boot/vmlinuz-2.6.32-21-generic [COLOR="Red"]resume=/dev/disk/by-uuid/521ea6e2-0d32-4703-90e4-2d0b613e20e3[/COLOR] root=/dev/disk/by-uuid/3eed4109-79ac-4510-85d2-cc123f499619 ro
initrd boot/initrd.img-2.6.32-21-generic

The parameters in red are just copied from Chakra's entry, I don't exactly know what should I put here.

Would this be right?


**EDIT: Now I'm getting a different error:**

Error 1: filename must be either an absolute pathname or blocklist

Press any key to continue...


Any idea?

---

### Post by ronparent on 2010-12-05
> kernel boot/vmlinuz-2.6.32-21-generic resume=/dev/disk/by-uuid/521ea6e2-0d32-4703-90e4-2d0b613e20e3 root=/dev/disk/by-uuid/3eed4109-79ac-4510-85d2-cc123f499619 ro
initrd boot/initrd.img-2.6.32-21-generic

Try adding a '/' in front of boot (ie /boot).

I think you are on the right track. Good luck.

---

### Post by dake22 on 2010-12-07
Thanks, it worked, "/"'s were lacking in the path.

---

