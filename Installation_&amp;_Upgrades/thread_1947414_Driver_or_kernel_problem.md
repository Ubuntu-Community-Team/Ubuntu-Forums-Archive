---
title: "Driver or kernel problem?"
date: 2012-03-26
forum: Installation &amp; Upgrades
---

### Post by Excelsys on 2012-03-26
I got error when installing a touchsecreen linux 3.0.0-12 driver in ubuntu 11.10 (which has 3.0.0-16) 

After:
# insmod /user/home/Desktop/zinFrameServer/zinFrameDriver.ko

got the following error:
insmod: error inserting /user/home/Desktop/zinFrameServer/zinFRameDriver.ko: -1 Invalid module format

the same error with:
# insmod /user/home/Desktop/zinFrameServer/VirtualInputDeviceDriver.ko

Is it a newbie installation fault or should I downgrade the kernel? How?
Note: ubuntu 11.04 has a lower kernel so I should stick to this version but lower the kernel’s last digit from 16 to 12.

---

### Post by gordintoronto on 2012-03-26
Try modprobe instead. But first: man modprobe

---

