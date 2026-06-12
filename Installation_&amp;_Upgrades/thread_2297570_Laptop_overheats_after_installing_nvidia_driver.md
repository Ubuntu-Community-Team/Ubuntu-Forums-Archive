---
title: "Laptop overheats after installing nvidia driver"
date: 2015-10-05
forum: Installation &amp; Upgrades
---

### Post by marius22 on 2015-10-05
Hey,

my laptop is a Dell E6420 with a Intel HD Graphics 300NVIDIA NVS 4200M 1GB RAM0 GPU.

This weekend I installed Nvidia driver 349.16 from the Nvidia page. I got stuck at the known login loop issue. I solved it by deactivating the Intel Graphics in BIOS and reinstalling Nvidia, so I do not use the hybrid function anymore (I tried with bumblebee but failed) .
After reconfiguration of unity (it didn't load for a reason I don't know) the laptop seemed to work again. I tried to played a round of hearthstone ( ~5 -10 minutes) and the laptop shut down due to overheating. Before that the game was lacking, I think that is just a symptom of the overheating. 
After cooling down I tried it again for 5 minutes and checked the sensors:
acpitz-virtual-0
Adapter: Virtual device
temp1:        +25.0°C  (crit = +107.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +50.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +47.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +48.0°C  (high = +86.0°C, crit = +100.0°C)

i8k-virtual-0
Adapter: Virtual device
fan2:        86520 RPM
temp1:        +50.0°C  
temp2:        +28.0°C  
temp3:        +38.0°C  
temp4:        +85.0°C  

So the last one was far too hot, but quickly cooled down after quitting the game. 
I am not sure if the fan was working on full speed - how do I know what full speed is? 
Before I used the standard nouveau driver so the graphic card was never challenged. Is it possible that the hardware is broken?

What next step do you recommend? I am asking here because the problem looks serious to me and I don't plan on destroying my laptop.

Thanks you!

---

