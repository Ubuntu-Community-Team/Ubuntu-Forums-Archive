---
title: "Finally was able install Ubuntu 12.04 (almost!)"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by jdrichardson on 2012-05-26
After several tries I was finally able to install 12.04 on my two computers - an AMD 64-bit machine with nVidia GE Force 6150 graphics chip and another AMD 64-bit machine with and ATI graphics chip. Neither will run with custom graphics drivers, but that's not a show-stopper for me. When this happens I run the nouveau driver (assuming that's the default). I usually set the gamma value at startup by having the following command inserted as a startup application:

/usr/bin/xgamma -gamma 0.7

This has always worked, but now it doesn't! It appears to use the setting for the log-in screen, but when I log-in to "ubuntu" it defaults to a gamma value of 1.00, which is too light for me. This happens on both computers. Once logged in, I can manually run said command and the appropriate adjustments are made, but that shouldn't be. If I run xgamma, it says the value is 0.7, but somehow this doesn't make it to the driver.

Does anyone have any suggestions on how I can correct this behavior? I'd sure appreciate it!

---

