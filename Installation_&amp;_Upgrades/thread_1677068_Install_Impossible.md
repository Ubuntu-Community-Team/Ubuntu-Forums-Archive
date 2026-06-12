---
title: "Install Impossible"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by the_obs on 2011-01-28
Hey all,
I'm trying to install Ubuntu 10.10 x64 but I can't, as the SATA disk controller on my [Asus P7P55D-E EVO]("http://www.asus.com/product.aspx?P_ID=6tYErg5Gvuxs4VGz"), a Marvell 6Gb/s PCIe controller, isn't recognized (or so I guess), and my hard drives aren't seen. I'm having difficulty finding the drivers and then I wouldn't know how to use them. I'm a complete n00b to Linux (for now). Could you help me with this problem?

---

### Post by sikander3786 on 2011-01-28
Welcome to the forums :-)

Did you try connecting your SATA drive to the other SATA controller on your mother board highlighted here.
> 
Storage	Intel® P55 Express Chipset
- 6 x SATA 3.0 Gb/s ports
- Intel Matrix Storage Technology supports RAID 0, 1, 5 and 10
JMicron® JMB363 SATA & PATA controller:
- 1 x UltraDMA 133/100/66 for up to 2 PATA devices
[B][COLOR="Red"]- 1 x SATA 3Gb/s port (black)
- 1 x eSATA 3Gb/s port[/COLOR][/B]
Marvell® PCIe SATA6Gb/s controller:
- 2 x SATA 6.0 Gb/s ports (Gray)

---

### Post by the_obs on 2011-01-28
I believe you highlighted the wrong text. 
The JMicron Controller is used for my optical drives, which leaves the Intel P55 chipset. However, it offers lower data transfer rate, which is why I like to use the Marvell controller, even though the hard drives are the theoretical bottlenecks.
Is there no way to use the Marvell controller?

---

### Post by Quackers on 2011-01-28
I don't think that is possible yet, as the Marvell controller is not supported. It may be soon though :-)
Unless you are using SSD's there is no noticable difference in speed.

---

### Post by the_obs on 2011-01-28
I have a 32 GB SSD for Windows OS, wanted to install Ubuntu on it too. I have a second drive though, and HDD, on which I could alternatively install Ubuntu. I'll try plugging in the second drive to the P55 chipset controller and installing ubuntu there.

---

### Post by ronparent on 2011-01-29
You are being perhaps a bit optimistic planning to install Ubuntu alongside windows on a 32 Gb ssd. I have Win 7 on a 40Gb ssd and figure that is comfortable only if I install win programs on a separate drive whenever possible. Over time windows tends to expand drastically so that it will occupy more than twice it original freshly installed space. Although you can test Ubuntu on as little as a 4 or 5 Gb space windows will probably begrudge you that on a 32Gb drive.

---

