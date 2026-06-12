---
title: "Several Versions of Ubuntu Freeze During Install or Live CD"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by helloinsomnia on 2011-05-01
I have an old Gateway MA3 laptop that has a driver error.  This causes the screen to go black on startup and so I need to use a Live CD to fix it.  But every time I boot from a live CD it goes to that screen where it says Ubuntu and has the dots under it, after about 5 to 10 minutes the dots stop and it does not do anything from this point.  I have left it for up to an hour before.

I also tried to boot it using nomodoset because that is part of the fix.  This didn't work either.

Any tips would be awesome.

---

### Post by helloinsomnia on 2011-05-03
Anyone?

---

### Post by helloinsomnia on 2011-05-08
Bump..

---

### Post by K_45 on 2011-05-08
Try a Debian live CD here: 

[http://cdimage.debian.org/cdimage/release/current-live/i386/iso-hybrid/](http://cdimage.debian.org/cdimage/release/current-live/i386/iso-hybrid/)    

The LXDE i386 is what I'd go for with those specs. See if that boots.

---

### Post by MAFoElffen on 2011-05-08
> **helloinsomnia said:**
> I have an old Gateway MA3 laptop that has a driver error.  This causes the screen to go black on startup and so I need to use a Live CD to fix it.  But every time I boot from a live CD it goes to that screen where it says Ubuntu and has the dots under it, after about 5 to 10 minutes the dots stop and it does not do anything from this point.  I have left it for up to an hour before.

I also tried to boot it using nomodoset because that is part of the fix.  This didn't work either.

Any tips would be awesome.
Try adding 
```

radeon mode=0 acpi_osi="Linux"

```...As a startup option and refer to this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

