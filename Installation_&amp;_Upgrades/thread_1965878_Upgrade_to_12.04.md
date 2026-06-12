---
title: "Upgrade to 12.04"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by chiparawe on 2012-04-26
Have just tried to upgrade from 11.10 to 12.04 using update manager and keep getting the following message:
Could not download the release notes. Please check your internet connection.
Connection is fine so I am a little confused.

---

### Post by jadtech on 2012-04-26
the server is very busy today  keep trying in your terminal to 
```
 sudo apt-get update 
sudo do-release-upgrade 
```

using do-release-upgrade  should upgrade  right in the terminal everything printed out as each part  down loads and installs very interesting  this way you have a print out of everything that happens during your upgrade before you boot you could copy and save it incase there is trouble ..

---

### Post by chiparawe on 2012-04-26
Ok that makes sense. Will just keep trying. Many thanks for quick reply

---

### Post by iqoniq on 2012-04-26
I noticed a few problems last night when I was trying to download some software from the Software Centre, and I'm having the same problem as you right now so you're not alone :|

---

### Post by Mark Phelps on 2012-04-26
> **chiparawe said:**
> Have just tried to upgrade from 11.10 to 12.04 using update manager ...

You DO know, that if the upgrade leaves you with a system that has problems, there's no way to roll-back to what you have now. Right?

My own approach has been to WAIT a few weeks AFTER the rlease and check the forums to see what problems folks are encountering.

---

### Post by daniber on 2012-04-26
> **Mark Phelps said:**
> You DO know, that if the upgrade leaves you with a system that has problems, there's no way to roll-back to what you have now. Right?

My own approach has been to WAIT a few _weeks_ AFTER the rlease and check the forums to see what problems folks are encountering.

Months...not only weeks.
;-)

---

### Post by chiparawe on 2012-04-27
Successful upgrade last night. I only upgraded because I seemed to have lost my HDMI output to my TV when I upgraded from 11.04 to 11.10 and was hoping I'd get it back in 12.04 but no luck. Hey ho.

---

