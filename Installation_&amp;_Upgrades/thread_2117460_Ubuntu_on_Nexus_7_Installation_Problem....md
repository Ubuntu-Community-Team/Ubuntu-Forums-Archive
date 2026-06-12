---
title: "Ubuntu on Nexus 7 Installation Problem..."
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by LucaS919 on 2013-02-18
I recently bought a Nexus 7, was having fun with it, until I heard Ubuntu had a port for it.
So, naturally, I started up my laptop and downloaded the installer, hooked the nexus 7 up in FastBoot mode, and let the installer go.
No errors at all, everything was fine. 
Nexus rebooted, did the partition-related stuff, started, and showed the Ubuntu startup screen.
Then... it went black. Here;s what I can gather:
-It's still on, the backlight is on.
-My computer can't recognize it, nor can ADB or Fastboot.
-It's doing nothing.
-There's no way to return to default ROM due to the sheer fact that nothing can read it.
Help? Please?

---

### Post by grahammechanical on 2013-02-18
Where did you get that image from? Did you follow instructions like these?

[https://wiki.ubuntu.com/Nexus7/Installation]("https://wiki.ubuntu.com/Nexus7/Installation")

You have installed a very experimental OS. That link will give instructions on how to re-flash Android back onto the Nexus 7

Regards.

---

### Post by LucaS919 on 2013-02-18
I followed those exactly. I've tried it twice now, no result.
32 GB Nexus 7
Default running 4.2.2 Jelly Bean
Nothing special about it.
What's wrong...

---

### Post by renewehle on 2013-02-18
Same here. You are not alone.
 32 GB Nexus 7 (GSM version)

---

### Post by ubunpar on 2013-02-19
Have you put it back into fast boot? Mine did the same as yours... Hold power button for 5-10 seconds (or) until it powers down, then enter fast boot the usual way- volume down + power .

---

### Post by LucaS919 on 2013-02-19
What does Fastboot matter here?
I installed it properly, it rebooted, ubuntu startup logo and such,
and then it black screens.
Nothing to do with Fastboot.

---

### Post by darkod on 2013-02-19
> **LucaS919 said:**
> What does Fastboot matter here?
I installed it properly, it rebooted, ubuntu startup logo and such,
and then it black screens.
Nothing to do with Fastboot.

I think the idea of the question is that you need to put it back into fastboot to flash it back to Nexus rom. Because you said you can't do that either.

The wiki also says that if it goes wrong, you can put it back into fastboot and flash it back to Nexus rom.

---

### Post by LucaS919 on 2013-02-19
Oh, I see. I have managed to do that and flashed back, but I'd still like to know if there's a way to get Ubuntu working..

---

### Post by heyup on 2013-02-19
This might help.

[http://ubuntuforums.org/showthread.php?t=2116406]("http://ubuntuforums.org/showthread.php?t=2116406")

---

### Post by LucaS919 on 2013-02-19
Going to try this soon. Thanks.

---

### Post by LucaS919 on 2013-02-21
This indeed worked. Thanks.

---

