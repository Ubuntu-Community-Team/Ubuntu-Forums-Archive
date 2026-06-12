---
title: "Skype - installation problem."
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by AnxietyDrive on 2010-02-06
I have an old version of skype running.

I downloaded the latest version for my ubuntu installation.

skype-ubuntu-intrepid_2.1.0.81-1_i386.deb

On running Gdebi package installer i get the following message:

**Error: Dependancy is not satisfiable : libasound2**

Ichecked and libasound 2 is installed and i re-installed it from synaptic manager.

Any ideas please??

AD

---

### Post by AnxietyDrive on 2010-02-07
sry to bump - just so many questions coming in  - mine dissapered very quickly - thanks :)

---

### Post by cherva on 2010-02-07
When you get this error it doesn't mean only that you don't have that package ... it means also that you gave a smaller version from the needed. For example you have python version 2.3.3 ,but a program needs version 2.4.3 .... can you write the error exactly how it shows on the screen .... And another thing do you know what audio system do you use ? I mean did you removed pulseaudio ? Because I remember that the last version of skype workes only with pulseaudio.

---

### Post by khelben1979 on 2010-02-07
> **cherva said:**
> Because I remember that the last version of skype workes only with pulseaudio.

That's incorrect, it's the other way around, that it's no longer needs Pulse audio. I have received information which says that it should work correctly by just using [ALSA]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture").

Other than this, I would recommend that you download [Skype static]("http://www.skype.com/download/skype/linux/choose/") to see if it works better.

---

