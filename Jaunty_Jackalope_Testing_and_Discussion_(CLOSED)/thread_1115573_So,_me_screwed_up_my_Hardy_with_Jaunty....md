---
title: "So, me screwed up my Hardy with Jaunty..."
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starmartyr on 2009-04-04
I have a new 250 GTS nVidia card, and had been working on getting the driver resolved.  Along this journey it seems I added in some Software Source, and later Update Manager stated I had 437 updates available.  It didn't dawn on me to not update this, so....I updated.  Now my system is no longer Hardy, but Jaunty!  Eeeek!!!  So network connections when running it either.  I am currently on this forum thanks to my Hardy CD.

So, can I revert back to Hardy or is that installation gone?

---

### Post by Melk79 on 2009-04-04
Yeah, it sounds like you've replaced your Hardy setup with Jaunty beta.  You may have done that while trying to fix your nvidia issue. Out of curiousity, did that properly setup your nvidia card?

Did you mean to say you have no nentwork connection without the live CD?  What wireless card/ networking setup do you have?

---

### Post by plucky on 2009-04-04
> **Starmartyr said:**
> I have a new 250 GTS nVidia card, and had been working on getting the driver resolved.  Along this journey it seems I added in some Software Source, and later Update Manager stated I had 437 updates available.  It didn't dawn on me to not update this, so....I updated.  Now my system is no longer Hardy, but Jaunty!  Eeeek!!!  So network connections when running it either.  I am currently on this forum thanks to my Hardy CD.

So, can I revert back to Hardy or is that installation gone?

You should not be able to upgrade from Hardy to Jaunty without going through Intrepid.

From a terminal,post output of ```
lsb_release -a && uname -r
```

---

### Post by Starmartyr on 2009-04-04
I had that wrong.  I was using Intrepid.  My laptop uses Hardy.

So, i am currently reinstalling Intrepid onto my system.  I've got the weekend to do undo this mess.

I did get my nvidia card running using the drivers 173.XX and 180.44.  For some reason I reverted back to 173.XX and tried playing World of Warcraft, and it failed.  So, I went back to 180.44, and for some odd reason it failed, too.  Tried working with the WOW config file, and it still failed to run.  I then noticed I could do some updates.  Regular updating failed, and so I went to Terminal and did 'apt-get update" and then i had Jaunty.

I only wish there was a warning message that popped up stating, "Yo, you are updating your system from Intrepid to Jaunty. You sure you wanna continue?"  If it had this I wouldn't have ever seen Jaunty.  At least not yet.

Anyway, Jaunty did fail to connect to my wired network.  Intrepid LiveCD has no issues.  My mobo is MSI K9NBPM2-FID AM2 NVIDIA Quadro NVS 210S Micro ATX.

---

