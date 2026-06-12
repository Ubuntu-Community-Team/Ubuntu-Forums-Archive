---
title: "Trouble installing Ubuntu"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by Rockmanneo on 2008-08-06
I'm installing it on a formatted hddd, it'll be the only OS on the disk. So when I installed it, I told it to use the entire disk. Anyway, installation went without a hitch. It told me to reboot.

So I reboot, it tells me "GRUB is loading, Please wait", and then it crashes. It shows the flashing underscore at the top left of the screen, an "F" below it, with 2 green squares, and it locks up.

Does anyone know what the problem is?

---

### Post by tech9 on 2008-08-06
> **Rockmanneo said:**
> I'm installing it on a formatted hddd, it'll be the only OS on the disk. So when I installed it, I told it to use the entire disk. Anyway, installation went without a hitch. It told me to reboot.

So I reboot, it tells me "GRUB is loading, Please wait", and then it crashes. It shows the flashing underscore at the top left of the screen, an "F" below it, with 2 green squares, and it locks up.

Does anyone know what the problem is?

you could try repairing grub with supergrub disk...

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by raul_ on 2008-08-06
I have no idea, but maybe you could try reinstalling Grub (you can find the instructions in the forums).

Also, what version of Ubuntu are you using?

---

### Post by Rockmanneo on 2008-08-06
> **raul_ said:**
> I have no idea, but maybe you could try reinstalling Grub (you can find the instructions in the forums).

Also, what version of Ubuntu are you using?

The newest one, 8.04

---

### Post by Rockmanneo on 2008-08-06
Where should I put the boot loader? I have three options:

(hd0)
/dev/sda (This had my hdd listed under it)
/dev/sda1

---

### Post by wpshooter on 2008-08-06
Are you installing this from the LIVE CD version of Ubuntu ?

If so, then try installing it with the safe graphics mode option.

If that does not work then download, burn & try installing from the ALTERNATE (texted based) version of Ubunutu.

Also, I recommend that you use the manual parition option and make sure that you make a bootable /root partition, a /home partition and a /swap paritition.

Good luck.

---

