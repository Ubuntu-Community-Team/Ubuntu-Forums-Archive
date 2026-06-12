---
title: "Legion 5/GPU problem"
date: 2023-01-05
forum: Installation &amp; Upgrades
---

### Post by futapowa on 2023-01-05
Hello,
I have recently installed Ubuntu 22.04 LTS and I have problems with a GPU driver. Nvidia 525 doesnt show any GPU at all. Only driver that have been working is 470/495/515 but even when I have 80fps the screen is lagging in few intervals so it doesnt work properly. I have Lenovo Legion 5 15ACH6H with 3060 RTX and some integrated gpu. Does anyone had similar problem? Thank you.

---

### Post by ubfan1 on 2023-01-05
What do you mean "Nvidia 525 doesnt show any GPU at all"?  What does lshw -c video show?   Does nvidia-smi work?  When running xorg (not Wayland, a choice at login), run xrandr --listproviders  and confirm that the nvidia is not the sink output.  Seems some settings like power mode (balanced/performance) might change things, but manual assignments work too:  
 __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia <progtorun>

---

### Post by futapowa on 2023-01-05
I mean that in Nvidia settings I don´t see anything when I´m using driver 525. nvidia -smi don´t work at all and lshw -c is showing both video cards. I did not noticed that I can change to xorg at login, I´ll give it a shot after work. Thank you.

---

