---
title: "fresh install vs. upgrade"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by gilang on 2008-05-27
this is the story:
i got few problem with my gutsy, like touchpad that didn't work, even when i try so many settings from out there to my Xorg.conf. 

and when i did upgrade to hardy online, this problem still not fixed. until suddenly i got mess with my ubuntu and i should reinstall it.
i did fresh install hardy to my machine, and like magic, my touchpad is working until now.
now everything just look fine with hardy, no problem at all!

and this is the question:
do i have to always do fresh install when a new version coming out?

could you explain how to backup your installed program and their setting if you want to keep these all on your new fresh install? 

thnks

---

### Post by Mhurst1 on 2008-05-27
Personally I would always do a clean install and to keep your files and settings always make a seperate partition for /home.

---

### Post by IgnorantGuru on 2008-05-27
I always do a fresh install now - I never had good results with upgrades.

The user-level prefs and settings are stored in /home.  If you make a backup of the /home folder then copy it back into your new system, that will restore many desktop and software settings.  You can find instructions on backup and restore of the /home folder here...
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

As for installing software, with apt-get install it's pretty easy to make a list of the software you want to install and do it in one shot on the command line.

Also, while doing a fresh install I make notes of each thing I do.  When the next fresh install comes around, I can go through the list and repeat the configuration steps, updating the list for the new OS.  This makes it pretty fast.

---

### Post by gilang on 2008-05-27
i see...
i use the same partition for /home now. can i make new partition and just move the /home directory to the new one?

---

### Post by gilang on 2008-05-27
i see...
i use the same partition for /home now. can i make new partition and just move the /home directory to the new one?

---

### Post by gilang on 2008-05-27
for ignorantguru, 
in xp i can backup the program files folder (where i usually install program) and just paste it to a new computer, and the program worked well (i think). can we just do it like that on ubuntu? so we dont need to reinstall the program...

---

### Post by IgnorantGuru on 2008-05-27
gilang, that will only work in limited cases with winxp.  As for ubuntu, that would not be a good approach.  Instead, make a list of program packages you add to the system after the base install.  Then you can reinstall them with one command...
```
sudo apt-get install package1 package2 package3
```

It's MUCH easier than installing software in windows.

And when you restore your /home folder, all the user-specific settings for these software packages will be restored.

As for the /home folder on its own partition, I don't personally like that method, although many people do.  I prefer to keep /home on the system partition because I like to install a new system on a spare partition and get it all set up before I decide to keep it.  Doesn't really matter how you go about it.  As long as the new system uses the old /home folder (or a copy of it), it will save you a lot of work.

---

### Post by gilang on 2008-05-27
ok thanks....help a lot

---

### Post by gilang on 2008-05-27
one more thing...do you recomend fresh install of ubuntu every six month they release new version? well, if yes, that will give a lot of work to do, backup the /home, fresh install and use apt get every six month...

based on your experience, can i get new problem if i just do upgrade the version? because everything just worked well now with hardy...

---

### Post by gauss on 2008-05-27
> **IgnorantGuru said:**
> Then you can reinstall them with one command...
```
sudo apt-get install package1 package2 package3
```

I'd like to make a fresh install of Heron along these lines and restore all my current Gibbon packages. How can I get a list of all the packages I currently have installed under Gibbon? Are they all in /var/cache/apt/archives?

Thanks.

---

### Post by vishzilla on 2008-05-27
I performed an upgrade for Hardy. It didn't work so well. I will stick with Fresh Install

---

### Post by buntunub on 2008-05-27
> **gilang said:**
> this is the story:
i got few problem with my gutsy, like touchpad that didn't work, even when i try so many settings from out there to my Xorg.conf. 

and when i did upgrade to hardy online, this problem still not fixed. until suddenly i got mess with my ubuntu and i should reinstall it.
i did fresh install hardy to my machine, and like magic, my touchpad is working until now.
now everything just look fine with hardy, no problem at all!

and this is the question:
do i have to always do fresh install when a new version coming out?

could you explain how to backup your installed program and their setting if you want to keep these all on your new fresh install? 

thnks

When doing an upgrade, you will get asked alot of questions, like do you want to keep this config file or that one. This is where people get into big trouble on upgrades IMO. For me, I understood what those questions meant, and which config files were essential to my setups (because I wrote them that way), so my upgrade went 100% smooth and flawless and the system remains rock solid stable to this very day. Like with anything you do on Linux, first research and understand HOW to do the upgrade before doing it, and you too will have no issues.

---

### Post by IgnorantGuru on 2008-05-27
> **gauss said:**
> I'd like to make a fresh install of Heron along these lines and restore all my current Gibbon packages. How can I get a list of all the packages I currently have installed under Gibbon? Are they all in /var/cache/apt/archives?


A list of ALL the packages currently installed would be massive, because it includes the base install as well as support packages required by software.  /var/cache/apt/archives would probably contain packages you've downloaded (unless you cleaned it out), but even a lot of that would be redundant dependencies.

The easiest thing to do is just go through your system and make a list of software you added.  Then go into Adept or your preferred package manager and look up their package name.  For example, mplayer is just called "mplayer".

Once you get into your fresh install you will tend to notice what's missing and install it.  As you do that, make a list for future use.

If you have the means, installing the new system on a spare partition is helpful because you will still have the old system to consult as you're setting it up.

---

### Post by IgnorantGuru on 2008-05-27
> **buntunub said:**
> Like with anything you do on Linux, first research and understand HOW to do the upgrade before doing it, and you too will have no issues.

