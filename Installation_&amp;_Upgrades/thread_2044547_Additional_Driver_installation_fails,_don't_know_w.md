---
title: "Additional Driver installation fails, don't know what to do"
date: 2012-08-19
forum: Installation &amp; Upgrades
---

### Post by GazaIan on 2012-08-19
Boy do I hate proprietary drivers. I'm trying to install the driver for my ATI Mobility Radeon 4250 but Every time I try, I get;

```
Sorry, installation of this driver failed.

Please have a look at the log file for details:[log location]

```Here is the log itself, it's filled with warnings but I honestly don't know how to resolve this issue, Desktop hardware isn't my thing :(

[http://paste.ubuntu.com/1155792/](http://paste.ubuntu.com/1155792/)

What can I do?

---

### Post by unevenflow on 2012-08-19
Hey, How did you try to install it?

---

### Post by OM55 on 2012-08-19
Did you notice that many of the errors and warnings refer to an NVidia driver? You did mention that you were trying to install an ATI Radeon driver... those are not the same...

Could it be that you are accidentally trying to install an NVidia driver on an ATI Radeon hardware (thus the error and unsuccessful installation)?
Or the other way around - you actually have an NVidia hardware and you are trying to install the ATI Radeon driver on it, resulting in those errors and unsuccessful installation)?

---

### Post by GazaIan on 2012-08-19
> **OM55 said:**
> Did you notice that many of the errors and warnings refer to an NVidia driver? You did mention that you were trying to install an ATI Radeon driver... those are not the same...

Could it be that you are accidentally trying to install an NVidia driver on an ATI Radeon hardware (thus the error and unsuccessful installation)?
Or the other way around - you actually have an NVidia hardware and you are trying to install the ATI Radeon driver on it, resulting in those errors and unsuccessful installation)?


Holy crap lol I didn't even realize, not sure how I missed that. Oddly though, the driver is listed as an ATI/AMD Driver under additional Drivers. I tried installing the other driver listed and suddenly it worked (for the past 16 months, the second one wouldn't even download, but then it chose to work just minutes after I made the post). From the looks of it seems all is good now, I guess I relied on Ubuntu too much for that. But I do have one question...

The first time I used Ubuntu was 9.04, back when GNOME was still mainstream and the windows were all jiggly when you moved them after installing the correct video drivers. Any way to get that into the current version of Ubuntu? It was one of the things that made Ubuntu distinct from other OSes.

---

### Post by OM55 on 2012-08-19
Sure, you can install CompizConfig Setting Manager, it has MANY interesting effects not only on Windows. 

You can install it from Software Center (look for CompizConfig) or in type in terminal:
```
sudo apt-get install compizconfig-settings-manager
```It will be installed in: Applications -> System Tools -> Preferences
or type in terminal:
```
ccsm
```To get the effect you asked for (Wobbly Windows) when you launch it, click on 'Effects' on the left pane, and then check the 'Wobbly Windows' effect on the right. You can also click on that icon and make changes to all the parameters that control this effect.

Enjoy!

(and now you can change this thread to 'Solved' for others to see)

---

### Post by GazaIan on 2012-08-19
> **OM55 said:**
> Sure, you can install CompizConfig Setting Manager, it has MANY interesting effects not only on Windows. 

You can install it from Software Center (look for CompizConfig) or in type in terminal:
```
sudo apt-get install compizconfig-settings-manager
```It will be installed in: Applications -> System Tools -> Preferences
or type in terminal:
```
ccsm
```To get the effect you asked for (Wobbly Windows) when you launch it, click on 'Effects' on the left pane, and then check the 'Wobbly Windows' effect on the right. You can also click on that icon and make changes to all the parameters that control this effect.

Enjoy!

(and now you can change this thread to 'Solved' for others to see)

Beautiful, thank you very much!

---

