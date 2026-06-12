---
title: "Adding RAID0 XP install to GRUB?"
date: 2006-04-12
forum: Installation &amp; Upgrades
---

### Post by SFalcon on 2006-04-12
My XP install crapped out and I decided instead of fixing it right away, I'd install ubuntu on a spare hdd I had and do a total immersion type thing for a few weeks.  So far so good.  However, I have now repaired the XP install but would still like to dualboot.  Here's the situation:

XP: installed on a 2x80GB S-ATA RAID0 array
UBUNTU: installed on a 120GB IDE HDD

When I installed Ubuntu, the installer did not recognize the RAID volume, and grub was installed to the 120GB IDE HDD.  Powering on the computer boots to GRUB and subsequently Ubuntu, no issues.  Disabling the 120GB HDD in the BIOS and restarting boots to the XP RAID0, no issues.

How can I set it up so that the XP install can be picked from the GRUB menu so that I don't have to disable the 120GB HDD everytime I want to boot to windows??

Thanks in advance for any help and I apologize if this is in the wrong section.  If I didn't provide enough information please let me know.

---

### Post by SFalcon on 2006-04-12
Added this to /boot/grub/menu.lst and it's working for now.

```

title Windows XP
root (hd1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
savedefault
boot

```

---

