---
title: "Network cards not detected"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by lonewolf88 on 2011-02-16
Toshiba T110 laptop, 4 meg ram, kernel 2.6.31-14; multi boot Suse /  Ubuntu / Windows; Atheros AR8132 Ethernet card; Realtek RTL8191 SE  wireless card.


Installed 9.10 from an old DVD lying around - everything appeared to go ok, but no networks cards - Ethernet or wireless - were detected during the install.

(Later versions do not install - problems somewhere with video card - I need to allow multi kernel selection - but this is another issue)

Does this mean that this install is toast, or can it be saved?

Thanks!

---

### Post by Koffeehaus on 2011-02-16
Under the desktop menu **System > Administration > Hardware/Additional Drivers**, the **STA** drivers can be activated for use. 

If that doesn't work try this:

[PHP]
sudo apt-get update && sudo apt-get install bcmwl-kernel-source

sudo modprobe -r b43 ssb wl && sudo modprobe wl

[/PHP]

And then check Additional Drivers again

---

### Post by Koffeehaus on 2011-02-16
P.S you'd be needing a wired connection to do that :)

---

### Post by lonewolf88 on 2011-02-20
> **Koffeehaus said:**
> P.S you'd be needing a wired connection to do that :)

Thanks, had it all working, installed 9.4, then new kernel, then upgraded to newer version.

All worked fine until I "upgraded" to 10.10;  now only boots in text mode.  :(

---

### Post by Koffeehaus on 2011-03-03
> **lonewolf88 said:**
> Thanks, had it all working, installed 9.4, then new kernel, then upgraded to newer version.

All worked fine until I "upgraded" to 10.10;  now only boots in text mode.  :(

No probs, I had the same issue when I upgraded from Mint 9 to Mint 10. Didn't have any problems when I switched to the original Maverick though.

---

