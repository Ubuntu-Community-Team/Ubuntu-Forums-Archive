---
title: "I have kubuntu 19.04 but only have the option to upgrade to 19.10"
date: 2020-04-24
forum: Installation &amp; Upgrades
---

### Post by TechnoJunky on 2020-04-24
I have Kubuntu 19.04 installed on a couple computers.  20.04 was released yesterday and I found a couple sites telling me how to upgrade to 20.04, however, I only get 19.10 as an option on them.  Can I not jump a release?  Do I have to install 19.10 before I can go to 20.04?

---

### Post by CelticWarrior on 2020-04-24
> **TechnoJunky said:**
> I have Kubuntu 19.04 installed on a couple computers.  20.04 was released yesterday and I found a couple sites telling me how to upgrade to 20.04, however, I only get 19.10 as an option on them.  Can I not jump a release?  Do I have to install 19.10 before I can go to 20.04?

19.04 is now out of support. Please do your backups and install a fresh 20.04.
Upgrading from 19.04 could only be done to 19,10 indeed and that was while 19.04 was still under support, i.e. until January.

---

### Post by TechnoJunky on 2020-04-24
Not that answer I wanted to hear, but understood.  Thanks.

---

### Post by TechnoJunky on 2020-04-24
I just upgraded one of the desktops to 19.10.  Went very smoothly, and quicker than I expected.  However, I still don't have the option to upgrade to 20.04.  'do-release-upgrade -c' says 'No new release found'.

---

### Post by Impavidus on 2020-04-24
It's normal that it takes a few days before the upgrade is available.

Are you sure you want a double upgrade, not a fresh install?

---

### Post by SeijiSensei on 2020-04-24
Try using "do-release-upgrade -d". 20.04 might still be treated as a "development" release.

---

### Post by TechnoJunky on 2020-04-24
with a couple of the computers, a fresh install would be ok, but with one I want the upgrade.  Although it's a desktop install, it acts as my server, print, file with software raid, etc.  I don't want to go to the trouble of setting all that up again.  With that computer, I'll stick with the LTS version, once I get it on there.

Don't necessarily want the development release.  Guess I'll wait a few days till the standard upgrade is available.  


Thanks for the replies.

---

### Post by mmontanaro on 2020-04-24
Is 20.04 still considered a "development" release?  When does it come out of development and become an LTS?  Confused.

---

### Post by CelticWarrior on 2020-04-24
> **mmontanaro said:**
> Is 20.04 still considered a "development" release?  When does it come out of development and become an LTS?  Confused.

Released today. You should read the news more often.

---

### Post by mmontanaro on 2020-04-24
> **CelticWarrior said:**
> Released today. You should read the news more often.


My confusion comes from the fact that when I attempt to install it, 18.04.4 tells me I am installing a development release and wants to know if it should continue.  I did not think this was still a development release, so I am assuming something is wrong.  However, I did not have the time to troubleshoot it or post a question in the forum other than the one you so snarkily replied to.  A simple yes or no would have been sufficient to answer the question.

---

### Post by Impavidus on 2020-04-25
20.04 has been released. You can download the live .iso and install it. However, the tools to upgrade from an earlier version of Ubuntu to 20.04 haven't been released yet. For the upgrade from 19.10 to 20.04, that can happen at any moment. For the upgrade from 18.04 to 20.04, that's expected to happen in July.

Note (for other people reading this thread) that there won't be an upgrade from Lubuntu 18.04 to 20.04 (changes are too extensive to make this reliable) and there won't be an upgrade for 32 bit systems (support for 32 bit is terminated after 18.04).

---

