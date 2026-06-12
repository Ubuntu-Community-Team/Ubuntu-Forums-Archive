---
title: "Ubuntu 9.10 beta - Huawei E220 not working after kernel update"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by marcozambi on 2009-10-14
Hi there!
I connect to Internet via USB modem Huawei E220, that was working flawlessly with 9.04 and with the vanilla version of 9.10 beta.
Using 9.10 beta with the first kernel provided (I think it was 2.6.31-11 or -12) and without applying any update I had no probs at all. Huawei E220 was recognized without any problems, than, since 2.6.31-13 kernel update, and also with the last 2.6.31-14 released this morning, the USB modem is not properly managed anymore.

Network Manager recognize the USB modem, and as a matter of fact I see the correct connection entry in Network Manager's list of available connections, but as soon as I try to connect, after a little while, I have an error message and the notification icon of not being connected to GSM network.

I am sure it's a kernel problem: I booted with 9.10 beta Live CD and Huawei works great.

Any hint?

---

### Post by ^_Pepe_^ on 2009-10-14
Hi!

I have no solution here, but I have that modem and a 9.04 version. 

Thanks for warning!

We'll keep searching!

Regards,

---

### Post by thecow on 2009-10-14
Just out of curiosity, how are you getting kernel updates?  I am just running apt-get update and then upgrade.  Do I need to specifically apt-get install a new kernel image?  Im still on 2.6.31-11 here

---

### Post by marcozambi on 2009-10-14
> **thecow said:**
> Just out of curiosity, how are you getting kernel updates?  I am just running apt-get update and then upgrade.  Do I need to specifically apt-get install a new kernel image?  Im still on 2.6.31-11 here
I check daily "System -> Update Manager" menu.

---

### Post by alexmurray on 2009-10-14
Probably related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

---

### Post by marcozambi on 2009-10-14
Yes, I agree.
Thanks for the hint :)
> **alexmurray said:**
> Probably related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

---

