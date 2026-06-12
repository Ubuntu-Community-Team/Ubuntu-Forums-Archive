---
title: "Upgrading failure from 8.04 LTS to 10.04 LTS."
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by AlbertCarlosEggs on 2010-05-05
Hi, when I try to upgrade from Hardy Heron 8.04 LTS towards Lucid Lynx 10.04 LTS (via internet, not ISO-CD), following error is displayed:

" Could not install the upgrades
Error during commit
'E:Couldn't configure pre-depend jre for openoffice.org-writer2latex, probably a dependency cycle.'
Restoring original system state "

I deleted all Open Office package and other options were checked, but no success. Hardware: Notebook Toshiba Qosmio G45-AV480. Suggestions & tips are welcome. Thanks, Albert

---

### Post by recluce on 2010-05-05
> **AlbertCarlosEggs said:**
> Hi, when I try to upgrade from Hardy Heron 8.04 LTS towards Lucid Lynx 10.04 LTS (via internet, not ISO-CD), following error is displayed:

" Could not install the upgrades
Error during commit
'E:Couldn't configure pre-depend jre for openoffice.org-writer2latex, probably a dependency cycle.'
Restoring original system state "

I deleted all Open Office package and other options were checked, but no success. Hardware: Notebook Toshiba Qosmio G45-AV480. Suggestions & tips are welcome. Thanks, Albert

"JRE" means Java Runtime Environment. At this point you should ask yourself if you ever did anything manually to your Java install, like installing a Sun Java package directly.

Avenues that I do see: disable all PPAs in your software sources. 
Run "aptitude install -f" (use search to see if I got that right, it is just about bed time for me and my thinking gets fuzzy) to repair any broken packages and unresolved dependencies. 
If that does not work, try to remove Java before the upgrade, you can always add it back later.

Ok.... off to bed... ):P

---

### Post by terminal*optimist on 2011-06-18
hi  

just thought i'd post this in case there are any other people out there who have this problem and still haven't resolved it... i have had ubuntu hardy 8.04 heron sitting in a dell laptop i don't use much and didn't connect to the internet until recently and it came up for me once i managed to do the 1200+ updates which you need to do before upgrading, which is a story in itself,  and started trying to upgrade to lucid 10.04 lynx... 

was solved, eventually, by doing the 'aptitude install -f' thing in the terminal which seemed to do something to do with libwriter2latex files. that on its own was not enough though, and i went to synaptic package manager to see if i could uninstall java (as other threads suggested) without getting rid of all of open office (which it didn't want to do because of other 'dependency issues')... turns out that java wasn't *in*stalled (or a much older version was active) even though i have never touched any of these settings. so i installed (or applied? it seemed to be ready, downloaded and just sitting there but not activated) java 6 and then the upgrade worked. HOWEVER there were lots of errors with openoffice stuff and it said that my system may be in an unusable state, restoring settings etcetc. 

but after rebooting there was an open office update waiting to happen which i presume was adressing those issues... so i let it run and everything seems to work fine... for now:D (though still braced for full system collapse!)

---

