---
title: "Live CD screen flickers continuously on 10.04.1"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by cclemon on 2010-08-28
As the title says, when I select the install option on the liveCD, the Ubuntu logo is shown, and the flickering starts. I've tried the vga=XXX option, but no luck. Any experiences? It doesnt' happen with the 9.10 live CD...

---

### Post by mörgæs on 2010-08-29
That is the advantage of using a live CD: Now you know which version to install (if you don't want to carry on experimenting with boot options). 

Some screen cards, which were supported in 9.10, lost support in 10.04, but since 9.10 is maintained until april 2011 you will not be ubuntu-less :-)

---

### Post by cclemon on 2010-08-29
I'll try to upgrade to Lucid Lynx from the update manager in 9.10...

---

### Post by varunendra on 2010-08-30
If there's not something so special in Lucid that you really like to have, I'd suggest to stick with Karmik since it seems to support your system 'out-of-box'.

Upgrading sometimes causes problems and as such, mostly a fresh install is recommended. However, it's just a minor risk that I guess you can safely take (if you can reinstall Karmik, just in case :))

I'm sure the driver will also get upgraded while upgrading the system causing the same problem and so you may need to roll back to the earlier one (the one used in Karmik).

Alternatively, you may try to make a fresh install of Lucid, and only replace display driver modules with the ones used in karmik. To determine which driver/modules are in use, you may try **lsmod** or **lspci -v** commands.

---

