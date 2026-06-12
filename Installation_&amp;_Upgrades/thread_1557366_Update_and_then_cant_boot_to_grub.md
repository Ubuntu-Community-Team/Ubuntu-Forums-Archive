---
title: "Update and then cant boot to grub?"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by NickHansonNet on 2010-08-20
I am dual booting Windows Vista and Ubuntu 10.04 with WUBI. (Windows works fine). When I updated Ubuntu from the update manager, it just gives me this error code from a JPG attachment I just added with this post. It keeps on saying that every time ubuntu boots up.

Is there a Fix? I cant boot up to ubuntu at all...:mad:

---

### Post by bcbc on 2010-08-20
> **NickHansonNet said:**
> I am dual booting Windows Vista and Ubuntu 10.04 with WUBI. (Windows works fine). When I updated Ubuntu from the update manager, it just gives me this error code from a JPG attachment I just added with this post. It keeps on saying that every time ubuntu boots up.

Is there a Fix? I cant boot up to ubuntu at all...:mad:

do you know what partition you installed Ubuntu on? You can find out by entering ls (small LS) and the looking for /ubuntu on each e.g. ls (hd0,1)/ubuntu  or ls (hd0,msdos1)/ubuntu

when you find it try this first:
```
configfile (hd0,1)/ubuntu/winboot/wubildr.cfg
```

If that doesn't work let me know and you can try a manual boot.
If it does work, run "sudo update-grub" and see if that fixes it.

---

