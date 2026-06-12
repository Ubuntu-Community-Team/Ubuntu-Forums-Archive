---
title: "Upstart troubles"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by ANTDx1 on 2006-10-30
I have recently 'upgraded' to Edgy.  upgrade, in this case, means watch some text go by and then fix the broken gui.  I've gotten everything that worked in 6.06 to work except the start.  During boot, rather than displaying a nice splash with text telling me what was going on, it displays a broken, black-and-white Ubuntu logo, with a bar, also in black-and-white, that seems to work properly, other than the fact that the colors are way off.  In addition, the text that showed up before now doesn't show up.  I assume that this is simply a problem with the black-on-black that is being displayed due to the lack of color on start.  Does anyone know how to fix this?  I know it doesn't seem like much of an issue, but I'd rather show all my friends the beautiful Ubuntu artwork along with the new quick boot time, rather than a half-working upstart.  Thanks for your help

---

### Post by rebird242 on 2006-11-23
I have that same problem.

---

### Post by xenoalien on 2006-11-23
I had this problem when I had Ubuntu 6.10 64bit version installed. But the 32bit OS was fine.

---

### Post by keybuk on 2006-11-23
> **ANTDx1 said:**
> I have recently 'upgraded' to Edgy.  upgrade, in this case, means watch some text go by and then fix the broken gui.  I've gotten everything that worked in 6.06 to work except the start.  During boot, rather than displaying a nice splash with text telling me what was going on, it displays a broken, black-and-white Ubuntu logo, with a bar, also in black-and-white, that seems to work properly, other than the fact that the colors are way off.  In addition, the text that showed up before now doesn't show up.  I assume that this is simply a problem with the black-on-black that is being displayed due to the lack of color on start.  Does anyone know how to fix this?  I know it doesn't seem like much of an issue, but I'd rather show all my friends the beautiful Ubuntu artwork along with the new quick boot time, rather than a half-working upstart.  Thanks for your help

This isn't caused by upstart, but by changes to usplash.

usplash was improved to offer high-resolution, high-colour-depth graphics on i386; unfortunately this didn't work out on AMD64, and there wasn't time to produce anything other than the B&W artwork you see.

---

### Post by m4dd0c on 2006-11-29
> **keybuk said:**
> This isn't caused by upstart, but by changes to usplash.

usplash was improved to offer high-resolution, high-colour-depth graphics on i386; unfortunately this didn't work out on AMD64, and there wasn't time to produce anything other than the B&W artwork you see.

Can this be solved somehow? Looks really ugly.

---

