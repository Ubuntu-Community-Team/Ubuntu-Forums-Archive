---
title: "fglrx Problem AFTER upgrade (Xserver doesn't start)"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by Zólhos on 2007-05-12
Hi!

Before upgrading to 7.04 my ubuntu was working correctly with the fglrx binary driver, I had even DRI.

But after I upgraded, xserver stopped working!!
It said "no screens found", but I was running X exactly with the same xorg.conf!
When I switched to "radeon" it started working again...

Also, I tried to use "X -configure" and it X SEGFAULTED!!

Is this a know problem? Can you help me please?

Xorg log for fglrx: [http://www.inf.ufpr.br/prz05/xorg_log_fglrx](http://www.inf.ufpr.br/prz05/xorg_log_fglrx)
Xorg log for X -configure: [http://www.inf.ufpr.br/prz05/x_-configure_log](http://www.inf.ufpr.br/prz05/x_-configure_log)

Thanks!

---

### Post by benanzo on 2007-05-12
Try to reconfigure fglrx

Update your system:
```

sudo apt-get update
sudo apt-get upgrade

```

Download the fglrx driver (if you haven't already):
```
sudo apt-get install xorg-driver-fglrx
```

Update your currently running modules:
```
sudo depmod -a
```

Reconfigure your xorg.conf with ATI's configuration script:
```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

Then reboot.

---

### Post by Zólhos on 2007-05-12
Thanks for the quick answer, but...

I had already seen these tips..
Tried executng them again, but it didn't work... =(

Any other tips?

Thanks,
Paulo.

---

