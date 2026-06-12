---
title: "Not loading the right kernel?!"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by ericus on 2008-05-19
Ok, I upgraded from 7.10 to Hardy Heron, and of I understand this correct my kernel version should be 2.6.24, right? uname -r shows me 2.6.22-14-generic, why is it so?

Any way to fix this?


EDIT: Additional info.

The new kernel can be found in /boot, but not in /boot/grub/menu.lst, so I added it manually:

> 
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=/dev/mapper/cryptroot ro 
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=/dev/mapper/cryptroot ro 
initrd		/initrd.img-2.6.22-14-generic

Unfortunaly it wont boot from that, stops at some "Attatched scsi blabla", just before I have to type in my LUKS passphrase.

---

### Post by zvacet on 2008-05-19
How many old kernels do you have?You can remove them in synaptic by searching for **linux-image** package.Delete one with lower number( you can keep Gutsy kernel just in case).After that 

```
sudo update-grub
```

---

### Post by ericus on 2008-05-19
Thanks for taking your time.
Two kernels, the one I'm using now and the new one.

I removed menu.lst and let update-grub make a new one. It looks like this:

> title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=/dev/mapper/cryptroot ro
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=/dev/mapper/cryptroot ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=/dev/mapper/cryptroot ro
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=/dev/mapper/cryptroot ro single
initrd		/initrd.img-2.6.22-14-generic

The 2.6.24-kernel stops loading at some lines about attatched scsi-disks or something, but the old one works, even though it now is a process bar when booting instead of just text scrolling by.

My disks are encrypted, and I need to enter a passphrase at every boot. I never get to that point with the new kernel.

---

### Post by nicminus on 2008-06-03
Did you ever fix this? After upgrading to Intrepid, I never get to the prompt for the encrypted root passphrase, it just sits there waiting for the crypted disk (2.6.24-16).

If I go back to my old kernel (2.6.24-14), it boots fine and prompts for my passphrase.

---

### Post by ericus on 2008-06-04
> **nicminus said:**
> Did you ever fix this? After upgrading to Intrepid, I never get to the prompt for the encrypted root passphrase, it just sits there waiting for the crypted disk (2.6.24-16).

If I go back to my old kernel (2.6.24-14), it boots fine and prompts for my passphrase.

No, I cant get this one fixed.
Someone must know the answer for this, please!

---

### Post by ericus on 2008-06-14
Anyone got any ideas?

---

