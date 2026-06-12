---
title: "Is Wubi releasing an Intrepid Ibex version?"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlbr on 2008-10-22
Hi you all, just wondering if the Wubi project will be releasing a 8.10 version in or around October 30?

Anyone know?

---

### Post by kansasnoob on 2008-10-22
> **jlbr said:**
> Hi you all, just wondering if the Wubi project will be releasing a 8.10 version in or around October 30?

Anyone know?

I had to look here:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

It says, "Upgrading from 8.04 to 8.10 will be fully supported."

So I assume there will be.

I only briefly tried Wubi out of curiosity, but I found Ubuntu to run noticably slower under Wubi than in a dual boot.

I've also read several complaints of corrupted Wubi installs due to power cuts:

> 
Any gotcha?

Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.


From:

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

