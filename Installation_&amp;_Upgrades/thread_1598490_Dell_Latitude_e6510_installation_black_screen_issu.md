---
title: "Dell Latitude e6510 installation black screen issue"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by rosati_ on 2010-10-16
Hello,
I've installed ubuntu 10.04 onto my Dell Latitude e6510 (through the wubi installer), but I can't get anything except a black screen.

I'm pretty new to ubuntu, but after a bit of looking around at graphics issues I found a bunch of boot parameters and tried different combinations of them.

i915.modeset=0
Gave me the purple loading screen, until the screen went black and I got flashing caps lock and scroll lock lights.

xforcevesa
Gave me a completely black screen -- not receiving power at all

I also tried noapci, acpi=off, irqpoll, and pci=routeirq as parameters. None of those had any success.

I've also tried letting ubuntu boot with a black screen until I heard the African drums and pressing Ctrl+Alt+F1 to go into the console, but the screen stayed black then as well.

Any way I could edit the xorg.conf file without seeing what I'm doing?

Any help you could give me would be appreciated. 
Thanks.

---

### Post by muthiahmerchant on 2010-12-15
I am having the exact same issue, I try to boot with cd and get a blank screen.

---

### Post by q999 on 2010-12-15
did you try an external monitor/ and an nvidia search may find more answers ....

---

