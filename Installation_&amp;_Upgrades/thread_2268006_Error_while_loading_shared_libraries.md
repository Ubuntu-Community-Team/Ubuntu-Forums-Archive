---
title: "Error while loading shared libraries"
date: 2015-03-05
forum: Installation &amp; Upgrades
---

### Post by alex342 on 2015-03-05
Hello. I'm using a software called GPUOcelot in order to be able to compile a software that I'm programming that uses CUDA. But my computer doesn't have any NVIDIA card, so tha'ts the reason why I am using this emulator, but when I execute the next command:
g++ -o Sinulacionpositrones.out Simulacionpositrones.o `OcelotConfig -l`

I obtain this:
OcelotConfig: error while loading shared libraries: libboost_system.so.1.46.1: cannot open shared object file: No such file or directory

What can I do?

---

### Post by steeldriver on 2015-03-05
Hello and welcome to the forums

What Ubuntu version are you using? Where did you obtain GPUOcelot and how did you install it? 

Did you install any of the boost library development components?

---

### Post by alex342 on 2015-03-05
Ubuntu 14.04, GPUocelot was in a .deb file. i think i install boost in the terminal, but it seems that is not the version that GPUOcelot want. I am desperate about this, besides this software has a very poor documentation. 
The webpage is this:
[https://code.google.com/p/gpuocelot/](https://code.google.com/p/gpuocelot/)

---

