---
title: "686 kernel panic?"
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by washman on 2005-11-10
Hi all,

I got another problem, when I upgraded hoary to breezy, both 686 and 386 kernel were intalled, but only 386 works. When I tried to boot into 686, the following error occured:
[PHP]
RAMDISK: ran out of compressed data
invalid compressed format (err=1)
kernel panic -not syncing: VFS: Unable to mount root fs on unknown-block(0,0)[/PHP]

Then the system was deadlocked. 

I think the 686 kernel itself was complied correctly, but the link to initrd.img and vmlunz were written to /root, because the /boot has no free space. Does that matter??

Can anybody help me out? Many thanks.

---

### Post by washman on 2005-11-12
Can anyone tell me how to reinstall the 686 kernel?

---

### Post by tseliot on 2005-11-12
[QUOTE=washman]Can anyone tell me how to reinstall the 686 kernel?[/QUOTE]

Try this:

[QUOTE=]sudo apt-get install linux-686[/QUOTE]

And if it says it is already installed (and it doesn't want to install it):

[QUOTE=]sudo apt-get install --reinstall linux-686[/QUOTE]

---

### Post by bargol on 2005-11-14
Hi,

i have a similar problem: installing new breezy from cdrom terminates with the exact failure from above.
Options like noapic nofb nolapic acpi=off pci=noacpi have not helped.

bargol

---

### Post by Original Brownster on 2005-11-14
[QUOTE=washman]
I think the 686 kernel itself was complied correctly, but the link to initrd.img and vmlunz were written to /root, because the /boot has no free space. Does that matter??
[/QUOTE]

Hi,
boot using the 386 image if necessary and check the grub conf points correctly to the initrd.img and vmlinuz image. /boot/grub/menu.1st
You say it wrote a link to /root, do you mean a symbolic link in /boot/ points to the actual files in /root ? 

Bit of a bugger if your boot partition is too small, it's possible to fix but might be easier to remove some of the old images if you do not use them.

---

