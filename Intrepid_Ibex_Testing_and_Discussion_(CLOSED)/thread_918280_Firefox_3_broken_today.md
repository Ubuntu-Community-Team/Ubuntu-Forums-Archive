---
title: "Firefox 3 broken today"
date: 2008-09-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by caryb on 2008-09-12
Well I know why I have Seamonkey on standby:) After todays upgrade to FF3 none of my default settings work & all of the function buttons are greyed out & non usable.

Am I on my own with this one?


Cary

---

### Post by SeanHodges on 2008-09-12
Is this using an Intrepid beta? I have no problems in Hardy...

---

### Post by wolterh on 2008-09-12
What version are you running? I'm running 3.0.1 perfectly, puting into exclusion that when I'm loading pages the mouse is hidden, sometimes.

---

### Post by caryb on 2008-09-12
Am running v 3.0.2


Cary

---

### Post by Foaming Draught on 2008-09-12
Sorry caryb, everything's fine with FF 3.0.2 after my upgrade this morning.  I got it from the main server, not the Australian mirror.

---

### Post by FishRCynic on 2008-09-12
had to synaptic to resolve some upgrade issues - had partial distribution  - once done - everything upgraded ok here too.

---

### Post by knattlhuber on 2008-09-12
Could that be the result of a conflict resulting from non-compatible add-ons? I would go to ~/.mozilla/firefox, save a copy of my profile folder to the Desktop and then erase the profile folder and start FF again. If that works you could then copy your bookmarks back into the new profile and re-install your extensions.

---

### Post by caryb on 2008-09-12
I removed the profile but that didn't work, when I try to fire up FF it tells me there is a another instance running! pa aux does not find a instance, I uninstalled FF & rebooted for good measure & tried to fire up ff & nothing there, so far so good, I reinstall ff & get the same message:confused: but still no ff runing in ps aux


Now I'm really stumped.


Cary

---

### Post by Slug71 on 2008-09-14
Is this a 64 bit thing or what? Firefox 3 sucks otherwise. I have 3.0.2, xulrunner 1.9.0.2 and Flash 10-B2 which all worked great for one day(the day 3.0.2 came out) and now im back to my normal issues with FF crashing on Flash sites. Could this be due to the nspluginwrapper update that came in a couple days ago?? Im pretty sure it was after that, that i started having issues again.

---

### Post by SeanHodges on 2008-09-14
> **Slug71 said:**
> and now im back to my normal issues with FF crashing on Flash sites. Could this be due to the nspluginwrapper update that came in a couple days ago?? Im pretty sure it was after that, that i started having issues again.

Correction, you're having problems with **Adobe Flash** crashing on Flash sites. 

Firefox has no direct interaction with Flash, it farms the content to the embedded Flash player (whether that be Adobe Flash player, Gnash player, etc...).

I would suggest that your problem is more likely to be a problem with nspluginwrapper. I'm using FF 3.0.2 with Gnash (64bit native build) and its working perfectly.

---

