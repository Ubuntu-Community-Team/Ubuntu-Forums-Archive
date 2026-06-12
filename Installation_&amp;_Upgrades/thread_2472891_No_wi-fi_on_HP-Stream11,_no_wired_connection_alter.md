---
title: "No wi-fi on HP-Stream11, no wired connection alternative"
date: 2022-03-16
forum: Installation &amp; Upgrades
---

### Post by jackn on 2022-03-16
Hi.

Can't install linuxmint-20.3-mate-64bit on my HP-Stream 11.
Love Linux, hate MS, life hell since Win11.


Tried linuxmint-20.3-mate-64bit live disk on a USB key, but couldn't proceed to install as no wi-fi.
The key works well on another computer and has been verified.
Sb suggested Ubuntu 14.10. Couldn't get past GRUB.

Realtek RTL8821CE 802.11ac PCIe Adapter.

No Ethernet connectivity, home not wired at all, living off my smartphone hotspot.

Is there any other way to proceed?
Another distro?
Install the necessary packages from a USB key?
Alternative wi-fi adapter on a USB key? But will *that* be compatible...?

Used to be an average Linux user years ago. No geek.

HP-Stream 11-ak0xxx
64-bit, Intel(R) Celeron(R) N4000, 4Gb RAM, 64Gb flash storage.


Thank you kindly.
Jackn

---

### Post by jackn on 2022-03-22
Solved.
Very pleased.

Two solutions:
[LIST]
[*]To my great pleasure, installing from live disk was enough. The system itself announced that the adapter didn't work and offered to fix it. It then went on to do so successfully.
I benefited here from Pierre's advice, on the LinuxMint forums, see link below, to USB tether the laptop to my smartphone connection. I had had no idea about this, it worked fine, and was, needless to say, indispensable as long as the adapter wasn't recognized.[/LIST]

[LIST]
[*]The above is enough, obviously.
While still on the live disk, before the install, I did, however, check out, the procedure.
[https://easylinuxtipsproject.blogspot.com/p/realtek.html#ID6]("https://easylinuxtipsproject.blogspot.com/p/realtek.html#ID6")
suggested by Pierre.
Installing the driver went without a hitch. Couldn't test it, as testing required a reboot, and on live disk, changes obviously don't persist.
I'm convinced it would work fine.
I'm mentioning this in case your system doesn't fix things on its own.[/LIST]
Thank you, Ubuntu people, for the OS.
Thank you, Pierre from the LinuxMint Forums, for this helpful advice.

---

