---
title: "Upgrade Edgy to Feisty - X Server Won't Start"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by brett.goodwin on 2007-05-07
I just ran the official upgrade wizard to update my Edgy installation to Feisty 7.04, and upon restart, I get a message that X Server cannot start.  I looked through the error output, but I'm still fairly new to Linux and most of it didn't make sense.  I can run it again and copy some of it down if anyone thinks that will help diagnose the problem.  The one message that stood out to me was "Could not find any screens."  The one thing I can think of that I may have done which would effect this is that I used ATI's "Big Desktop" utility to stretch my desktop across my dual monitors.

Please tell me what I can do to get things back to normal!  All I want is to be able to boot into X.  If I lose my dual-monitor settings, I don't really care at this point.  Thanks!

---

### Post by robcarr2 on 2007-05-07
I am not sure if this will work for you, but it worked for me on Edgy.

Boot into recovery and use this:

sudo dpkg-reconfigure xserver-xorg

When choosing the driver for your card rather than choose ati use Vesa.

After finishing reconfiguring it restart your computer and you should be able to get into your desktop

---

### Post by brett.goodwin on 2007-05-07
Thank you very much, this allowed me to boot succesfully!

---

### Post by robcarr2 on 2007-05-07
Glad it worked for you, I have had quite a lot of trouble in this department myself so if you need any more help dont hesitate to PM me, and if I can help you I will :)

---

