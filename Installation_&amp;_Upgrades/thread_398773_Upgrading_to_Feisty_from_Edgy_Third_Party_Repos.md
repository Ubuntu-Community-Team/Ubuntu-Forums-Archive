---
title: "Upgrading to Feisty from Edgy: Third Party Repos?"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by darkmaster on 2007-04-01
Hi all, I've got a mystic problem in my mind while I'm waiting for Feusty Fawn to be released (When will the exact date be after all?). I've got a lot of extra third party repos for Edgy taken from Trevino's Blog:

[http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/](http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/)

Since I found myself really very confortable with these repos and my edgy system gave the best of itself with these very often updated repos, I'm wondering, what will happen to my repos list after upgrading to feisty?

Will the repos be a problem? Will they be deleted and substituded with feisty's repos? I just need some clarifications by someone who knows what he's saying, thanks :) 

The other question is: I use Network Manager. I've read that Feaisty will use another network manager, so, I was guessing, will this be a compatibility problem beetween my edgy and Feisty? Will all the new features of feisty be installed on my PC or will I get a sort of mutant edgy system?

Thans for paying attention to all my doubts :) bye bye!

---

### Post by pradeepadapa on 2007-04-01
hello can u paste ur sources.list file here so that we can also benefit from the repository changes which u hav made to the standard edgy repos list........ and as far as i know in fiesty fawn also u can add ur own repositories but i dont know whether ur sources.list will be same or change after an upgrade to it from edgy.. :)

---

### Post by zvacet on 2007-04-01
Like right now when you have Edgy source list that wiil be the case with Feisty.You have to relace al Edgy to Feisty,otherwise you will have messed source list.Your trevino will give you updates for Feisty like it gives you for Edgy now.You dont´t have to be af
```
 sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
```
This will change your Edgy to Feisty source list.

---

### Post by darkmaster on 2007-04-01
> **zvacet said:**
> Like right now when you have Edgy source list that wiil be the case with Feisty.You have to relace al Edgy to Feisty,otherwise you will have messed source list.Your trevino will give you updates for Feisty like it gives you for Edgy now.You dont´t have to be af
```
 sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
```
This will change your Edgy to Feisty source list.

yes, I thing the only way is to wait for Trevino to give us new Feistry repositoryes. If I just rename every repo's name, I think I will mess up things. Not all repos may exist for feisty too, don't you think? 

@pradepadapa
just follow the link I posted in my first question, the repos are all there!!!!

Thanks for the help. Any other suggestion?

---

### Post by bapoumba on 2007-04-01
Hello,
what did you install from treviño's repos ?
I would recommend to comment out _all_ thrid party repos before upgrading to a new release.

---

### Post by johnc4510 on 2007-04-01
I agree with bapoumba, I always comment out all 3rd party repos before upgrading. In this way you avert a lot of problems during upgrade.

---

