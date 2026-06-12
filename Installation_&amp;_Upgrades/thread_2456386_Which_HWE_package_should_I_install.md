---
title: "Which HWE package should I install?"
date: 2021-01-10
forum: Installation &amp; Upgrades
---

### Post by The Cog on 2021-01-10
My laptop (Ryzen 4700U) doesn't work with the 20.04 kernels because they don't have the required drivers, so I had to install a recent kernel-ppa/mainline. I tend to get and install the latest whenever I see an apt update fetching another 5.4 kernel, on the basis that there must be a security update in there. I'm currently on 5.10.5. This also involved disabling secure boot.

I gather that there is a "hwe" update available now, that includes a later (but nowhere near latest) kernel. I would like to try this out. However, this command lists 68 hwe packages that I could install:
```
apt search 'linux-*hwe-20.04*'
```

Is there any documentation on what hwe really is?

How can I tell which of these 68 packages I should install?

---

### Post by deadflowr on 2021-01-10
For stable, install linux-generic-hwe-20.04.
For bleeding edge, install linux-generic-hwe-20.04-edge.
Currently both packages will bring in the 5.8.0-36 kernel package,
but the edge will move faster to whatever kernel eventually gets used by 21.04.

(The edge version will get that upgraded stack soon after 21.04 is released in April, while the non-edge package will get it around midsummer July or so)

---

### Post by The Cog on 2021-01-11
Bingo! Thank you. 
I installed linux-generic-hwe-20.04-edge (can't help wanting the shiny new things).
It installed these 3 as dependencies: linux-headers-generic-hwe-20.04-edge, linux-hwe-5.8-headers-5.8.0-36 and linux-image-generic-hwe-20.04-edge.
Everything seems to be working, and I have re-enabled secure boot.

---

