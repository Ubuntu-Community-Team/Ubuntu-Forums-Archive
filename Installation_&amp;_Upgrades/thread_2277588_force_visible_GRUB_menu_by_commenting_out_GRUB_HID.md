---
title: "force visible GRUB menu by commenting out GRUB_HIDDEN_TIMEOUT"
date: 2015-05-10
forum: Installation &amp; Upgrades
---

### Post by Li_Wu on 2015-05-10
in 2015 GRUBs many people do not like the GRUB BOOT menu being hidden by default.

In earlier days, things used to be very simple with /boot/grub.cfg - people liked it that way.

Now you have to be a system programmer to even get a visible boot menu. Turns out, the only thing to do the trick is to have

**[COLOR=#ff0000]#[/COLOR]**GRUB_HIDDEN_TIMEOUT=0
[COLOR=#ff0000]**#**[/COLOR]GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=[COLOR=#008000]**6**[/COLOR]

in    **[COLOR=#ff0000]/etc/default/grub[/COLOR]**

Only if you [COLOR=#ff0000]**comment out the HIDDEN stuff,**[/COLOR] you will have the [COLOR=#006400]**desired 6 second visibility,**[/COLOR]

else you will always end up with the much hated :evil: [COLOR=#ff0000]**HIDDEN**[/COLOR] business in one variant or the other. 


run 'update-grub' afterwards to update  /boot/grub/grub.cfg

This is clearly somehow improper. There should at least be a hint in the .cfg text file of how to get rid of the dreaded HIDDEN mode without rebooting 50 times or more and fiddling with the parameters.

---

### Post by Bucky Ball on 2015-05-10
There is more than one way to skin a cat and your example by no means is the only one. This is what I use, and always have.

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
GRUB_CMDLINE_LINUX=""
```

---

### Post by Li_Wu on 2015-05-10
> **Bucky Ball said:**
>  your example by no means is the only one. 

```

#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10

```

only 3 of your parameters are relevant to the question at hand (I quoted them above). Now somebody tell us, why we get a NON-quiet (seconds countdown only, no menu) menu from this setting.

contradictory ! You set QUIET=True but get a non-quiet menu ?

my old article heading still applies, btw.

---

