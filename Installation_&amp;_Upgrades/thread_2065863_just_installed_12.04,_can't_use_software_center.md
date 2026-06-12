---
title: "just installed 12.04, can't use software center"
date: 2012-10-03
forum: Installation &amp; Upgrades
---

### Post by joshofalltrades on 2012-10-03
howdy y'all, i'm new here
i just installed ubuntu 12.04 my on my HP laptop, using a brand new hard drive.  now that its running, i try to open the software center and it runs for 2-3 seconds with a "busy" icon in the center of the window, then closes.
any idea how to get this working right?  there's some software i need to get running to make this thing work out for me, and i figure i need the software center running for that 
thanks in advance

---

### Post by vasa1 on 2012-10-03
Could you share the specs of your laptop?
The Software Center is quite resource-hungry.

Also, what is the output when you run **software-center** from a terminal?

---

### Post by jerrrys on 2012-10-03
Hi josh, welcome to the forums :)

You may just need to update your fresh install.  [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update && sudo apt-get upgrade

---

