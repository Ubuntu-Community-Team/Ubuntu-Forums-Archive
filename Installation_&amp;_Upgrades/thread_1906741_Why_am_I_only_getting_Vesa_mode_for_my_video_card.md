---
title: "Why am I only getting Vesa mode for my video card?"
date: 2012-01-09
forum: Installation &amp; Upgrades
---

### Post by PandaFace623 on 2012-01-09
I have an **AMD HD Radeon 6850**. While in windows I could run, say Starcraft 2 for example, in the most extreme of extreme graphical settings pretty easily. I recently switched over to **Ubuntu 11.10** because Windows 7 was starting to fail on me.

I have gotten Ubuntu all set up and running smoothly on the desktop. For games however I have to have the video settings set to their lowest to get about 20 frames per second. I did some reading, and if I understand correctly, the reason why I have to have the lowest settings is because I have a "VESA" video driver. This does not support 2D or 3D acceleration and is basically good for nothing in gaming.

My question is how do I get into a better mode other than VESA? Where can I get a driver that will allow my card to again perform as it was designed?

I really appreciate any and all answers.

Some more information about my system:

CPU - AMD Phenom II X6 1090T
RAM - 8GB DDR3

Let me know if there is any information I might have missed, or if you need addition details about my issue.

---

### Post by cmileto on 2012-01-09
install the propietary drivers. try looking for the addition hardware drivers.

---

### Post by PandaFace623 on 2012-01-10
> **cmileto said:**
> install the propietary drivers. try looking for the addition hardware drivers.

I did try that but I've repeatedly gotten an error each time I try to activate the proprietary drivers:

"Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

I'll attach the log file for those who are more fluent in it's language. I don't know where to look in it or really what to look for.

---

### Post by MAFoElffen on 2012-01-10
> **PandaFace623 said:**
> I did try that but I've repeatedly gotten an error each time I try to activate the proprietary drivers:

"Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

I'll attach the log file for those who are more fluent in it's language. I don't know where to look in it or really what to look for.
I'm going through your logs... And initially have a few questions while I'm reading:

1. Were you were trying the do updates / driver installs with a wifi connection?  So far I see errors with your wifi card on at least three installs/updates in the first 300 lines of your log...

2. NVidia and ATI?  Did you change from Nvidia to ATI. And if you did, did you unstall the nvidia drivers first? (Conflicting pieces.)

Reading...

---

### Post by PandaFace623 on 2012-01-10
> **MAFoElffen said:**
> I'm going through your logs... And initially have a few questions while I'm reading:

1. Were you were trying the do updates / driver installs with a wifi connection?  So far I see errors with your wifi card on at least three installs/updates in the first 300 lines of your log...

2. NVidia and ATI?  Did you change from Nvidia to ATI. And if you did, did you unstall the nvidia drivers first? (Conflicting pieces.)

Reading...

I have an amd video card, aka ati. Not sure if you knew but the ATI name has been dropped since amd bought them.

And yes I have a wifi connection and did all my driver installs with it.

---

### Post by grahammechanical on 2012-01-10
The reason MAFoElffen was asking about Nvidia was because of these lines:


> 2012-01-09 11:22:56,379 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-01-09 11:22:56,380 DEBUG: nvidia.available: falling back to default
2012-01-09 11:22:56,406 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-09 11:22:56,409 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-01-09 11:22:56,413 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-01-09 11:22:56,413 DEBUG: nvidia.available: falling back to default
2012-01-09 11:22:56,440 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-01-09 11:22:56,443 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

After failing to load an ATI/AMD proprietary FGLRX graphics driver the system then tries to load the Nvidia 96 driver and when that fails it tries with the Nvidia 173 driver and tries again and again.

You are ending up with a basic video driver but a working one because of conflicts. In my opinion.

Regards.

---

### Post by PandaFace623 on 2012-01-10
That seems really off. An NVidia card has never touched this computer.

I'm going to go ahead and try a fresh, clean reinstall and see where that takes me.

Thanks for taking a look into this.

---

### Post by mastablasta on 2012-01-11
it could be you have an nvidia integrated GPU on your motherboard. you could check that in bios and disable it, since you are not using it.
 
if you are still unable to install it there is a way to do it manualy by downloading them from the  AMD site.
 
you are correct about branding, however both ATI and new AMD card have same driver file.

---

### Post by PandaFace623 on 2012-01-14
I checked and [my motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128441") doesn't have an integrated video card.

Could you provide some instructions on how to install the drivers from AMD manually?

The clean install i tried did not solve the problem btw, same thing still occured. I cannot run on full graphical power.

---

### Post by PandaFace623 on 2012-01-20
Friendly bump

---

