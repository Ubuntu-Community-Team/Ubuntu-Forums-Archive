---
title: "grub Error 15 - root (hdX,Y)"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by DannyW on 2008-06-20
I just installed Ubuntu 8.04 from the alternate CD. When I selected to boot Ubuntu from grub I got Error 15: File not found.

I pressed e to edit the boot options and then e again to edit the option root (hd4,0). I changed it to (hd0,0) at a guess and ubuntu booted fine.

Now I'm not sure why (hd0,0) works. I have /boot on sde1 which, correct me if I'm wrong, is (hd4,0).

(hd0,0) means sda1 but this drive is just part of a raid array.

So, all in all, slightly confused. I can get it to work by changing to (hd0,0), but I'd just like to know why I have to do this (especially since the install CD set it to (hd4,0)).

Thanks

Danny

---

### Post by drsox1899 on 2008-06-20
> **DannyW said:**
> I just installed Ubuntu 8.04 from the alternate CD. When I selected to boot Ubuntu from grub I got Error 15: File not found.

I pressed e to edit the boot options and then e again to edit the option root (hd4,0). I changed it to (hd0,0) at a guess and ubuntu booted fine.

Now I'm not sure why (hd0,0) works. I have /boot on sde1 which, correct me if I'm wrong, is (hd4,0).

(hd0,0) means sda1 but this drive is just part of a raid array.

So, all in all, slightly confused. I can get it to work by changing to (hd0,0), but I'd just like to know why I have to do this (especially since the install CD set it to (hd4,0)).

Thanks

Danny

Exactly so.  I had the same and looked at all the posts on Grub errors.  Zippo effect.  Then a searched on Grub AND RAID.  Bingo.

This works.

Should be in the sticky section of any RAID forum

Thanks

PS I have a 3ware 8506-4LP with 4 WD drives.

---

### Post by drsox1899 on 2008-06-20
However, it doesn't solve the problem as the change doesn't seem to stick !  I unplugged/replugged a lead or two and the same problem !


UPDATE :

I unplugged my RAID card and reinstalled 8.04 server - installed with grub on root (hd0,0)

Plugged RAID card in and rebooted - grub unchanged !  Rebooted a few times, no problems ??

Must be the effect of the RAID card at time of initial install/setup ?

---

