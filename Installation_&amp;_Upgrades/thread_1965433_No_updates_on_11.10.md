---
title: "No updates on 11.10?"
date: 2012-04-25
forum: Installation &amp; Upgrades
---

### Post by CWM800 on 2012-04-25
Hi I am new, Just installed Kubuntu today...

I am using 11.10 I noticed no green cog saying I have updates.... So is everything up to date?

I installed adept, I was googling for where the updater was... even tried a sudo apt-get update -f... nothing... 

I would of thought there'd be updates since this 11.10 came out in Nov, of last year

Please Advise.

Thanks,
Christopher

---

### Post by PaulW2U on 2012-04-25
Well 11.10 was actually released in October last year but since then the kernel, KDE and LibreOffice will all have been updated. Their updates alone will come to over 300MB.

So can you confirm that

```
sudo apt-get update
sudo apt-get upgrade

```

tells you that you are fully up-to-date after listing all the repositories that you have enabled and that there are no errors.

By the way, Kubuntu 12.04 will be released tomorrow!

---

### Post by CWM800 on 2012-04-25
> **PaulW2U said:**
> Well 11.10 was actually released in October last year but since then the kernel, KDE and LibreOffice will all have been updated. Their updates alone will come to over 300MB.

So can you confirm that

```
sudo apt-get update
sudo apt-get upgrade

```tells you that you are fully up-to-date after listing all the repositories that you have enabled and that there are no errors.

By the way, Kubuntu 12.04 will be released tomorrow!

Hi Paul,

I just ran that command is this is what I got:

[IMG]http://i16.photobucket.com/albums/b10/cmarlow/Websites%20I%20am%20on/Forums/Kubuntu/April%2030th%202009/snapshot3.png[/IMG]

as you see Ive downloaded 11.04 --- Ive always had problems with the .10 versions... I am tempted to slap 11.04 on here... until I see if version 12 works out... and if I see good results, upgrade from 11.04...

--- Christopher

---

### Post by techsupport on 2012-04-25
Keep updating the system with 

sudo apt-get  update
sudo apt-get upgrade

Reboot

And then do it again until there are no more updates.

:popcorn:

---

### Post by QIII on 2012-04-26
There should be no reason to update and upgrade repeatedly.  
  
  All the updates should be downloaded (which may take a long time  depending on the number of updates) and upgraded in one iteration.  A reboot will likely be required because the kernel has been upgraded.
  
  Also, I recommend 
   
   ```
sudo apt-get dist-upgrade
```   dist-upgrade does all that upgrade does, with the addition of attempting to resolve dependency issues.

Never answer yes if you get a message saying "The following packages will be held back..."  That is a partial upgrade and often results in a borked system.  Also, pay attention to anything that says "The following packages will be removed: ", especially when it lists your DE.  That will definitely give you a headache.

---

### Post by QIII on 2012-04-26
By the way, Kubuntu 12.04 is working out just fine.  I've been using it as my primary since the first Alpha.

---

