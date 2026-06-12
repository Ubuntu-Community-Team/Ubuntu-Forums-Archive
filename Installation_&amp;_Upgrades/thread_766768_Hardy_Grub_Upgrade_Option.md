---
title: "Hardy Grub Upgrade Option"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by c007c on 2008-04-25
Hello,
I have 2 questions about the 7.10 to 8.04 upgrade.

1) I was prompted with a question about using the menu.lst from 7.10, or create a new one. I chose keep the old. I changed for the new kernel, boots ok, got rid of the PCI boot errors I was expereincing in 7.10, but am wondering about the boot options. Are they the same as the 7.10 boot options? Here's the menu.lst edit for 8.04:

title		[COLOR="Red"]Ubuntu 8.04, kernel 2.6.24-16-generic[/COLOR]
root		(hd0,4)
kernel		/boot/[COLOR="Red"]vmlinuz-2.6.24-16-generic[/COLOR] root=UUID=75e0f98e-4500-4e3b-9799-7baaaa889924 ro quiet splash
initrd		/boot/[COLOR="Red"]initrd.img-2.6.24-16-generic[/COLOR]
quiet

What about root=UUID=75e0f98e-4500-4e3b-9799-7baaaa889924 ro quiet splash, does any of that change with 8.04?

2) The Software Sources GUI - Third Party - What the...? Totally different, has the 7.10 paths and and only a couple of Hardy Paths. Looks like some could be integrated into the main options tab? I still can't run a full update using the Update Manager since the upgrade, the with all the load, maybe that will change once I do?

Thanks!

---

