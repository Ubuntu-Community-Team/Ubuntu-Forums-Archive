---
title: "small issue installing Ubuntu from USB drive"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by Radissthor on 2010-09-04
Hello Everyone,

I'm testing a live CD (USB actually) of Lucid Lynx in a Dell Inspiron 11z. The wired works out of the box, but wireless is not detected. I went to System-->Administration-->Hardware Drivers. There, two available, but not activated drivers are shown:
Broadcom B43 (which uses fwcutter)
Broadcom STA (which is proprietary)

I tried activating both (one at a time, of course) and it said "downloading and installing driver", but the progress bar gets stuck and it gives the following error message:
```
SystemError: installArchives() failed
```

Any guesses on what might happen? I haven't installed anything yet. Do you think Ubuntu needs to be installed in order to download and install anything?

Any help is much appreciated. :)

---

### Post by C.S.Cameron on 2010-09-04
I usually just play with the network thing on the upper right of hte screen and start wireless.
I have never had to install anything.

---

### Post by kmsalex on 2010-09-04
most large programs/drivers with multiple dependency ect, can not be install in the *live* environment. 

> I usually just play with the network thing on the upper right of hte screen and start wireless.
I have never had to install anything.     great for you!:p alot of the wireless card drivers are integrated into the kernel now a-days but some still have to be installed manually (especially the propriety ones).

more then likely one or the other will work, but you'll just have to install Ubuntu to see for your self.

PS: you really should it normaly takes less then half an hour and can be removed easily, the live cd doesn't to ubuntu justice when it comes to speed.

---

