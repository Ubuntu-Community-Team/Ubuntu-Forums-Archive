---
title: "How to upgrade ubuntu server from 6.10 to 9.10"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by ShawnSmiley on 2009-11-23
I have an Ubunut Server 6.10 install that has been running flawlessly for 3 years.  

However I recently noticed that the apt-get routines are no longer pulling updates (apt-get upgrade returns 404 errors on all repositories).  

So I'm figuring now would be a good time to upgrade to to either 9.04 or the 8.04 LTS releases.


What would be the best approach to use in doing this upgrade?

Can it be done remotely via ssh?

I ask because I'm no longer at the same physical location as the server (its on the US east coast and I'm on the west coast) and we don't have any Linux knowledgeable staff still on site.

This server is currently hosting our SVN Repository, though we want to start using it for hosting Trac as well.


Thanks in advance!

---

### Post by snowpine on 2009-11-23
6.10 reached its "end of life" a long time ago (April 2008 ). Here is my recommendation:

1) Back up all important documents and settings
2) Do a "fresh install" of a current Ubuntu version (8.04 or 9.10 would be my recommendation)

Some conservative users choose a "dual boot" where they install the new version alongside the old version, to use as a fallback.

Good luck!

---

### Post by phillw on 2009-11-23
As your system is working okay, IMHO, I'd hang on for the next LTS due 04-10.  The guys over on the server section would be better placed to answer your question [http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

They'd also be be better placed to advise you on how to do the upgrade paths.

I'm looking forward to 10-04 ... Came in at 9.04 as release cycle was already well the way through. goes to prove, however, that your system is nice and stable :-)

Regards,

Phill.

---

### Post by snowpine on 2009-11-23
Phill makes a good point. If you can hold out until 10.04, you'll have the next "long term support" which is supported 5 years on the server side, I believe.

ps I forgot to mention, the 6.10 repositories aren't gone... they've just been moved to old-releases.ubuntu.com ... you could update your /etc/apt/sources.list if you choose to stick with 6.10, but want repository access. (You've made it since April 2008 with no security updates or bug fixes... why start now, right? ;))

---

### Post by ShawnSmiley on 2009-11-23
Thanks for the feedback snowpine and phillw.

I think we're just going to do a fresh install of 8.04 LTS and then upgrade to 10.04 LTS next summer.

It's also a good excuse to archive and remove some of our old SVN Repositories. :-)

---

### Post by ShawnSmiley on 2009-11-23
Thanks Snowpine, I didn't realize the old repositories were still available.

---

### Post by snowpine on 2009-11-23
> **ShawnSmiley said:**
> Thanks Snowpine, I didn't realize the old repositories were still available.

They are available, but not being updated (no security patches etc.)

[There is a very messy way to upgrade using the old repos,]("https://help.ubuntu.com/community/EOLUpgrades") but I recommended the fresh install for obvious reasons (you won't have to go 6.10-7.04-7.10-8.04-8.10-9.04-9.10).

---

### Post by slakkie on 2009-11-27
> **snowpine said:**
> They are available, but not being updated (no security patches etc.)

[There is a very messy way to upgrade using the old repos,]("https://help.ubuntu.com/community/EOLUpgrades") but I recommended the fresh install for obvious reasons (you won't have to go 6.10-7.04-7.10-8.04-8.10-9.04-9.10).

Very messy? I've done so many upgrades (incl EOL) that I would hardly call it messy. The methods are proven to work.

---

