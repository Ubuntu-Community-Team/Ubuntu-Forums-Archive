---
title: "Zte mf622 - usb hdspa modem"
date: 2009-06-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nyarnon on 2009-06-06
Does anybody get passed the usbdrive configuration on this one. Needless to say it works just fine under Jaunty but with Koala it seems to get stuck.

---

### Post by jfernyhough on 2009-06-06
Have you installed udev-extras?

If this doesn't work I did a tutorial on getting the MF-627 working though that should now work with just udev-extras ( [http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630) ).

---

### Post by macroshaft on 2009-06-06
Mine works just fine, by fine I mean the modem works but three mobile doesn't! Interestingly I can't make it work in kubuntu. It picks the modem up fine but I'm damned if I can figure out how to tell it to connect!

---

### Post by nyarnon on 2009-06-06
> **jfernyhough said:**
> Have you installed udev-extras?



Yes they are installed. No problem it's not my modem I was fixing the thing to run on jaunty and noticed that it wouldn't run on karmic because it doesn't pass usb drive status.

---

### Post by nyarnon on 2009-06-06
> **macroshaft said:**
> Mine works just fine, by fine I mean the modem works but three mobile doesn't! Interestingly I can't make it work in kubuntu. It picks the modem up fine but I'm damned if I can figure out how to tell it to connect!

Did you check your dmesg? Mine is stuck at usbdrive status. If you can get to modem modus make sure your pin is disabled. Then NM should do the rest.

---

### Post by GeorgeVita on 2009-06-07
Hi **nyarnon**, **jfernyhough** and **macroshaft**,

I have a ZTE MF636 (very popular in Greece) which managed to work with various Linux distros/versions in many ways but always using tips & tricks.

I need some help on how to install the "typical 9.10" (as per today) on my EeePC 1000H having the same (as you?) versions of packages in order to understand if it works or not. Can you suggest a link to any 'HowTo install Ubuntu X.YY for testing?".

> **Nullack said:**
> ...People who want to contribute towards Ubuntu testing need to **keep their configuration in a supportable state**...

Do you know how can I obtain this?

Till now I made some tests on a full installation of 9.04 with updates to a newer kernel. I do not feel this a "typical" way. On June 11th the **Alpha 2** will be released. Can we all have the same "starting point" to test our ZTEs?

Regards,
George

---

