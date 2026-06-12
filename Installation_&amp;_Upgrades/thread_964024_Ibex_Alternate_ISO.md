---
title: "Ibex Alternate ISO"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by meatlegs on 2008-10-30
Hello all,
I've downloaded the Intrepid Alternate CD ISO and I'm planning on mounting this on my hard drive and upgrading from Hardy. 
Has anyone else tried this with success?

Cheers

---

### Post by tajgenie on 2008-10-31
I'm trying to do the same thing right now. When it asks if I want to download additional packages, I say no, but then later it tries to download them anyway instead of using just the packages on the cd. If I'm not connected to the internet, the upgrade fails and won't continue. If I am connected it downloads ok, but my connection is too slow for this to be acceptable.

Anyone know why this is happening?

---

### Post by cbstryker on 2008-10-31
I'm getting the EXACT same problem/symptom. The servers seem to be flooded with people getting the update that I'm getting an average 15kbps which says it'll take more than 2 days. My solution was to download the alternate install iso via torrent and update. When it asks if I want to get the latest packages from the internet I say no but it downloads anyways. I started the upgrade over with my internet connect disabled and then it gives me an error saying "could not fetch" etc etc and will abort. MAJOR flaw if you ask me!

I LOOOVE Ubuntu and this is a bit disappointing. I expect this from MS, not Ubuntu.

---

### Post by tajgenie on 2008-10-31
Now that I think about it, I tried to update via internet before I tried the alternate cd. Maybe because I started the download and then cancelled, ubuntu is confused?

I checked my **/etc/apt/sources.list** and there are a bunch of *intrepid* sources in there. I replaced it with an older version (with only *hardy* sources), and am now trying the **cdromupdate** again. I think this might just work - I will report back when I know if it does or not.

---

### Post by tajgenie on 2008-10-31
The cdrom updater appears to have added intrepid sources to my sources.list, but now when it says "getting packages" the number is reduced to 1060 total packages (about half what it said before). It's now Installing the packages, and I should be in Intrepid soon! 

So try what I did cbstryker, and you may just be in Intrepid soon too!

---

### Post by me121 on 2008-10-31
i started downloading the updates, but it was running to slow and took longer than all night, and since i can't seem to schedule it to start during off-peak times, i will get the alternate-cd.

but are you saying that if i've started the download the updates via the web, but now want to do the rest by cd, i will need to change the sources? this sounds like it will break the upgrade, are you sure it works? thanks!

---

### Post by quonsar on 2008-10-31
same deal here - i d/l the iso torrent and then the upgrade took forever downloading packages anyway when i thought i would be avoiding the crush on the servers. but aside from that it went well - i just feel like i wasted the time it took to d/l the alternate iso!

---

### Post by Dumdideldum on 2008-10-31
I have used the alternate iso (downloaded via torrent) to upgrade and had other problems - a kernel panic (posted in this forum) - but there is afair (was already after midnight ;) ) an option to select, if the updater just should use the packages on the CD or fetch those packages, which are newer than on the CD and/or aren't on the CD, from the internet.

But it took even though very long and in my case, didn't finish at all.

---

### Post by meganox on 2008-10-31
Worked fine for me, I started with a completely clean and up to date Hardy install (don't ask why) and it didn't download anything, but that's because I haven't any packages installed that aren't on the CD.  The packages it downloaded for you guys are updates to the extras you've installed from repos, so it wasn't wasting your time at all :)

---

### Post by tajgenie on 2008-10-31
> **me121 said:**
> i started downloading the updates, but it was running to slow and took longer than all night, and since i can't seem to schedule it to start during off-peak times, i will get the alternate-cd.

but are you saying that if i've started the download the updates via the web, but now want to do the rest by cd, i will need to change the sources? this sounds like it will break the upgrade, are you sure it works? thanks!

I just booted into Intrepid and it's working :)

> **Dumdideldum said:**
> I have used the alternate iso (downloaded via torrent) to upgrade and had other problems - a kernel panic (posted in this forum) - but there is afair (was already after midnight ;) ) an option to select, if the updater just should use the packages on the CD or fetch those packages, which are newer than on the CD and/or aren't on the CD, from the internet.

Right, but our problem was that the option ignored our choice - it was downloading the web packages even if I said "no, only use the cdrom". Resetting my sources did the trick, and got that option working again.

---

### Post by cbstryker on 2008-10-31
> **tajgenie said:**
> The cdrom updater appears to have added intrepid sources to my sources.list, but now when it says "getting packages" the number is reduced to 1060 total packages (about half what it said before). It's now Installing the packages, and I should be in Intrepid soon! 

So try what I did cbstryker, and you may just be in Intrepid soon too!


Well my sources.list had only hardy entries. What I did do though, was change the server on the software sources box to "main" instead of "canada". For whatever reason, after I did that, the update no longer tried to download anything. I still think there's a significant bug that needs to be filtered out still with the update manager, but otherwise it has gone well so far. Thank for the sugestion tajgenie.

---

### Post by tajgenie on 2008-11-05
> **cbstryker said:**
> Well my sources.list had only hardy entries. What I did do though, was change the server on the software sources box to "main" instead of "canada". For whatever reason, after I did that, the update no longer tried to download anything. I still think there's a significant bug that needs to be filtered out still with the update manager, but otherwise it has gone well so far. Thank for the sugestion tajgenie.

Interesting.... Well at least you got it working, albeit for an even stranger reason!

---

