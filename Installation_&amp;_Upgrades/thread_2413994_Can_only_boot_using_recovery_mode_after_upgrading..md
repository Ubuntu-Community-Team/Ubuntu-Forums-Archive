---
title: "Can only boot using recovery mode after upgrading."
date: 2019-03-04
forum: Installation &amp; Upgrades
---

### Post by william-s2 on 2019-03-04
I just upgrading from 18.04 to 18.10, and everything seemed to go smoothly - until the reboot, stuck on purple splash, I waited, waited some more, and then did a cold restart and booted in recovery mode - which worked fine - everything seemed to be fine. Though, every time I start the pc, I have to use recovery mode, or it will hang.

Any ideas would be a big help.

Thanks.

---

### Post by kc1di on 2019-03-05
Can you give us a little more information about the Machine in question?  
What graphics card?

---

### Post by william-s2 on 2019-03-05
I have the nvidia gtx 650 running the 390 driver. 

This morning I did I fresh install with 18.10 and after two reboots - the same problem, I have to boot using recovery mode.
After, I did a fresh install of 18.04.2 and it's running fine/booting fine. Maybe i have my drives set up wrong?? or a problem with my graphic card? --that the newer kernel doesn't like.

---

### Post by kc1di on 2019-03-05
I'm not sure but with Nvidia drivers it could be that with a different kernel the driver module is not being created.
If you have no pressing reason to go to 18.10 I'd stick with 18.04 since it's LTS. 
Also check and make sure in 18.10 that your not using wayland instead of x.org since Nvidia drivers are not support yet under wayland.

---

### Post by william-s2 on 2019-03-05
First: thanks a lot for the reply. Yes, I agree. I have 18.10 on my ThinkPad and it runs great. I'll leave 18.04 on my desktop and wait for the next LTS - I do most of my work on it and reliability is important.

I didn't think Wayland was the default - but I'm thinking the problem started after installing the propriety graphics driver. Fun fact: On my Thinkpad the media buttons, etc ... didn't work using Xorg, but work perfectly with Wayland.

---

### Post by kc1di on 2019-03-05
which Thinkpad do you have? Been thinking of getting one.

---

### Post by #&amp;thj^% on 2019-03-05
```
inxi -SM
System:
  Host: arch Kernel: 4.20.13.a-1-hardened x86_64 bits: 64 
  Desktop: MATE 1.20.4 Distro: Arch Linux 
Machine:
  **Type: Laptop System: LENOVO product: 2349M88 v: ThinkPad T430 **
  serial: <root required> 
  Mobo: LENOVO model: 2349M88 serial: <root required> UEFI [Legacy]: LENOVO 
  v: G1ETB8WW (2.78 ) date: 09/19/2018 

```
Most of my usage is with the T-models have left me wanting nothing, great little lappy's.

---

### Post by william-s2 on 2019-03-05
Carbon X1 - I've had it about 6 months, I bought it blank, installed 18.04 ( my first Linux distro in 5 years  - I really missed it and refuse to do Win 10 ). With exception of the volume/brightness buttons, everything worked great. I gave Wayland a go, just to try it, and noticed all the buttons now worked. Now I have 18.10 on it and runs perfectly. I'm really happy with my decision to get back to Linux. I still have Win 7 on my old desktop drive (for one app I need on occasion ).

---

