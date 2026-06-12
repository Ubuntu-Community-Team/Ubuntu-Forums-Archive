---
title: "Recent Update Broke Make Command"
date: 2022-02-08
forum: Installation &amp; Upgrades
---

### Post by jack-klompus on 2022-02-08
Hello,

My girlfriend and I both have MS Surface 3s; she has Kubuntu 20.04 and I have KDE Neon 5.24. The only issue with the Surface 3 is that Ubuntu 20.04 doesn't support the battery monitor out of the box so we have to build and install a custom driver downloaded from [https://lkml.org/lkml/2018/8/31/538](https://lkml.org/lkml/2018/8/31/538) every time the kernel updates.

For the last year we've never encountered an issue building this driver after updating, but after installing the latest updates on my girlfriend's Ubuntu system running the make command results in the following error:

```
Make[1]: *** No rule to make target '/home/username/src/surface3_power/surface3_power.o', needed by  '__build'. Stop
Make: *** [Makefile:1762: /home/username/src/surface3_power] Error 2
```

On my KDE Neon system with the latest updates the make command here still works fine. The make file is simple and contains only the line:

```
obj-m += surface3_power.o
```

Any assistance here would be much appreciated.

Edit:
Forgot to mention the make command:
```
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
```

---

### Post by MAFoElffen on 2022-02-08
You are right in that the hardware and Desktops are similar, and it is the same scripts for both. That is just odd.

What happens if you manually add that file there. so it finds that rule?

---

### Post by jack-klompus on 2022-02-08
Thanks for the reply. If I specify -f Makefile I get the same error. If I specify -f /home/src/username/src/surface3_power/Makefile I get similar output, but instead it says no rule to make target 'modules'. /home/username/src/surface3_power is the current working directory:

```
Make: Entering directory '/usr/src/linux-headers-5.4.0-99-generic'
Make[1]: *** No rule to make target 'modules'. Stop.
```

---

