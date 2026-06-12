---
title: "LUKS-encrypted root LVM volume won't take password after kernel upgrade (Hardy)"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by Vengeance on 2008-06-20
Running Hardy (kubuntu), using the encrypted root-volume from the alternate install disk.
Kernel 2.6.24-16 (the one I installed with in April) works fine. Takes the password, mounts, boots.
Upgrades -17, -18, and -19, it gets as far as asking for the password...when I enter it, it just blinks and asks again, until I've entered it enough times for it to decide I'm trying to break in.
The /boot/grub/menu.lst has the same options after each kernel entry (root=/dev/mapper/anubis-root ro quiet splash).
The /etc/crypttab has the right UUID and device.
I've been searching the forums (ubuntu, kubuntu, debian, google, luks) for 3 days and gotten nowhere.
Can someone give me a clue?

Thank you
Vengeance

---

### Post by Vengeance on 2008-06-27
Should I assume from the deafening silence that no one can help me, and I should do a good backup and reinstall without the crypto?

---

