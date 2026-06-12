---
title: "No WIRED ethernet on Thinkpad T43"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by setherd on 2009-10-10
I almost never use my wired Ethernet but plugged it in yesterday and network manager can't connect. (Yes my wired network is working fine.)
Network manger knows I have a wired interface but it's not working.

I have this in /var/log/messages
```
Oct 10 10:48:28 Linux kernel: [  353.506066] tg3: eth0: Link is up at 100 Mbps, full duplex.
```
so it seems to be working, I don't know what the problem is.
Broadcom BCM5751M Gigabit Ethernet is the hardware for it.

any ideas??????

---

### Post by tekstr1der on 2009-10-10
There's problems with the tg3 driver and the current kernel. I filed a bug this morning about this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/447988](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/447988)

There are several others also. The kernel maintainers are aware of this and there is some discussion last month here:

[http://www.******************/ubuntu-kernel-team/361588-need-load-broadcom-kernel-module-before-loading-tg3-driver.html](http://www.******************/ubuntu-kernel-team/361588-need-load-broadcom-kernel-module-before-loading-tg3-driver.html)

I am not sure what the outcome will be. Looks like a situation that needs to be fixed upstream and Ubuntu devs don't want to patch. However, this late in the Karmic Dev cycle, it's unlikely we'll see a fix land if they are adament about upstream only.

No properly working wired ethernet for a ubuntu release version would be a first for me. Hope something is done.

EDIT: No idea why I cant post the link to linux-archive forum. Anyhow just google "tg3 karmic" and it's the first hit

---

### Post by setherd on 2009-10-10
thanks, I was searching for broadcom module errors :)

---

