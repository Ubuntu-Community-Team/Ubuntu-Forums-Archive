---
title: "Very High Swap Usage while using Gwibber"
date: 2010-04-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by prabin-dahal on 2010-04-20
I am testing beta version of lucid. I update everyday for the security updates. but everytime when I load gwibber service my swap usage goes very high..
I uninstalled gwibber, gwibber-services and restarted the computer. After restarting the swap usage is normal.
When I reinstalled gwibber, again my swap usage goes very high and make my computer unresponsive.
if I do "sudo swapoff -a", from the task manager I can see the swap emptying, but after some time the operation is killed. now I am getting the following error when trying to switch the swap off.
 
```
swapoff: /dev/sda7: swapoff failed: Cannot allocate memory
```

I found this link [http://ubuntuforums.org/showthread.php?p=9142335](http://ubuntuforums.org/showthread.php?p=9142335)
maybe they are related..

---

### Post by perham on 2010-04-20
> **prabin-dahal said:**
> I am testing beta version of lucid. I update everyday for the security updates. but everytime when I load gwibber service my swap usage goes very high..
I uninstalled gwibber, gwibber-services and restarted the computer. After restarting the swap usage is normal.
When I reinstalled gwibber, again my swap usage goes very high and make my computer unresponsive.
if I do "sudo swapoff -a", from the task manager I can see the swap emptying, but after some time the operation is killed. now I am getting the following error when trying to switch the swap off.
 
```
swapoff: /dev/sda7: swapoff failed: Cannot allocate memory
```

I found this link [http://ubuntuforums.org/showthread.php?p=9142335](http://ubuntuforums.org/showthread.php?p=9142335)
maybe they are related..

swap is needed only when your ram is low. how much ram do you got there?

---

### Post by tokyobadger on 2010-04-20
I just checked my system, gwibber is using most RAM 149.5M - the system has been up for 34 hours and change, chromium (13 tabs), evolution, gwibber, 2 terminals, OOWriter have been open constantly during that time.

Overall the system is at 1.4G RAM usage, swap is untouched. This install is Lucid amd64 (updated from Beta 1) but pretty much vanilla; i7-920, 6G RAM, nvidia proprietary drivers. 

Gwibber certainly looks a little hungry, but not terrible. Could you share

1) hardware details
2) Lucid install and running apps
3) why you want to run the command swapoff

---

### Post by snkiz on 2010-04-20
gwibber is a heavy one. I myself can't use it and surf at the same time. But if you have at least a gig you shouldn't notice a slowdown. I have 384 megs of ram and 1 gig swap with gwibber and chrome (2 tabs) I'm touching about 200 megs of swap.

---

