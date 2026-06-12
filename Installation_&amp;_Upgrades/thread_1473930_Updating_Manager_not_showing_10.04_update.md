---
title: "Updating Manager not showing 10.04 update"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by megabenman on 2010-05-05
Hey, I'm running Ubuntu 9.10.  The Update Manager originally showed the update to Ubuntu 10.04 and I pressed the update button.  Midway through the update, my internet died so I just cancelled the update.  My internet is working again and I'm trying to update but the update manager won't show the update button.  I've pressed check a bunch of times and installed all the other updates but I can't see the distribution update.  Help?

---

### Post by Revolutionary101 on 2010-05-05
Go to System>Administration>Software Sources. Once you open that click on the Updates tab and make sure that for "Release upgrade" it says "Normal Releases", if not just change it so it does.

---

### Post by megabenman on 2010-05-05
it does say normal releases

---

### Post by lechien73 on 2010-05-05
Try pressing ALT+F2 and then typing:

```
update-manager -d
```

Does that bring the distribution upgrade option back?

---

### Post by gordtulloch on 2010-08-27
Having the same problem on a fresh Unbuntu 9.10 install, button never shows up. Updates set to normal, tried update-manager -d, no joy. Thoughts?

Regards,
  Gord

---

### Post by dylanzwick on 2011-03-07
> **lechien73 said:**
> Try pressing ALT+F2 and then typing:

```
update-manager -d
```Does that bring the distribution upgrade option back?

I did this and it worked perfectly for me. Thanks so much! What exactly does this do?

Thanks again,
Dylan

---