It is good advice, but I would say you're a little overly optimistic.  I understood all the questions with the Edgy upgrade and it just froze and killed my system.  (Fortunately I backed up the partition first so it was no big deal.)

Even for the most competent devs, writing a good upgrade is very complex.  With that rate that Ubuntu delivers new versions, I don't think they can put ample time into testing, which is the primary reason people have such difficulties.

And even if the upgrade appears to work, often there are problems waiting to arise because of latent misconfigurations.  I have found it's just not worth the time to deal with upgrades.  Much easier for me to keep a list of my basic install steps and just fly through them in a few hours.

---

### Post by IgnorantGuru on 2008-05-27
> one more thing...do you recomend fresh install of ubuntu every six month they release new version? well, if yes, that will give a lot of work to do, backup the /home, fresh install and use apt get every six month...

The 'if it ain't broke don't fix it rule' applies here.  If your system is running well and your software is doing what you want, there is no need to grab every six-month release in my experience.  If you see the new release has software or features you want, then it might be worth your time.  Remember that releases are supported for security updates for 18 months.

Personally, I tend to follow more of a one-year schedule, skipping every other release.  (This is bad if you are going to upgrade, though - don't skip versions.)  I also keep an eye on the forums when a new release comes out for whether it is a winner or a 'rotten egg', especially as it relates to my uses and hardware.  For example, the Gutsy release broke a lot of HP laptops, so I avoided it altogether.  Didn't even try it.

I don't find a fresh install all that time-consuming, and I think the system runs better if it's completely refreshed every year or so (despite the best intentions of people to create a timeless OS).  It's just a matter of getting organized a bit and knowing where settings are stored.  My 'upgrade' procedure is basically this one...
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems#Scenario_.235:_Alternating_Versions_Of_Linux](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems#Scenario_.235:_Alternating_Versions_Of_Linux)

---

### Post by gilang on 2008-05-29
> **IgnorantGuru said:**
> The 'if it ain't broke don't fix it rule' applies here.  If your system is running well and your software is doing what you want, there is no need to grab every six-month release in my experience.  If you see the new release has software or features you want, then it might be worth your time.  Remember that releases are supported for security updates for 18 months.

Personally, I tend to follow more of a one-year schedule, skipping every other release.  (This is bad if you are going to upgrade, though - don't skip versions.)  I also keep an eye on the forums when a new release comes out for whether it is a winner or a 'rotten egg', especially as it relates to my uses and hardware.  For example, the Gutsy release broke a lot of HP laptops, so I avoided it altogether.  Didn't even try it.

I don't find a fresh install all that time-consuming, and I think the system runs better if it's completely refreshed every year or so (despite the best intentions of people to create a timeless OS).  It's just a matter of getting organized a bit and knowing where settings are stored.  My 'upgrade' procedure is basically this one...
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems#Scenario_.235:_Alternating_Versions_Of_Linux](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems#Scenario_.235:_Alternating_Versions_Of_Linux)

thanks for your help:)

---

### Post by circusmonkey on 2008-05-29
Well I have just tried upgading to Hardy and it has failed , the desktop enviroment has defaulted and I cannot change it , plus all the netowrk connections have now failed .....

not impressed with the extra leg work now required :)

R

---

### Post by gauss on 2008-05-30
> **IgnorantGuru said:**
> A list of ALL the packages currently installed would be massive, because it includes the base install as well as support packages required by software.  /var/cache/apt/archives would probably contain packages you've downloaded (unless you cleaned it out), but even a lot of that would be redundant dependencies.


Perhaps I should have made the list of old packages with ```
$ dpkg-query -l
```I gather that that would list only the packages currently installed.

If I run *apt-get install* on, say, the list of packages in */var/cache/apt/archives* and it came upon a base package already installed, wouldn't it simply skip it? Also, if it installed a dependency before it installed the package which required the dependency, would that be a problem? I'm not sure what problems would result from re-installing all the old Ubuntu version packages.

There should be an easy, programmatic way to do a fresh install and restore all packages from the previous Ubuntu version.

Thanks for helping me find it.

---

### Post by ForksHolder on 2008-05-30
Well, A clean install from CD will ALWAYS be better.

I recommend to backup the things you need and just install and put them there.

Good Luck :]

---

### Post by PaulGrahamRaven on 2008-05-31
Hi guys; just trying to get some confirmations on my suspicions here.

I'm currently running Gutsy split across three partitions - /root, /home and swap.

All the evidence I've seen on the forums here suggests that a clean install of a new version is a much better plan than the upgrade, and I can see how that would be the case. What I'm unclear on is the following:

[LIST]
[*]If I use my current /home in the new system, just remounting it during the install, all the files stored there will stay aboard, yes?

[*]If that's the case, I assume I'd have to set up the same localhost name, user name and password during the new install, or the permissions/ownerships of the files in /home would mean the new install couldn't use those files?
[/LIST]

I realise these are probably obvious n00b questions, but I really have had a good search on fresh install procedures here, and I can't find an answer - I think possibly because it's considered too obvious to be worth mentioning. I'd really appreciate a brief explanation if someone can spare a moment.

---

### Post by PaulGrahamRaven on 2008-06-02
Consider this a mild *bump* - or should I have started a new thread?

---

### Post by PaulGrahamRaven on 2008-06-27
Could someone give me a hint on this fresh install query?

---

