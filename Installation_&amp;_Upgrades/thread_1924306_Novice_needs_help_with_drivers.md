---
title: "Novice needs help with drivers"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by Jerycko on 2012-02-12
Hello,

I'm probably asking a very stupid question but it's my first one so..
I have just installed Linux for the first time (Ubuntu 11.10). I*have just managed to install the catalyst driver for my graphic card and I*am now facing a new problem with the sound.
On windows 7 the sound was good but on ubuntu, there is a lot of noise.
I would think it comes from the fact that I'm missing a driver for my motherboard but I'm not sure and don't know how to fix that.

My system has:
Graphic card :*ATI*HD5850
Motherboard :*P7P55D-E PRO
Processor :*Intel i5

I*would very much appreciate someone to help to set up ubuntu for good and let me enjoy it to its full potential.

Thank you very much

---

### Post by mastablasta on 2012-02-12
have a look here: [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

sound drivers are already installed, but they might not support all hardware. if you have new hardware then problems arise. lame...

anyway, you can use the following commands in terminal (and then copy & paste output results here) to see what sound chip you are using. maybe someone faced your issue:

```
lspci
```

this one will list PCI devices.

```
lshw
```

this one will list your hardware.

---

