---
title: "My System Is Still Borked"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Johnsie on 2009-09-18
I get dropped to the root shell ever time I start.. Even after applying the latest updates. Are they going to fix it or shoud I re-install? I've been waiting a few days hoping an update would fix it, but so far now luck.

---

### Post by Ratscallion on 2009-09-18
Care to elaborate? You're very vague.. So much so, I'm struggling to think of anything here...

---

### Post by AlanR8 on 2009-09-18
Happened to me on Tuesday of this week! 

I reinstalled from Alpha 5 last night and applied a partial update from Update Manager and things were OK. Tonight it allowed a full update and all is well.

Love the new loading screen art, far more subtle. Question, how can I change the hideous orange logon screen to match?

---

### Post by Johnsie on 2009-09-18
Sorry for being vague. The problem is all over these forums and is common knowledge among most testers. Basically one of the updates trashed alot of testers systems. 

I'm trying this:

> 
- check your sources.list to be sure you use the good one's, disable all the extra if exist (ppa's)

- run sudo aptitude clean
- sudo aptitude autoclean
- sudo aptitude install -f

don't run "sudo apt-get autoremove" now

- run system --> administration --> system janitor
- install gtkorphan & then: system --> administration --> remove orphans
- you can safely remove all the xorg-driver-chip-you-dont-have except the main one (intel, nvidia, ati & vesa)

Then, sudo aptitude update & sudo aptitude safe-upgrade


---

### Post by JCoster on 2009-09-18
> **AlanR8 said:**
> Love the new loading screen art, far more subtle. Question, how can I change the hideous orange logon screen to match?

We should get a new GDM theme as the development progresses which will hopefully match the new loading screen art.

---

### Post by Johnsie on 2009-09-18
Hmmm... that didn't work. Even when I do manually start dbus, hal and X the system seems to freeze randomly. I know this is a test version, so I hope the QA people at cannonical can eliminate these major bugs before the release date. 

I personally think the 6 month development cycle is too short and I don't think applications should be part of the operating system development. How much time to they spend playing around with packaging applications when they could be working on the OS itself? Let the app developers themselves control application versioning and spend more time working on drivers etc. 


Rant over.

---

### Post by Ratscallion on 2009-09-18
So.. You tried to install a few things and messed with the janitor. So... (probably
missig something here) what is the problem?? You're dropped to a root shell and have no GUI?

---

