---
title: "How should we attain trust in a PPA?"
date: 2020-06-12
forum: Installation &amp; Upgrades
---

### Post by bobjunga2 on 2020-06-12
I am a long time server admin and do not understand how we are supposed to get to a level of trust of a 3rd party PPA.  I understand that if a PPA is owned by the upstream project then you can trust it as much as you have already decided to trust that project. Also, sometimes in a community there is a lot of discussion about a particular PPA which has gained the trust of that community over time and it becomes well known it how to guides which is a form of reputation endorsment. I have choosen many PPA this way.

However, in general, I am surprised at the lack of help that launchpad gives us. Github and other platforms have reputation based systems that let you know if the project that you are considering is well regarded, poorly regarded, or not used enough to have a reputation. I just looked for nginx PPAs, looking for ones that include the modules I want.  I get 735 matches with no context about the maturity or popularity of each result. I can not filter on significant attributes. If I click on one I can see when the last update was which seems to eliminate many unmaintained ones but that is like looking for a few needles in a haystack. Filtering or sorting by last update would be a big help.

The Launchpad PPAs system has been around forever. How has it not gotten any of these features by now.  Could it be that it has some and I just can not find them?

I suspect that most people do not give it a second thought. They take a PPA's presence on launchpad as endorsement that it is not malicious (which it is not).  I think as a community, we get away with being lax on this point just because it is not common to have malware targeting linux machines for some reason.

So how do you decide whether or not you should trust a PPA? Do you stick you head in the sand and hope for the best, or do you have a good system that I might be able to learn from?
 
--BobG

---

### Post by CatKiller on 2020-06-12
There is no definitive way to trust PPAs. Even if, at the time you add them, they have exactly the packages you want, the maintainer of the PPA *could* put different packages up later that do some other thing. And you might not notice.

> **bobjunga2 said:**
> The Launchpad PPAs system has been around forever. How has it not gotten any of these features by now.  Could it be that it has some and I just can not find them?

The discoverable, curated, progression from the PPA system is the Snap Store.

---

### Post by bobjunga2 on 2020-06-12
Yes, it does seem that Ubuntu is putting all of its eggs in the spap basket.

> [COLOR=#000000]There is no definitive way to trust PPAs. Even if, at the time you add them, t[/COLOR]
Of course this it is true for Linux, Ubuntu, and any other software we choose to leverage. Trust is a social construct that is earned.  Snap isolation is not a panacea.  I dont want an application running on my servers that does not have my interest in mind over theirs. 

--BobG

---

### Post by guiverc on 2020-06-12
> **bobjunga2 said:**
> 
So how do you decide whether or not you should trust a PPA? Do you stick you head in the sand and hope for the best, or do you have a good system that I might be able to learn from?


I'll put in my 2c, though it's unlikely much help (I'm not an administrator of servers, but desktop user so packages I look for are possibly a little different).


I look at who created it, their launchpad account, member since, member/affiliated groups, maybe karma etc. As the PPAs I'm interested in are desktop related, I can often recognize names (quick check in my liferea for feeds from the project etc), though it doesn't take long to check they are a member of a project, and get a glimpse of any involvement (how much, when..) online (project web sites/planet blogs/ML etc).  This works even if they're not involved with Ubuntu projects (involved elsewhere, just package it for Ubuntu now and again). If I find nothing, I'm not going to add it...


> **bobjunga2 said:**
> 
I suspect that most people do not give it a second thought. They take a PPA's presence on launchpad as endorsement that it is not malicious (which it is not). I think as a community, we get away with being lax on this point just because it is not common to have malware targeting linux machines for some reason.


Me I don't trust PPAs, and very much try & add a comment on askubuntu.com when I do see users (which I assume are new) adding PPAs that are years past their last maintenance etc.. From what I've seen I'd agree with you that newer users tend to trust, but I can't speak to more experienced (it's usually no/low point users on askubu)

---

### Post by ActionParsnip on 2020-06-13
In short, you can't. The first 'P' stands for personal. The maintainer is making the packages for themselves. The fact that they are publicly available is just a bonus but ultimately you have no idea what is in the package until you pull it down and have a look.

---

### Post by bobjunga2 on 2020-06-13
So I would amend my question to be how do we decide to use a PPA because trust is only part of it. Its also about whether a PPA is being maintained and how well.
 
I think that the information about the author's involvement in communities that @guiverc talked about is important to know. Also, you would want to know some things about the PPA like when it was last updated and the average period between updates.

As @ActionParsnip pointed out, Launchpad can't tell us whether we should trust a PPA but it could make some information available so that we can make an informed decision.

Some information is easy for it to collect, for example, our launchpad user accounts already have participation levels and it could track how many times per day the PPA's release file is requested as a rough indication of how much it is used and it already knows the age of the last update.

The problem is that it does not make any of that information available,  even the information it already has, when we are searching for PPAs.

--BobG

---

