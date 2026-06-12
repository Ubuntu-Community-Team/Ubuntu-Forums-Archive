---
title: "System Update"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by marf88 on 2007-10-18
Ok, I installed Tribe 5 about a month ago. Been using it ever since. Running updates whenever they popped up. Today with the release of Gutsy I figured there would be some more updates but nothing had popped up in the upper right corner. I do a quick google search and I see a site saying go to System > Administration > Update manager.  I do and it checks and brings up this following error (click thumbnail).  Any help is appreciated.

Thanks

---

### Post by whoopn on 2007-10-18
I think the servers are at capacity.  If you wait for a little while or hit it late at night you might have different results.

---

### Post by marf88 on 2007-10-18
now I get this. I hope its because server is busy and my PC isn't messed.

---

### Post by marf88 on 2007-10-18
does my problem have to do with the fact I'm using the tribe 5 installed version? Shouldn't it automatically upgrade to the final release?

I also looked in my sources.list and my main ones are

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted


where as people with the final release use 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted


should I manually change mine??

---

### Post by soccermonstar13 on 2007-10-18
I installed tribe 5 too and am having similar problems with updating. I have commented out the first line in sources.list so that it no longer includes the Beta CD as a source. I have both gutsy and gutsy-updates though and both are us.archive.ubuntu.com

I wonder what needs to be changed... or maybe the servers are just slow like someone suggested...

---

### Post by marf88 on 2007-10-19
anybody?

---

### Post by Anicka on 2007-10-19
There are several different levels of repos. I have (for feisty) feisty, feisty-updates, feisty-backports, feisty-proposed and feisty-security. Feisty contains pretty much the basic system; updates and security is updates and security-fixes for this. Backports and proposed are more for testing. For gutsy it should be the same.

Each of these repos have categories main, restricted, universe and multiverse. For the basic user, the main-part might be enough.

To change the repos, without manually editing the source-list, go to System -> Administration -> Software sources and tick the different boxes.

If you had the gutsy-beta and you have done your updates, you are now the proud owner of the final release version.

---

