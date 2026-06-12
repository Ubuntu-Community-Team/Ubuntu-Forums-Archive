---
title: "xserver problem"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by geeree on 2007-10-08
Hello,

I had terrible time yesterday trying to install Ubuntu 7.04 on a friend's Dell Inspiron 1420 laptop (Intel Core 2 Duo processor; Intel 965 GM Express Chipset). We used a Live CD that we downloaded yesterday but the installation couldn't complete. We got an error and a BusyBox console came up saying "can't access tty; job control turned off". 

This problem has been reported on these forums many times and several solutions have been suggested. Some of them (weird ones) have worked for some people. We tried out six different solutions. None worked. We also tried using the Alternate CD. Installation was complete but no graphics. The xserver gave an error "No screens found." 

Could somebody  *explain* why the problem comes up? I have had no problem in installing Ubuntu 7.04 on my own Dell Inspiron 640m. It would be great if anybody comes up with a workable solution too. 

Girish

---

### Post by Ub1476 on 2007-10-08
Am I right if he has a graphic card from ATI?

---

### Post by geeree on 2007-10-08
> **Ub1476 said:**
> Am I right if he has a graphic card from ATI?

No. The graphic card is Intel. 965GM. I think Ubuntu 7.04 comes with X11R7.2, which was released *before* this chipset was released (965GM was released in May 2007). And this is the reason for the problem. Hopefully Ubuntu 7.10 will solve it. (Gutsy Gibbon will include X11R7.3, which was released last month.)  

Girish.

---

