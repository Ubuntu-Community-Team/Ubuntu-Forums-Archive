---
title: "Instability, maybe caused by hotplug?"
date: 2005-02-11
forum: Installation &amp; Upgrades
---

### Post by Martin Stigge on 2005-02-11
Hi,

I discovered some problems concerning instability on my newly installed Ubuntu box. One day I came to work and the (framebuffer-)console just didn't react anymore, or on another day, the bootup just hang while starting 'hotplug', and some minutes ago, I logged in remotely and everything was strange (top just didn't start, shutdown -r now didn't restart the system, and the 'date' command always showed a time between 02:43:17 and 02:43:20).

So I don't really have much ideas how to debug this - maybe there's something wrong with hotplug? How can one debug this effectively? I'm using the stock Ubuntu kernel 2.6.8.1-4-686 with the bootsplash-Patch applied from [www.bootsplash.de](www.bootsplash.de). I'll try the original Ubuntu kernel, but I don't think that this will help...

Thanks in advance.

Martin

---

