---
title: "How do I save the default grub boot settings?"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by Brian Kendig on 2010-06-27
I just installed Ubuntu Server 10.04. When I reboot, it stops at a "grub>" prompt. I figured out that I can continue booting by entering these four commants:

set root=(hd0,1)
linux /boot/vmlinuz-2.6.32-21-generic-pae root=/dev/sda1 ro
initrd /boot/initrd.img-2.6.32-21-generic-pae
boot

I can't figure out, however, how to save these as the default so that the machine can boot without someone present to enter these commands. Running "grub-set-default" tells me "entry not specified." I don't see anywhere in /etc/default/grub that looks relevant.

How do I save my default grub settings?

---

### Post by darkod on 2010-06-27
If it stops at grub> prompt it seems you have some problem. That's why it's not booting on its own.
The easiest to try is updating the grub2 main config file, grub.cfg. Boot with the manual method and then execute:

sudo update-grub

See if it boots automatically after that.

---

### Post by Brian Kendig on 2010-06-27
Looks like update-grub did it! Thank you very much!

Any idea why the installer might not have done this on its own? I even tried booting from the CD again and doing a "repair" on the new installation, setting up grub again, and that still hadn't worked for me.

---

