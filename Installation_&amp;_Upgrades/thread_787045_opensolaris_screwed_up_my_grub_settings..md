---
title: "opensolaris screwed up my grub settings."
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by Schreck425 on 2008-05-08
I have a tri-booted PC now.  I just put opensolaris on the 3rd partition and the stupid OS blew away my grub settings.  I can't seem to even get to my other partitions to edit the new opensolaris grub menu.

I added this to it...
title Ubuntu
root (hd0,0)d
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=b-661784b5-8dbf-451b-b1a8-c1b1f375cb6a ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

I got this from online cuz I can't get back into my old grub menu file to copy and paste it in there.

Doing this gives me that Ubuntu option, but when I hit enter on it,  it takes me to the ubuntu startup screen and it gets stuck.  So I obviously have something wrong in the kernel line or initrd line.  

So I need help either with what I should put for the kernel, or how to access my other partitions that opensolaris is keeping me out of.

---

### Post by lemming465 on 2008-05-10
I'm assuming the trailing d on *root (hd0,0)d* is a typo, because I don't thik you want it.  My first guess based on your description is that the UUID value is slightly wrong; you could try replace the whole root= clause with *root=/dev/sda1* and see if that version does better.

Alternatively, depending on how much you love booting opensolaris (haven't tried it yet myself) you could boot a live Ubuntu CD in rescue mode and reinitialize the Ubuntu grub on the first partition.

---

