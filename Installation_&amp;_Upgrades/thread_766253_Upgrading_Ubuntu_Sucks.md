---
title: "Upgrading Ubuntu Sucks"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by yogo on 2008-04-25
I have spent 8 hours trying to upgrade Ubuntu through the update manager. Why on earth does this method even exist for upgrading. For over the last hour the upgrade manager has been fetching 1185 out of 1186 files. This does suck bigtime and I love Ubuntu, so much that I may boot into Windows twice a year at best.

However the upgrade process should be much better. On the plus side, I am now downloading Hardy Heron and am at 90% and just started ten minutes ago. As I type the download is now at 97% and now it is complete.

I so much want to kill the update manager as it is going nowhere, less than 1kb. My cable is fast as I got the complete HH iso in 17 minutes. Why should the update manager virtually stop and getting less than 1kb is stopped IMO.


As I type, it finally fetched all 1186 files and is now installing them BUT I will never update through the update manager again to a new distro.

Sorry for my rant but I started before seven and it is now almost three am, This is too painful and should not be used as a method to upgrade to a newer version IMO


Still I do love Ubuntu.

---

### Post by hyper_ch on 2008-04-25
Do you think you're the only one trying to upgrade right now?

How big is the the total upgrade for you?

Now think that several thousand people want to do the same on the same server...

----

Is there a better way?

Yes, download the alternate install cd through BitTorrent and use it as medium for upgrading!

----

So, basically upgrading ubuntu does not suck but your way of trying to do it sux

---

### Post by freestylekyle on 2008-04-25
It's prob. only that slow because it's the first day it's out, all the servers are backed up. That said I never upgrade any OS, I've seen nasty stuff happen. I mount 20 GB at / and the rest at /home wipe and reinstall to the / partition. You have to reinstall all the apps but all you data's still there.

---

### Post by flagger on 2008-04-25
took me 6 attempts to upgrade through the upgrade manager from 7.10. I was en connecting to my local isp's mirror (free quota yay), and it was bombing out. keep on trying, but it sounds to me that it may have 'frozen up' if its been trying to get the last package for ages.

---

### Post by yogo on 2008-04-25
Yes I do realize that many other people are trying to download as well. Actually I would not have been upset if the Hardy Heron iso which is 699,1 mb took a while, that downloaded in less than 17 minutes.

Actually I did not think it would be as bad as it was since I was upgrading to Gutsy. Please do not shoot the messenger here but but back in the day when I downloaded Vista beta, it was never this slow.

I admit I did it the wrong method, but that was my point that that method should not even exist, way too painful to upgrade through the update manager even if the servers are not overloaded.

---

### Post by hyper_ch on 2008-04-25
> **yogo said:**
> Please do not shoot the messenger
I did not... you said upgrading ubuntu sucks and I said your way to do it sux... ;)


> **yogo said:**
> here but but back in the day when I downloaded Vista beta, it was never this slow.
Well, nobody wants Vista, so no wonder it was never this slow ;)

> **yogo said:**
> I admit I did it the wrong method, but that was my point that that method should not even exist, way too painful to upgrade through the update manager even if the servers are not overloaded.
This method is the normal upgrade for APT... so you can't actually cancel that out as it would be one of the basic function of the package management in debian based distros.

---

### Post by yogo on 2008-04-25
Well here is where I am at, I will be upgraded back to Gutsy shortly for a second go around. First time I had it  for a week. I found that my desktop was faster using Beryl in Feisty so this time around I should be able to get Gutsy and Compiz up to speed.

Seeing a few problems with HH, I will wait a while before upgrading and see if the bugs get worked out.

PS I thought I got the title here changed (toned down) but I guess it only shows when clicking on this thread

---

### Post by yogo on 2008-04-25
@hyper_ch

I now have Gutsy installed, it found 53 obsolete packages to be removed, I skipped that as it had Beryl in that list and last time I installed Gutsy, it removed Beryl.

Can I remove all packages in local and obsolete, it lists wine there as well as a few other programs, am I to assume these all are updated so they can be removed?

TIA

---

### Post by agent8131 on 2008-04-25
I have an idea.  Since you said there was 1 package you couldn't get I'd think that maybe that package was from a different repository.

Do you have packages from medibuntu?  I noticed they were down earlier today.  If you could remove any 3rd party repositories that could clear up your problem.

On the other hand, waiting a bit is not a bad idea either.

> how do I find the other obsolete packages

I use deborphan.

---

### Post by kellemes on 2008-04-25
> **yogo said:**
> ..() but now how do I find the other obsolete packages?


[http://www.berthon.eu/wiki/foss:ubuntu:aptclean]("http://www.berthon.eu/wiki/foss:ubuntu:aptclean")

I use the following..

```
sudo apt-get autoremove
```

---

### Post by yogo on 2008-04-25
> **kellemes said:**
> [http://www.berthon.eu/wiki/foss:ubuntu:aptclean](http://www.berthon.eu/wiki/foss:ubuntu:aptclean)

I use the following..

```
sudo apt-get autoremove
```

Thanks, that worked better than using Synaptic.

---

### Post by hyper_ch on 2008-04-25
I haven't used gutsy for months and gutsy has also compiz-fusion, why do you still have beryl in there?

---

### Post by yogo on 2008-04-25
> **hyper_ch said:**
> I haven't used gutsy for months and gutsy has also compiz-fusion, why do you still have beryl in there?


I left Beryl in on purpose (I should have removed all obsolete files) because last time I upgraded to Gutsy Compiz did not work as smooth as Beryl did.

However Beryl does not work with Gutsy so I removed it. Compiz does work just at times it seems a little heavy or does erratic movement when Beryl was smooth. 

Compiz is working, funny in Feisty Beryl worked better, in Gutsy, Beryl did not work at all. But Compiz in Gutsy is not as smooth as Beryl was in Feisty.

It is jerky and jumpy at times, especially when grabbing a window from the corner and dragging it, not near as smooth as Beryl was.

All this is probably due to the fact that I have a Dell with onboard graphics and not an actual graphics card.

---

