---
title: "virtualbox cd mount issue with toshiba recovery discs"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by Armadillo Kilr on 2007-09-22
yea ive looked through the forums and i might have missed it, but basically what the title says.

i have a toshiba satellite M105 and im trying to use virtualbox.

so i mount the cdrom with the recovery cd's, it asks me for my model number and it doesn't recognize it so it shuts down after a couple tries  saying "WRONG COMPUTER!".

is there a way around it or would i just be better off finding an XP.iso somewhere and booting from that. the model number is "M105-S3064". 

thanks in advance

AK:guitar:

---

### Post by cowkiller on 2007-09-23
> **Armadillo Kilr said:**
> yea ive looked through the forums and i might have missed it, but basically what the title says.

i have a toshiba satellite M105 and im trying to use virtualbox.

so i mount the cdrom with the recovery cd's, it asks me for my model number and it doesn't recognize it so it shuts down after a couple tries  saying "WRONG COMPUTER!".

is there a way around it or would i just be better off finding an XP.iso somewhere and booting from that. the model number is "M105-S3064". 

thanks in advance

AK:guitar:
I guess the "virtual computer" that you run under virtualbox has different specifications from your real computer, so the recovery software doesn't recognise it. Try to install first the virtualbox guest addons, but I think that the result will be the same. 
I'd make it directly installing XP on a different HDD partition and going on from there. If you install XP you'll lose your grub menu, so check out some way to solve that browsing the forums. There are easy ways to solve it. 
Good luck!

---

### Post by Armadillo Kilr on 2007-09-24
i ended up downloading winxp corporate and running that through virtualbox.

 the NEW problem that came up was that i couldn't use my keyboard in winxp corp ed. i guess some driver didnt come through or something. so i would have to restart manually to get back to ubuntu because the hotkey obviously didnt work. this is getting pretty irritating :confused:

---

