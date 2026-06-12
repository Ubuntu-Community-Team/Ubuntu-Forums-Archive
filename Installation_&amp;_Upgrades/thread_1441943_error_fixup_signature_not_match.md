---
title: "error: fixup signature not match"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by lefos on 2010-03-29
How do I solve this?

Details:
Using wubi, just installed 2 weeks ago did an upgrade and got a grub command line "sh:grub>" deal

I set the root of everything to my hard drive, and when I told it where the root.disk was located it says "error: fixup signature not match"

I am dual booting with windows 7

---

### Post by garymokha on 2010-04-10
I am having the same problem. Ubuntu was working fine earlier. Yesterday when i booted, it loaded to grub's bash like terminal.
I tried using this

>  sh:grub>insmod ntfs
> sh:grub>set root=(hd0,1)
> sh:grub>loopback loop0 /ubuntu/disks/root.disk
> sh:grub>set root=(loop0)
> sh:grub>linux /boot/vmlinuz-2.6.31-17-generic  root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
> sh:grub>initrd /boot/initrd.img-2.6.31-17-generic
> sh:grub>boot

but when i use the loopback in line 3 i get an error.
error: Fixup signature not match

i am using wubi..

---

