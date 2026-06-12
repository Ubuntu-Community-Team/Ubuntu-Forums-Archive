---
title: "ubuntu installation fails with a broken screen"
date: 2020-02-23
forum: Installation &amp; Upgrades
---

### Post by jemin.hwangbo on 2020-02-23
I tried 18.04 (64bit) and 19.10(64bit) and both show the same symptom. After I press either "try ubuntu without installation" or "install ubuntu", I get broken a screen (a few purple and white lines in black background)

It works with graphics safe mode. I tried to upgrade my nvidia driver (440, 435 and 430) but none of them made a difference after reboot.

I am using 

Asus x570 pro + 3950x + 2070 super

Is there anything I should try? I am using fresh new parts so I guess it can be hardware faults too but 

1. in graphics safe mode, it display well with 1080p
2. memory and number of cores seem fine in htop

I turned off the secure boot and it didn't make a difference

---

### Post by EuclideanCoffee on 2020-02-23
Nvidia is a difficult case.

There are a few steps you can take to work around it.

See step 3 in this link below.

[https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics](https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics)

---

### Post by jemin.hwangbo on 2020-02-23
You saved my day!!! I forgot about this trick

---

