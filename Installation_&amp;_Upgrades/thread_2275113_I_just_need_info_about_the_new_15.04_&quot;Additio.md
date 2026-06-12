---
title: "I just need info about the new 15.04 &quot;Additional Drivers&quot; Panel"
date: 2015-04-24
forum: Installation &amp; Upgrades
---

### Post by flix3 on 2015-04-24
Hello everybody. I've just successfully upgraded my Ubuntu 64bit from 14.10 to 15.04. Now the questions:


[LIST=1]
[*]In 14.04 I used the proprietary NVIDIA graphic driver version 331.89: in the "Additional Drivers" panel it was marked as "recommended". In 15.05 I can see that the version "340.76" is installed, but there is no additional hint about it; instead there is a newer version "346.59" that is marked as "tested". I would like to install a stable, "recommended" version. What should I do ? Should I keep the "default" version (the one the Ubuntu upgrade manager installed) waiting for a "recommended" version, or should I manually (well, from the panel) install version "346.59", that's marked as "tested" (but not "recommended") ?
[*]In the same panel there's a new "slot" called "Unknown: Unknown. The device is not working", that can be activated to install what's called: "Using Processor microcode firmware for Intel CPUs from intel-microcode (proprietary)". I don't think I'll ever install it (I prefer "stable" configurations), but, out of curiosity, what is it ?
[/LIST]

Thank you in advance for your answers.

---

### Post by dino99 on 2015-04-24
the 346 driver works great here with a gtx750 on vivid. The default one installed on your system is adapted to your card, but you should activate the 346 instead (no big diff)
intel continously update the 'microcode' for their cpu (fixing bug, adding new supported cpu, ...), so its good to have it installed. But today a user installing kubuntu vivid had an issue with ubiquity when trying to install intel-microcode; looks like that ubiquity might be blame here. So if you are a kubuntu user, maybe wait to install it till that issue is fixed. I myself have it installed on ubuntu, with no issue.

---

### Post by grahammechanical on 2015-04-24
I did check this out for myself. I am not sure that I understand it correctly. But to put it simply, it is a way of updating an Intel CPU's behaviour without doing a BIOS upgrade.

> The microcode data file contains the latest microcode  definitions for all Intel processors. Intel releases microcode updates  to correct processor behavior as documented in the respective processor  specification updates. While the regular approach to getting this  microcode update is via a BIOS upgrade, Intel realizes that this can be  an administrative hassle. The Linux operating system and VMware ESX  products have a mechanism to update the microcode after booting. For  example, this file will be used by the operating system mechanism if the  file is placed in the /etc/firmware directory of the Linux system.

[URL="https://downloadcenter.intel.com/download/23082"]https://downloadcenter.intel.com/download/23082
[/URL]
"Tested" is the new "Recommended." The alternative is nvidia-340-updates. We are being told the source of the driver. One is from the Nvidia tested channel and the other is from the Nvidia channel were the driver is receiving  updates and so it has not yet reached the stage of being called "tested."

Regards.

---

### Post by oldfred on 2015-04-24
Also the 340.xx version is now a legacy driver for many not so old models of cards. 
So what version is correct depends greatly on the model of the nVidia card you have.

 nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

### Post by flix3 on 2015-04-25
Thank you all for your useful info/tips.

[Edit] I've installed both the NVIDIA "tested" driver 346.59 (that added support for OpenGL 4.5, instead of 4.4) and the Intel microcode without any problem (so far).

---

