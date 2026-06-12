---
title: "Boot from Windows after installing Ubuntu"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by lambdacore on 2008-08-10
Heeey.

I just formatted my laptop and wanted to reinstall my dual-boot Windows Vista and Ubuntu Hardy.
I began with installing Vista, because I know it kind of overwrite grub and everything if I install it after Ubuntu.
I then installed Ubuntu and, upon restarting, was kind of surprised to realise that Vista was not in the choices offered by Grub.
It's the first time for me that Ubuntu overwrites Vista boot, and it embarrasses me.

The Windows partitions are mounted and good going. Is there anything I can do to make it possible to start it from Grub.
I guess there is like a simple command to play with Grub. I hope so.

Thanks a bunch.

---

### Post by SkonesMickLoud on 2008-08-10
You have to add an entry to your GRUB menu.lst:

```
title         "Windows Vista"
root         (hdx,y)
chainloader      +1
```

The X and Y correspond to the hard drive and partition that Vista is installed to.  GRUB starts it's numbering scheme from 0, so the first hard drive and first partition would be (hd0,0).  Second and second would be (hd1,1) and so on.

Figure out where Vista is installed and set that as the (hdx,y).  Save and reboot.

[EDIT]  This entry can go anywhere after "## ## End Default Options ##"

---

### Post by lambdacore on 2008-08-10
Hey that was pretty easy after all :D
I check my fstab to see what hd0,? to write, but did not really find it.
Anyway, I tried hd0,1 and it works.

Thanks a loooot!

You are my hero for the week.

---

