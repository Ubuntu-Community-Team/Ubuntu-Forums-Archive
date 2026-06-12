---
title: "grub: swap /dev/sda and /dev/sdb"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by lo.j on 2012-05-05
hi all.

i have ubuntu installed on /dev/sda3 and i installed debian on /dev/sda2 but when i boot into the new debian installation the df command says it has been mounted as /dev/sdb2.

i searched everywhere, edited my /boot/grub/device.map (to put my main disk as the first i the list), did many chroot, grub-install (**/dev/sda or /dev/sdb?**) and update-grub but the problem persists.

probably i miss something...

could anyone spend some words on this?
thanks very much.

---

### Post by dino99 on 2012-05-05
how many hdd/sdd are installed on this system ? The swapping issue is due to the hdd bios boot order. But i suppose your swap is a separate partition shared with both OS.

i agree that is confusing, but there is no much to worry about anyway, you only need to know about it.

---

### Post by lo.j on 2012-05-05
well, with the **swap** term i meant invert... :)

i have many hard disks but, every time i did a dual boot, the order has always been the right one, the bios one... i don't know the reason why this time it is all messed up...

is it possible to fix it?

---

### Post by darkod on 2012-05-05
If it works fine, there doesn't seem to be anything to fix. It seems like only debian is calling it sdb2 while in ubuntu and grub it's sda2.

---

### Post by lo.j on 2012-05-05
> **darkod said:**
> If it works fine, there doesn't seem to be anything to fix. It seems like only debian is calling it sdb2 while in ubuntu and grub it's sda2.

and it's fine.
but, since i guess that with linux is possible, there's nothing wrong in trying to achieve it. ;)

i found [these suggestions]("http://ghantoos.org/2012/01/29/debian-restore-grub-on-sdab-using-grub-mkdevicemap-and-grub-install/") but they didn't seem to work as expected.

i'm just looking for anyone who'd like to discuss about this procedure. thanks.

---

### Post by VMC on 2012-05-05
That usually happens when the share the same UUID. Run bootinfoscript (see my blue link) so we can see the boot info.

---

### Post by lo.j on 2012-05-05
great script, it scans almost everything!

some extra info:
let's say i got the normal disks order booting ubuntu (and all the others installations i remember). with debian sda becomes sdb (and so on) and the sda position is taken by the last sdg.

:-k ...i probably have the disk that debian "prepends" on another motherboard controller (the main one is a 6 entries) but this should not be relevant since the order is set by the bios, isn't it?

---

### Post by VMC on 2012-05-06
I don't see an sdb2, but I do see you have raid installed. Is that software or hardware? I know next to nothing about raid, but as previous mention, its most likely your BIOS settings - sda2 becomes sdb2 and visa versa.

---

### Post by dino99 on 2012-05-06
there are two orders:

- the real one, which is identified by: primary-main, primary-slave, secondary-main, etc while booting, its the phisical order

- the bios order: there it is a user choice order, and it can be different of the real one.

But , like in your case, things can be more complicated, due to using raid, llvm, etc

---

