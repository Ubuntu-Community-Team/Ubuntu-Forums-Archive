---
title: "Updated Kubuntu and now X wont start."
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2009-09-26
Had a bunch of updates for Kubuntu including the new Kernel, reboot and now X doesnt load. Just boots into Terminal. Anyone else get the same?

---

### Post by tghe-retford on 2009-09-26
> **Slug71 said:**
> Had a bunch of updates for Kubuntu including the new Kernel, reboot and now X doesnt load. Just boots into Terminal. Anyone else get the same?
Yep, though I think this is a known fault:

[https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/437067](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/437067)

Got worse for me, the first time I got to the desktop, my soundcard and digital TV card would not work either. Thankfully they do now.

---

### Post by ElVirolo on 2009-09-26
I can confirm this. X does start with "startx", but then it automatically boots to GNOME (I have both DE's installed).

---

### Post by tghe-retford on 2009-09-26
> **ElVirolo said:**
> I can confirm this. X does start with "startx", but then it automatically boots to GNOME (I have both DE's installed).
I found that 'startx' causes the sound and DVB devices to not work on my computer.

I had to 'sudo start kdm' and then 'sudo kdm' (because I only use KDM and KDE) to get the desktop to work and get devices to work again.

---

### Post by Slug71 on 2009-09-26
```
startx
``` worked here, i dont think the sound worked for me either though but at least im in. :)

Thanks.

---

### Post by ElVirolo on 2009-09-26
The fix mentioned in Launchpad works for me.

---

### Post by jim-fwb on 2009-09-26
This fix works for me, too got sound back as well.  Unfortunately kdm only sees fluxbox and xfce, not kde.

Update: installing kde-full made kde available again with my old settings intact.  I'm clueless as to what had happened.

---

