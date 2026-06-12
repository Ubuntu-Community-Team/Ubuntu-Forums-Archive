---
title: "Dial up Internet Connection"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by Jim Davis on 2006-08-30
I need help setting up a dial up internet connection. I have just completed installation of 6.06.

Jim Davis:)

---

### Post by Jim Davis on 2006-08-30
I have not been able to connect with the internet.

Jim Davis

---

### Post by shultzjr on 2006-08-30
Please list modem and chipset and version of Ubuntu you are using.

What have you tried so far?

---

### Post by zxee on 2006-08-30
> **Jim Davis said:**
> I have not been able to connect with the internet.

Jim Davis

Is this an internal pci modem you have? If it is then go to [http://www.linmodems.org/](http://www.linmodems.org/) and download the scanmodem tool and then you'll have to follow the directions there- There is also a method here at ubuntu check the link in my signature. 
If you know you have a controller type modem rather than a winmodem then you can open a terminal and type sudo pppconfig <enter>

---

### Post by unisol on 2006-08-31
type wvdialconf/etc/wvdial.conf and see if dapper can tell you that it recognizes your modem and what port it is on

---

