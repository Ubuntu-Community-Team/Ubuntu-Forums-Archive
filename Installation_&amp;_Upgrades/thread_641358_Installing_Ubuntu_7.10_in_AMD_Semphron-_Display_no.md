---
title: "Installing Ubuntu 7.10 in AMD Semphron- Display not coming after loading"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by jakson84 on 2007-12-15
Hi,
Can anyone help me how to Install Ubuntu 7.10 properly. Nothing comes after loading. I get CPU frequency scaling not supported as error. And also **AIGLX: Screen 0 is not DRI capable as error**. I tried sudo **dpkg-reconfigure xserver-xorg **and set the appropriate values. But i can see my gnome is running. I get half my background in the display and the remaining half i get 2 ubuntu logo which is 4 bit colour.

I have AMD Semphron and Samsung 17 inch monitor.

 Some one please help me i need it very urgently. Thanks.

---

### Post by zvacet on 2007-12-15
```
sudo dpkg-reconfigure xserver-xorg
```

and choose **vesa** driver.You wil have graphic and then you can go and find right driver for your card.

---

### Post by jakson84 on 2007-12-16
Hi,
   I am facing the same error. AIGLX: Screen 0 is not DRI capable. Could you please help me on this. Kindly find the attachment for the xorg.conf file.

---

