---
title: "Update via update manager Karmic -&gt; Lucid"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by abickerton on 2010-04-29
Having suffered badly with the upgrade from Jaunty to Karmic on my home PC I'm more that a little reluctant to go through it all again so there I'll most likely to a clean install.

The major problem I'm now facing is with my office Desktop. Dual head Karmic beast of a machine. I'll have to update using the update manager.

What I need to know is ...**will the update work?**

Let me make this clear for those that may be skimming this post.
[CENTER]
[SIZE="7"]
[COLOR="Red"]THIS IS MY DAILY PRODUCTION WORKSTATION,
A CLEAN INSTALL IS NOT AN OPTION![/COLOR][/SIZE][/CENTER]

I cannot spend days getting everything backup and running, This is my daily work pc. If I cannot just update and have it remain functional, then ultimately I cannot justify running Linux to my boss.

I suspect many others are in the same situation right now.

---

### Post by phillw on 2010-04-29
If your /home is on its own partition, regardless of how the update goes, you are in no danger of losing data. I updated 9.04 --> 9.10 via update manager and had no problems. I haven't tried with my 9.10 yet as 10.04 has been delayed. If you are concerned, wait a day or two and watch the forum. I have a full LAMP server on my 9.10, it upgraded seemlessly from 9.04 - I will be doing the update of 9.10 tomorrow.

Regards,

Phill.

---

### Post by abickerton on 2010-04-29
That's not really what I meant. I'm more concerned with having to justify doing nothing for > 1 hr. I need the updgrade to just work as if it was a normal update.

Re installing flash & java I can live with. More than an hour without a working pc, not so much.

For the record. /home is on the same partition but that can be dealt with.

---

### Post by guv999 on 2010-04-29
Hi - I too had issues updating to Karmic and had to do a clean install in the end.   
I updated to the Lucid RC two days ago, and everything has gone well.   Very stable and no issues at all. :P 
The only benefit I am not seeing is an improved boot time which has remained constant at 40 secs, but I am not too concerned about that

---

### Post by bobnutfield on 2010-04-29
> **abickerton said:**
> That's not really what I meant. I'm more concerned with having to justify doing nothing for > 1 hr. I need the updgrade to just work as if it was a normal update.

Re installing flash & java I can live with. More than an hour without a working pc, not so much.

For the record. /home is on the same partition but that can be dealt with.

If you have no third party software installed (other than that supported by Ubuntu or available via Synaptic), then you have a reasonably good chance of a smooth upgrade.  But how long it will take depends on a few variables.  If you are upgrading online, then I would wait a few days until the Ubuntu servers cool down.  Right now they will be jammed packed.

Also, the speed of your connection is another variable.  All of my upgrades have been online and have gone smoothly.  But upgrades CAN go loopy.  It can happen, so there are no guarantees.

---

### Post by snowpine on 2010-04-29
There is no way I would upgrade a production machine on day zero of a new release. :) TEST the upgrade first on a non-production machine, then you will have your answer. Also hang out on these forums for a few weeks; if there are major problems with the update, you'll read about it. ;)

---

### Post by abickerton on 2010-04-29
LOL, you're funny. you think there's more than one of these in the building... Intel Quad core, 8GB RAM, Nvidia 260 mumble... 
The only testing time for the an upgrade is when I do it for real.

The plan so far is to wait for at least 2 weeks. After all, if it's shown that installing what is effectively equivalent to a Windows Service pack knocks me out of action for more than an hour, I'll be told to use the Vista partition or bend over a use a Mac. 

<rant>
Until update-manager -d is reliable to the point that this thread would not be needed, how coulb business be expected to adopt Linux en mass. It just isn't going to happen.

As for the "Just make a clean install crowd"... I have one thing to say, but I won't type it.
</rant>

---

### Post by snowpine on 2010-04-29
> **abickerton said:**
> 
Until update-manager -d is reliable to the point that this thread would not be needed, how coulb business be expected to adopt Linux en mass. It just isn't going to happen.

There are plenty of businesses using Linux en mass and guess what? They test major upgrades before applying them on production machines (smart businesses do this for Windows and Mac deployments too). Would you buy a car without taking it for a test drive? :)

---

### Post by abickerton on 2010-04-30
Your telling me that a business with say 200 pcs (all different in some way). will test the a new upgrade every six months. Even though the update manager is constantly stating a new release is available?

Seems to be a recipe for disaster IMHO.

Anyways trying an update on the spare laptop now, I'll report back as soon as.

---

### Post by snowpine on 2010-04-30
> **abickerton said:**
> Your telling me that a business with say 200 pcs (all different in some way). will test the a new upgrade every six months. Even though the update manager is constantly stating a new release is available?

Seems to be a recipe for disaster IMHO.

Anyways trying an update on the spare laptop now, I'll report back as soon as.

Personally if I were running a business like that, I would upgrade every 2 years (at the most) and you can bet I would test the upgrade thoroughly. (I also would lock down the Update Manager so individual users don't see the "new release available" notification.) :)

The short answer to your question is: Yes. Ubuntu has a an update manager. It is designed to work, it should work, it will probably work... but the readers of this forum cannot *guarantee* it will work 100% bug free in 1 hour with zero effort on your part. :)

Have you considered burning a Live CD of 10.04 and thoroughly testing it on your hardware? That would be a good first step IMHO.

---

### Post by abickerton on 2010-04-30
On a Lenovo R60, the update via the update manager went flawlessly. 

It just plain worked ... =D>

If I don't find anything. I'll do the real update next week.

---

### Post by congdonb on 2010-04-30
Since it seems time spent doing upgrade is very important to you I would give you this from my experience.................

Yesterday, I used a 10.04 alternate install disk inside up my running version of 9.10 and did a distribution upgrade directly from the alternate disk.... I did it this way because all the mirrors are so busy right now (I tried just doing the distribution upgrade from the update manager 1st but connection kept stalling out). Basic upgrade was over in about an hour. However, after upgrade it needed to connect to mirrors for some remaining updates and also several packages installed (mostly older games) were not updated and it ran all night and most of this morning and then finally failed to fetch all required files.  I am sure if I waited a few days and tried again it would eventually be able to fetch the needed files.  Bottom line here is: completing upgrade time frame is based on a lot of factors some of which are: version and quantity of packages on system being upgraded, connection to mirrors, system memory, swap space etc. etc.

I did not want to wait and this is not my primary computer, so I backed up my data files, bookmarks etc. and did a from scratch install which was done is 20 minutes and another 20 minutes tweaking everything out again.

For me, the fresh install turned out to be way faster as I do not have a multitude of applications, 3rd party packages and custom settings.

If time taken to complete distribution upgrade has to be low for you, I would definitely wait until the mirrors settle down a bit in a few weeks.  Also, you can expect longer upgrade times and some upgrade issues if you have any 3rd party software packages installed and any custom configurations completed.

In the case where your production computer is so important I would also use Conezilla or such before going home the night before to ensure I have a bullet proof way to get the system to back to pre upgrade condition.

-Bill Congdon

---

### Post by abickerton on 2010-04-30
> **congdonb said:**
> Since it seems time spent doing upgrade is very important to you I would give you this from my experience.................

In the case where your production computer is so important I would also use Conezilla or such before going home the night before to ensure I have a bullet proof way to get the system to back to pre upgrade condition.

-Bill Congdon

Now that is something I will be doing before I start.

---

