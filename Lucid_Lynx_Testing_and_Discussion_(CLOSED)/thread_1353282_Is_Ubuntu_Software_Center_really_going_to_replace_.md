---
title: "Is Ubuntu Software Center really going to replace Synaptic in Lucid?"
date: 2009-12-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by A_T on 2009-12-12
No Synaptic at all? If so I find that incredible. USC tells you almost nothing. It would be OK to have alongside Synaptic but it's very far from a satisfactory replacement.

---

### Post by Techsnap on 2009-12-12
I doubt it, when I tried it, it didn't even show all the installed applications.

---

### Post by Hetor on 2009-12-12
I hope they will at least keep it in repos.

---

### Post by SunnyRabbiera on 2009-12-12
Indeed, unless software center undergoes a major overhaul and if it totally phases out synaptic in lucid Ubuntu is out of the game as far as i am concerned.

---

### Post by Uncle Spellbinder on 2009-12-12
> **sunnyrabbiera said:**
> indeed, unless software center undergoes a major overhaul and if it totally phases out synaptic in lucid ubuntu is out of the game as far as i am concerned.

+1

---

### Post by sisco311 on 2009-12-12
> **A_T said:**
> No Synaptic at all? If so I find that incredible. USC tells you almost nothing. It would be OK to have alongside Synaptic but it's very far from a satisfactory replacement.

nope, although they plan to make it viable alternative to Synaptic.

