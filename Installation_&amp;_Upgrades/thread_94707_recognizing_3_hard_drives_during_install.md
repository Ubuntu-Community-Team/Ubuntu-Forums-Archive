---
title: "recognizing 3 hard drives during install"
date: 2005-11-24
forum: Installation &amp; Upgrades
---

### Post by trasa on 2005-11-24
Hi, I'm kicking Windows out of my computer and installing Kubuntu. How do I make Kubuntu recognize all my 3 hard drives? Can this be done during the install?  Thanks.

---

### Post by yesplease on 2005-11-24
It wiil recognize them during install, no problem there.

When you are a beginner it is good to have access to an OS that you are familiar with. Perhaps you can leave Windows on one of those partitions. Or can you work from another computer?

Games, for instance, are often supported on Windows only.

---

### Post by trasa on 2005-11-24
Ah, well maybe I should be a little bit more specific. I installed Kubuntu 5.10, no problem there. I installed it on my smallest drive. Now I want to access my other 2 drives.
  This I can't do now.
  Should the hard drives be formatted in any shape or form? They are right now filled with files from my windows install, files I don't want to keep.

---

### Post by aysiu on 2005-11-24
Yes. Install QTParted (see the first link, then second link in my sig).
Then, reformat the two other drives as Ext3.

---

### Post by trasa on 2005-11-24
Thanks very much. I will try - and I will succeed!

---

### Post by trasa on 2005-11-24
So, I followed as best I could Aisoy's response. It didn't go so well. I updated and probably got Qparted. But I could not find it. So, I rebooted my computer and it got "stuck" and wouldn&#168;t boot up.
  My question. When I try to install again (thatis  my plan), what do I do during install to get all 3 drives recognised? Or is there something that has to be done once I've installed Kubuntu on on one drive and booted up?

Lucky for me I kept Windows on my laptop, so I can ask these silly questions. All help is greatly appreciated.

---

### Post by aysiu on 2005-11-24
[QUOTE=trasa]So, I followed as best I could Aisoy's response. It didn't go so well. I updated and probably got Qparted. But I could not find it.[/quote] Sometimes they appear in the menu--sometimes they don't. You can still type the command in the "Run" dialogue box: ```
qtparted
``` 

> When I try to install again (thatis  my plan), what do I do during install to get all 3 drives recognised? Or is there something that has to be done once I've installed Kubuntu on on one drive and booted up? If they're all plugged in, they should all be recognized.[/QUOTE]

---

