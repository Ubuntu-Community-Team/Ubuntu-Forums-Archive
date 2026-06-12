---
title: "upgraded to 18.04.2 but still kernel 4.15"
date: 2019-02-16
forum: Installation &amp; Upgrades
---

### Post by geovino on 2019-02-16
I upgraded to 18.04.2 today but the kernel is still 4.15. Isn't it supposed to upgrade to 4.18?

---

### Post by deadflowr on 2019-02-16
No.
The installs from the original and first point release remain on the original kernel and X stacks.
In order to get the upgraded kernel you must either install the .2 point release (or .3 , or .4 or .5 when they come out)
or install the hwe packages
Should be
```
linux-generic-hwe-18.04
xserver-xorg-hwe-18.04
```
those should roll meaning once installed you'll get the future stack upgrades when they arrive at the next point releases.

---

### Post by geovino on 2019-02-16
Thank you.

---

### Post by geovino on 2019-02-19
had to add a . between the 1804 in first command. Now it installed.

---

### Post by Dennis N on 2019-02-19
There should be a decimal point in the 18.04
linux-generic-hwe-18.04

---

### Post by fumie23 on 2019-02-19
Hi, 
My kernel was 4.15.0-1031-raspi2, then try these:
sudo apt install linux-generic-hwe-18.04
sudo apt install linux-generic-hwe-18.04-edge

Then always failed. I tried four times from SDcard burning.

According to this message, "Couldn't find DTB bcm2710-rpi-3-b-plus.dtb on the following paths:" 
It seems that 18.04.2 and kernel 4.18 is not suitable on my RaspberryPi 3B+ :(

[ATTACH=CONFIG]282595[/ATTACH]

All suggestion are welcome :'(

---

### Post by deadflowr on 2019-02-20
> **Dennis N said:**
> There should be a decimal point in the 18.04
linux-generic-hwe-18.04
Fix that oversight.
Not sure how I missed it.
> **fumie23 said:**
> Hi, 
My kernel was 4.15.0-1031-raspi2, then try these:
sudo apt install linux-generic-hwe-18.04
sudo apt install linux-generic-hwe-18.04-edge

Then always failed. I tried four times from SDcard burning.

According to this message, "Couldn't find DTB bcm2710-rpi-3-b-plus.dtb on the following paths:" 
It seems that 18.04.2 and kernel 4.18 is not suitable on my RaspberryPi 3B+ :(

[ATTACH=CONFIG]282595[/ATTACH]

All suggestion are welcome :'(

You need a raspi2 kernel and not a generic kernel.
There are no raspi2 hwe kernels so no 4.18 kernel for 18.04.

Will there be in the future?
Probably not, as there are no hwe raspi2 kernels for 16.04 either.

---

### Post by fumie23 on 2019-02-22
So that's why I always failed to upgrade. Thanks!

---

