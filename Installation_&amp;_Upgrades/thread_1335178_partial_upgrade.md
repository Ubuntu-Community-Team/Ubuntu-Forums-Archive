---
title: "partial upgrade"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by DarinB on 2009-11-23
i get this screen everytime i click on my auto updates that get sent about once a week.  from cononical i guess? the screen shots will tell the story i don't know what is causing this partial upgrade warning???[ATTACH][ATTACH][ATTACH]137295[/ATTACH][/ATTACH][/ATTACH]

---

### Post by DarinB on 2009-11-23
sorry the first one should be at the end after i click run partial update.

---

### Post by Bunnybugs on 2009-11-23
> **DarinB said:**
> i get this screen everytime i click on my auto updates that get sent about once a week.  from cononical i guess? the screen shots will tell the story i don't know what is causing this partial upgrade warning???[ATTACH][ATTACH][ATTACH]137295[/ATTACH][/ATTACH][/ATTACH]

Well, it looks like the downloads are unavailable... wich distro/version are we talking about??

The screens don't really look like Ubuntu 9.04 to me;), at least, the whole desktop looks like something else... an RPM distro or some?

---

### Post by DarinB on 2009-11-23
nope its all 9.04 jaunty,

---

### Post by DarinB on 2009-11-23
maybe it is because when i get the partial upgrade screen no matter what the package is inside...i close on the partial upgrade and then click the install updates then they install and then the partial upgrade screen comes back. then i click it and get the above results. it seems that something is not correct and this warning keeps on coming up.

---

### Post by DarinB on 2009-11-23
here are my software sources is this the problem?[ATTACH]137300[/ATTACH]

---

### Post by presence1960 on 2009-11-23
> **DarinB said:**
> here are my software sources is this the problem?[ATTACH]137300[/ATTACH]

tick the two unchecked boxes.

If you have 3rd party software installed that software can not be upgraded from apt usually.

---

### Post by kansasnoob on 2009-11-23
Go to Synaptic, click on Reload, when it's stopped running click on Mark all upgrades, then click on Apply. 

**[COLOR="Red"]Do not proceed with the upgrade![/COLOR]**

Rather than just proceeding you'll see that a new window pops up:

[ATTACH]137302[/ATTACH]

Click on Show Details. You can then copy-n-paste the text in that window here, so do just that.

Then for now click on Cancel, and close Synaptic (it will ask you whether you want to discard the marked changes - **yes you do for now**).

Then we can see exactly what's going to be upgraded, installed, or removed.

Edit: be sure you c&p all of the text from that window here, you may have to do some scrolling to get it all!

---

### Post by DarinB on 2009-11-23
here it is!

firefox will be downgraded
firefox-3.0 will be downgraded
firefox-3.0-branding will be downgraded
firefox-3.0-gnome-support will be removed
firefox-gnome-support will be removed

---

### Post by DarinB on 2009-11-23
BTW, i use firefox 3.015 i had nothing but problems with 3.5xx. when i did a clean reinstall i stayed with the 3.013 but it ended up upgrading before i could stop it now i am at 3.015 and no problems. a little choppy on HD at ABC.com or CBS.com but i heard that was an adobe plug in problem with all linux not sure but it sucks to have to go to windows partition just to see a HD show on line. **I regress I am using firefox 3.015**

---

### Post by kansasnoob on 2009-11-23
Arrgh, I don't like the look of that.

I'm not real sure how to deal with it though.

For now I'd just sit on that and NOT remove or downgrade. I'm sure someone else will have an answer.

I'm using 3.5.5 in Jaunty.

---

### Post by phillw on 2009-11-23
I know lovinglinux doesn't hate me for doing this  (Well, he says he doesn't) ... He keeps an excellent thread over here for all things FF

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

His how-to's and backup that he provides is really good. It is a busy thread and will take a bit of reading through - If you can't find an answer, post a question & he will reply.

He may not be able to 'talk you through' your partial update stuff - But he sure will be able to talk you through safely updating to the new FF, which will remove that problem

Regards,

Phill.

---

### Post by DarinB on 2009-11-23
Well As they say God protects drunks and fools. 
i didn't see a response so i did apply and now i am using firefox 3.08 and it screams. so far no problems!
when i hit update i don't get the partial upgrade i will see next time i get auto updates and we will see. i think it did the trick but very risky indeed.

---

