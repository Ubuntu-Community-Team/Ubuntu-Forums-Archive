---
title: "unmet dependencies error when changing Nvidia driver version"
date: 2022-07-25
forum: Installation &amp; Upgrades
---

### Post by wombyte on 2022-07-25
My system specs:
 Intel I3 10100
16 GB DDR4 Ram (2666 MHZ)
Nvidia GTX 1060 (3GB VRam)
Ubuntu 20.04 (64 bit, Desktop)
500 GB M.2 SSD Storage 
 When I try to change Nivida driver version (currently using 470, tried to change to 515), I get this issue: [https://ibb.co/stJDYd9](https://ibb.co/stJDYd9)

 It also happens when I try to switch to xorg driver.

---

### Post by Autodave on 2022-07-25
Since that is in another language, it doesn't tell me anything.  Your current 470 driver.....where did you get it from?  From Linux or from nVidia's website, or........?

---

### Post by wombyte on 2022-07-25
"Hängt ab von" means "depends on".
everything else should be clear?

I got the driver from Ubuntu's update application

---

### Post by ubfan1 on 2022-07-25
Look at the dpkg -l |grep nvidia output and see what's leftover from before the 470 driver (and purge them).

---