[https://wiki.ubuntu.com/SoftwareCenter]("https://wiki.ubuntu.com/SoftwareCenter")

---

### Post by wilee-nilee on 2009-12-12
USC will only load single packages at a time as of now, you can Q other packages but it runs very slow. Synaptic will multi load at times. The terminal will always be there if synaptic is removed for those that know what to load.

---

### Post by SunnyRabbiera on 2009-12-12
> **sisco311 said:**
> nope, although they plan to make the it viable alternative to Synaptic.

[https://wiki.ubuntu.com/SoftwareCenter]("https://wiki.ubuntu.com/SoftwareCenter")

They better, right now the current software center is fine for beginners but for us who like the more advanced features of syanaptic without dealing with command line its not up to speed.

---

### Post by joey-elijah on 2009-12-12
Do people really not realise that the USC is a work in progress?! It's at stage 1 of 4 in Karmic. 

The best, as they say, is yet to come.

---

### Post by forrestcupp on 2009-12-12
Even after USC takes the place of Synaptic, all you'll have to do is```
sudo apt-get install synaptic
```and viola!

Synaptic is just a GUI frontend for apt.  You'll always be able to have Synaptic if that's what you want.  I seriously doubt if Ubuntu is ever going to do away with apt.

---

### Post by murderslastcrow on 2009-12-12
Yeah, I wouldn't be surprised if they didn't just have an option on the left for package management, then have the right pane be a reproduction of the way Synaptic looks now, just with the search bar integrated where it is currently in Get Free Software.

I don't think it's far-fetched to think they'll implement this, and I think it would be very nice to have if they allow multiple checkboxes like they should have originally.

---

### Post by meho_r on 2009-12-12
> **forrestcupp said:**
> Even after USC takes the place of Synaptic, all you'll have to do is```
sudo apt-get install synaptic
```and viola!

No, no, no!, not that way. You **should** go to **Applications > Ubuntu Software Center**, then search for "Synaptic", then select it, then press that orange arrow on the right which is shouting "Press me and something wonderful will happen!", and then click on the button "Install", on the bottom. Why using tedious and complicated way you just described when you can use this piece-of-cake and soooo simple and effective way that saves your time. And money. And brain cells. And time. And... ehm... I'm a fan. Yes, really, I am.

---

### Post by zekopeko on 2009-12-12
You people that are up in arms can read the wiki at [https://wiki.ubuntu.com/SoftwareCenter](https://wiki.ubuntu.com/SoftwareCenter)

USC is going to improve a great deal by the time Lucid is out.

And if USC ins't ready to replace Synaptic, then Synaptic is going to stay.

---

### Post by Exodist on 2009-12-12
> **A_T said:**
> No Synaptic at all? If so I find that incredible. USC tells you almost nothing. It would be OK to have alongside Synaptic but it's very far from a satisfactory replacement.
USC is in heavy development. The plan is to replace Synaptic, but from what we discussed before in regards to this. There is to be 3 steps of development, Karmic being the first and introduction of software center. Lucid will be the 2nd step and 10.10 being the final implementation. Apt-get will still be included and provide a solid backbone.

As far as removing Synaptic on Lucid, to my knowledge it still will be included. But do expect to see more focus on USC.

---

### Post by meho_r on 2009-12-12
> **zekopeko said:**
> You people that are up in arms can read the wiki at [https://wiki.ubuntu.com/SoftwareCenter](https://wiki.ubuntu.com/SoftwareCenter)

USC is going to improve a great deal by the time Lucid is out.

And if USC ins't ready to replace Synaptic, then Synaptic is going to stay.

Just kidding, zekopeko, don't get upset :D

---

### Post by AICollector on 2009-12-12
I find USC a more friendly enviroment then Synaptic; but when I need to know about what I'm installing...I use Synaptic.

---

### Post by AllRadioisDead on 2009-12-12
> **meho_r said:**
> No, no, no!, not that way. You **should** go to **Applications > Ubuntu Software Center**, then search for "Synaptic", then select it, then press that orange arrow on the right which is shouting "Press me and something wonderful will happen!", and then click on the button "Install", on the bottom. Why using tedious and complicated way you just described when you can use this piece-of-cake and soooo simple and effective way that saves your time. And money. And brain cells. And time. And... ehm... I'm a fan. Yes, really, I am.
 Tedious and complicated? 
It's 5 words, and your proposed alternative was a paragraph..
hmmm.

---

### Post by airtonix on 2009-12-12
Hi can i sell you a new sarcasm detector?

---

### Post by Mr. Picklesworth on 2009-12-12
> **joey-elijah said:**
> Do people really not realise that the USC is a work in progress?! It's at stage 1 of 4 in Karmic. 

The best, as they say, is yet to come.

And on that topic, the version in trunk now lists all available packages. Currently these are thrown into a System Packages category, but that categorization will be played with a lot as time goes on.

(And the application is written in Python, so there is really no reason not to test the latest version Right Now if you're running Karmic; just branch it, run the main program from the source directory and it works!)

---

### Post by cmat on 2009-12-12
Synaptic is a very important tool to hunt down the load of packages needed to manually compile stuff.

---

### Post by mybunche on 2009-12-12
I have high hopes for the USC. I would like to see any software that needs to be installed, removed, updated, downgraded be done by the USC with absolute reliability. I like it to include, free and commercial applications, individual packages and any drivers.

---

### Post by Rainstride on 2009-12-12
> **A_T said:**
> No Synaptic at all? If so I find that incredible. USC tells you almost nothing. It would be OK to have alongside Synaptic but it's very far from a satisfactory replacement.

yes, it is still in development though. the current software center is nothing like the planned end product. there will be a lot of changes. here is the wiki [https://wiki.ubuntu.com/SoftwareCenter#Animation%20of%20the%20main%20pane](https://wiki.ubuntu.com/SoftwareCenter#Animation%20of%20the%20main%20pane)

---

### Post by abeisgreat on 2009-12-12
Synaptic and USC are very different software with different audiences. They could easily co-exist. I see no reason to get rid of either one.

---

### Post by SilverDragon on 2009-12-12
> **airtonix said:**
> Hi can i sell you a new sarcasm detector?

Best response to someone not understanding a sarcastic comment.

But on topic, the Ubuntu Software Center could be completely different in functionality by the time it is implemented fully in 10.10, so much so that maybe it will be good enough to replace Synaptic. I doubt it though.


> **abeisgreat said:**
> Synaptic and USC are very different software with different audiences. They could easily co-exist. I see no reason to get rid of either one.

I agree with this.

---

### Post by hoppipolla on 2009-12-12
> **SunnyRabbiera said:**
> Indeed, unless software center undergoes a major overhaul and if it totally phases out synaptic in lucid Ubuntu is out of the game as far as i am concerned.

I'm sorry what? xD

You don't really think they would omit something as crucial as Synaptic from the repos do you?

And Ubuntu out of the game... Ubuntu is the biggest Linux distribution in the world and is showing no signs of weakening at least not for years. How on earth would dropping Synaptic from the default install condemn a whole OS?

---

### Post by forrestcupp on 2009-12-14
> **cmat said:**
> Synaptic is a very important tool to hunt down the load of packages needed to manually compile stuff.

Lol.

---

### Post by Uncle Spellbinder on 2009-12-14
> **abeisgreat said:**
> Synaptic and USC are very different software with different audiences. They could easily co-exist. I see no reason to get rid of either one.
> **SilverDragon said:**
> I agree with this.

As do I. I have high hopes for Software Center. After all, it is in it's infancy at the moment and can only improve. I look forward to seeing the improvements in Lucid, and further down the road in Mighty Mandrill. As long as I have the option for Synaptic, I'm happy.

---

### Post by alexfish on 2009-12-14
> **A_T said:**
> No Synaptic at all? If so I find that incredible. USC tells you almost nothing. It would be OK to have alongside Synaptic but it's very far from a satisfactory replacement.

The Idea Seem Good  . But The Way Linux Works I  ???

From a Desktop  Point of view . Each bit of Software  will have to know the mapping of the system, RE: Plugins /ect .That would be the                            Developers responsibility unless it platform                            independent.  I think we all Know what happens then.



ppa:network-manager  Possible slight hint there somewhere

So Unless Things are Developing at pace  we don't know about ? who really Knows!

Time Will tell  But Linux is Linux , and we have got used to  Synaptic doing the hard work

'''Some days I don't feel like Trawling through  a list as long as the "GRAND CANYON"

There are lots of times I just go direct to the Debian Site and  Hi Presto :P

It Won't Beat Me

PS : HOW LONG IS THE GRAND CANYON

---

