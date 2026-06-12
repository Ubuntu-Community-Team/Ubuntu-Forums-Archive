---
title: "Overwriting xandros installation"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by thered on 2007-11-13
Ok I have Ubuntu dual booting on my laptop -very  happy with it.  so much so that I'm thinking of installing it on my desktop which at present dual boots with xandros

I would like to install it(Ubuntu)  in the same space as my Xandros installation which at present dual boots with XP.

If I do an ubuntu install will it overwrite the boot manager presently in use and installed by xandros, still allowing me to dual boot with Windows?

Should I boot to windows repair and do a 'fixmbr' first?  Then install on xandros partition?

I'm a little wary 'cos last time messing I ended up without access to any OS at all and no coaxing could retrieve bootup -ended up re-installing everything, and I'm not sure whether the changeover is worth doing that again!

---

### Post by Triptol on 2007-11-13
Before you upgrade you might want to backup your home directory on some drive.

Ubuntu uses grub to boot. I guess Xandros does the same. In that case you could also make a backup of the file /etc/grub/menu.lst (or /etc/grub/grub.conf). 

Normally Ubuntu will detect your Windows installation and make sure you can still boot to it. If, for some reason, it doesn't you will still be able to boot into Ubuntu and change your /etc/grub/menu.lst file to add a boot item for Windows. A template for a menu item is already in that file so all you need to know is where your Windows partition is located (in 90% of all installations the default settings will be ok).

So if nothing strange happens, you will be fine. If not perfect, you can still fix it. Of course you could still make mistakes (format the wrong drive for instance) or something terrible could happen (earthquakes????)

---

### Post by thered on 2007-11-13
Thanks Triptol.

I'll give it a go tomorrow or Thursday.  See you on the other side :)

---

### Post by thered on 2007-11-16
Seems xandros uses lilo to boot from... re-assessing:)

---

### Post by thered on 2007-11-16
OK, up and running in Ubuntu.

Did a fixmbr with windoze boot disc and then fixboot using Hiren boot utilities.

Booted to Ubuntu live and used partition manager to delete partition.

Rest was straight forward.:)

---

