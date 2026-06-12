---
title: "compiz: black windows"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gator_ml on 2010-04-11
I have a pretty seasoned laptop with an ATI Radeon RV250 graphics chip (using the RADEON driver). Until recently, the machine was running Ubuntu 9.04 without major problems. With 10.04 impending, I thought it was time for an upgrade; I first upgraded to 9.10 and because this caused some problems went on to 10.04 (so this is not strictly a "Lucid Lynx" issue)

Originally, some applications (most prominently firefox) were totally unusable, because the application windows were straight black (Dialogs/context menus were still visible). The same was true for the desktop background. Mysteriously, after investigating this for a while and rebooting the machine several times this phenomenon disappeared,  although I had not really changed anything.

In certain contexts a similar issue still persists, however: certain previews from compiz plugins like "Expo" or "Wall" are almost unrecognizable, because everything is shown almost black (actually, It isn't totally black, just too dark to recognize) and there is no visible indication of the current desktop.

Has anybody else seen similar issues (as said, even though I didn't investigate it further there, these problems obviously were introduced already with 9.10) and has any idea what to do about it?

Regards, 
                                 Peter

---

### Post by cianca on 2010-04-21
I have the same issue with compiz. Everything is too dark in some plugins. I'm using an ATI Radeon 9200 SE

Edit: It seems to be a problem with some ati cards.

I fix it doing:```
#echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf
```and rebooting.

More info: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539163/]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539163/")

---

### Post by gator_ml on 2010-04-24
> 
More info: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539163/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539163/)thanks for the hint - at least, I'm not the only one ...

Unfortunately, on my machine things get even worse with modesetting turned off. More precisely, the effect that I originally was struggling with (totally black desktop background, some programs like firefox showing black windows) occurs, when kms is off. It seems like after the dist upgrade, the machine originally ran without kms, while later kms somehow was turned on (without me having changed any related settings ... ;)

---

