---
title: "Wireless stopped working on eee pc"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by GoldNugget on 2009-04-17
I am running Jaunty on an eee pc 701. The Atheros wireless card was working fine until a recent update (last night or today) and now, no wireless networks are displayed by network manager. The driver is still enabled in the Restricted Drivers Manager.

I remember there was a conflict with the Atheros driver for the eee pc under Intrepid so it was removed before the final release and I have been recompiling the driver after each kernel upgrade ever since. I was hopeful it would continue to work this time. 

Is anyone else suddenly having trouble with wireless on their eee pc? Should I hold off installing the driver in the hopes it will be working again after another update?

---

### Post by GoldNugget on 2009-04-17
I figured it out. I disabled the proprietary Madwifi driver and rebooted. It defaulted to the open driver which works fine on this machine. Hope this helps someone else.

---

