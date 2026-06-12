---
title: "X cannot find monitor - Dell Optiplex GX620"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by RyanGT on 2006-08-07
I have a Dell Optiplex GX620 as well with the ATI Radeon x600 video card. Both the Dapper live CD and the default install fail to find a monitor (I actually installed from the alternate CD without testing with the live CD).

How do I fix this?

Thanks,

Ryan

---

### Post by tseliot on 2006-08-07
Boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

The Xserver should work fine

if it doesn't you can use "vga" instead of "vesa"

---

### Post by RyanGT on 2006-08-07
Thanks, the vesa driver seems to have worked.  Is there some reason this ATI card doesn't work with the ati driver?  Any idea why it wasn't autodetected correctly?

Thanks,

Ryan

---

