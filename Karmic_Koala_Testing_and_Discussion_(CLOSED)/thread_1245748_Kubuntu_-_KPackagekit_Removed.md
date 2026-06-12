---
title: "Kubuntu - KPackagekit Removed"
date: 2009-08-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by graaant on 2009-08-20
Well it seems that today's update's removed KPackageKit at the whole packagekit update.
But so far, there's no new updater?

Anyone know what the plans for this is? Not that I mind using terminal..

---

### Post by taavikko on 2009-08-21
> **graaant said:**
> Well it seems that today's update's removed KPackageKit at the whole packagekit update.
But so far, there's no new updater?

Anyone know what the plans for this is? Not that I mind using terminal..

You did the partial upgrade, kpackakit isn't supposed to be removed.

---

### Post by zenarcher on 2009-08-21
Same situation here.  I just am holding back on updates, rather than let it remove KPackageKit.  I see there is now an updater of some sort which would be added, but I'm not sure if that's supposed to replace KPackageKit or what.

Cheers,
zenarcher

---

### Post by caryb on 2009-08-21
If you don't hold back you will also loose kubuntu-desktop, then you would have to use your other O/S on the dual boot. In my case it's Vista (the shame of it):lolflag:

Cary

---

### Post by zenarcher on 2009-08-21
Since I don't use any other O/S, I think I'll go with the holding back!:P

---

### Post by taavikko on 2009-08-21
> **caryb said:**
> If you don't hold back you will also loose kubuntu-desktop, then you would have to use your other O/S on the dual boot.

Cary

?

kubuntu-desktop is jus a meta-package which in itself isn't a issue if it's removed.

---

### Post by zenarcher on 2009-08-21
Currently, it looks like policykit-kde is the only package that will be removed if updates are done.

Cheers,
zenarcher

---

### Post by taavikko on 2009-08-21
> **zenarcher said:**
> Currently, it looks like policykit-kde is the only package that will be removed if updates are done.

Cheers,
zenarcher

It's ok to remove, it's been integrated to kde-workspace-bin
```
kpackagekit (0.4.2-0ubuntu2) karmic; urgency=low

  * Replace policykit-kde dep with kdebase-workspace-bin

 -- Jonathan Riddell <jriddell@ubuntu.com>  Thu, 20 Aug 2009 23:33:45 +0100

kpackagekit (0.4.2-0ubuntu1) karmic; urgency=low
```

---

### Post by zenarcher on 2009-08-21
Thanks for that information.  Really appreciate it!

Cheers,
zenarcher

---

### Post by 23meg on 2009-08-21
> **zenarcher said:**
> Thanks for that information.  Really appreciate it!

This kind of information is **always** in the changelogs. When in doubt about an upgrade, check them; that's what they're there for.

---

### Post by inportb on 2009-08-21
> **caryb said:**
> If you don't hold back you will also loose kubuntu-desktop, then you would have to use your other O/S on the dual boot. In my case it's Vista (the shame of it)

Well not really; I lost KDE, but it was trivial to reinstall kubuntu-desktop from commandline.

---

