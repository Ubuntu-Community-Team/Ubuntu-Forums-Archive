---
title: "iso-scan parameter for grub2"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by sapeurcamembert on 2011-04-20
Hello,

I am trying to boot iso distrib from the command line (using c at the grub2 menu) and iso files are not located on the parttion where grub2 is installed. I have a separate partition. sda1 for system, sda3 for /home and sda2 for swap.

sda3 contains iso images

How can I specify a path for iso file (iso-scan/filename=.....
if the file is not on the system disk (sda1 in this situation).

I did (hd1,3)/filename.iso etc do not work

And of course I got the message that iso file is not found on sr0 being back at Busybox...

Any idea somebody ?

---

### Post by drs305 on 2011-04-20
Take a look at the "ISO" link in my signature line. It gives examples of menuentries for booting ISO images. The command line entries would be similar.

---

### Post by sapeurcamembert on 2011-04-20
Thank you for your quick reply. If I posted something is because I did already provide an iso file location WITHOUT the leading /home and I did read your faq or howto...

Commands are

loopback loop (hd0,3)/am/Documents/iso/myiso.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=(hd0,3)/am/Documents/iso/myiso.iso noprompt noeject
initrd (loop)/casper/vmlinuz
boot

---

### Post by drs305 on 2011-04-20
> **sapeurcamembert said:**
> 
loopback loop (hd0,3)/am/Documents/iso/myiso.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=(hd0,3)/am/Documents/iso/myiso.iso noprompt noeject
initrd (loop)/casper/[B][COLOR="DarkRed"]vmlinuz
[/COLOR][/B]boot

Was the above highlighted text a typo? (... initrd (loop)/casper/initrd.lz )
Also note some initrd's are .lz and earlier ones are .gz

Is the ISO file in */am/Documents/iso/* of the sda3 partition?

The iso-scan/filename= should not include the partition, just the path/filename:
> linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/am/Documents/iso/myiso.iso noprompt noeject
initrd (loop)/casper/initrd.lz

I've not mounted from the command line. If you tell me what iso file you are trying to load I can try it myself. The initrd location and name can vary depending on the ISO.

---

