---
title: "do I need any drivers after installing ubuntu"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by forsubhi on 2012-05-07
I installed ubuntu 12.04 , should I install any drivers (for sound card and graphic card ,as instance) after installation ?

---

### Post by cortman on 2012-05-07
Unless something is obviously not working, no.

---

### Post by forsubhi on 2012-05-08
ok , then how can I update my drivers ?

---

### Post by oldos2er on 2012-05-08
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by deadflowr on 2012-05-08
I find the stock open-source drivers to be sufficient. However certain graphic cards work better with restricted drivers, such as nvidia. I'm running ati open-source on this machine, and have intel open-source on another, and they run smooth as can be.
 In terms of sound cards, every card I've had has worked out of the box; without tinkering with the drivers.
 The only thing that I can think of that might really need restricted drivers for might be any wireless adapters.
 But if you follow oldos2er's advice you should be fine.

---

### Post by mips on 2012-05-08
What gfx do you have? The only thing besides your gpu driver you could need is codecs which you can install with ubuntu-restricted-extras

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by SeijiSensei on 2012-05-08
If you're really using Kubuntu (you tagged the thread with this, but it sounds like you're running Ubuntu), you can just click on the blue launcher button on the left end of the panel at the bottom of the screen and choose Applications > System > Additional Drivers.  The application will analyze your hardware and determine if there a proprietary drivers required for your hardware.  The app will then download and install them if you tell it to do so.

I don't know where the Additional Drivers application lives in Unity; maybe someone else here can chime in?

There is almost never any need to install a driver manually in Ubuntu, and in general it's not a good idea to do so.  By relying on the drivers in the standard repositories, you will automatically get any updates when they are released as part of the overall software upgrade process that happens each night.

---

