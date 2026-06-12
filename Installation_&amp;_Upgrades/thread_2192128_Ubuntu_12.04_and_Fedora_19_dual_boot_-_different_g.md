---
title: "Ubuntu 12.04 and Fedora 19 dual boot - different grub versions"
date: 2013-12-06
forum: Installation &amp; Upgrades
---

### Post by kyozo on 2013-12-06
Hi,

I have a dual boot with Ubuntu 12.04 LTS (long time favorite) - currently running on kernel 3.2.0.55-generic-pae and Fedora 19 running with a much newer kernel 3.11.x and is 64-bit. It's running on old hardware, so no UEFI problems
These 2 systems use different versions of grub - both grub2 from what I can understand - I don't remember, but my ubuntu might be an upgrade from a previous ubuntu system.
Ubuntu 12.04 uses Grub 1.99-21ubuntu3.10'
Fedora 19 uses Grub 2.00

This causes some issues when I run ```
sudo grub-mkconfig
``` in ubuntu such as this ```
dpkg: warning: version '3.11.9-200.fc19.x86_64' has bad syntax: invalid character in revision number

```
This also causes issues when trying to update the kernels in Ubuntu, since the update process regenerates the grub-config, hence I cannot boot Ubuntu with the new kernels.

So I thought I might resolve this by upgrading Grub on my Ubuntu box, but I cannot find out how, except I found a post asking me to compile Grub from source, and I'm not very confident in that.

I have a lot more issues about generating the right menu entries and so on, but I will try to figure those out when I can run grub-mkconfig without issues from my ubuntu box.

Thanks for your help.

Cheers

Heine

---

### Post by fantab on 2013-12-06
Different Grub versions on different distros don't really matter. Only ONE Grub will be in command. If you installed fedora in its default then you will have Grub 2.0 from Fedora in command. 
Which Grub is in command, Ubuntu-grub or Fedora-grub?

Shouldn't that command in Fedora you are running be:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
OR
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
```?

---

### Post by oldfred on 2013-12-06
Did you create just one /boot partition? That would lead to the type of errors you have. 
Better not to have any /boot, but Fedora usually installs with /boot and LVM.
Ubuntu would not need the separate /boot and then each is separate. 
But you still have to decide which grub is in MBR as default boot. Ubuntu may need lvm2 driver to see Fedora correctly.

---

