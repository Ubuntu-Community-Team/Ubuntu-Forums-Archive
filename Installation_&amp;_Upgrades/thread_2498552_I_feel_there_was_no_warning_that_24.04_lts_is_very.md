---
title: "I feel there was no warning that 24.04 lts is very buggy"
date: 2024-06-19
forum: Installation &amp; Upgrades
---

### Post by pgershon on 2024-06-19
I trusted Canonical and upgraded from 22.04 lts to 24.04 lts on an optiplex 5090 that came with 20.04 installed. I trusted Canonical because prior upgrades have been issue-free.

This time, it was a major mistake, I did not realize 24.04 was buggy. Could I please have advice on how to back-grade if possible? THanks. I first upgraded from 22.04 to 23.10 then from there to 24.04. I can give more details if required, but it was all done with standard commands, I think, and I did not see any obvious errors.

There is no advice online that I can find: It is not since the 1990s that I had an OS that failed to connect to internet ("Connection failed: Activation of network connection failed"). This is a very standard wired connection, there is nothing I can find online for 24.04 failing to connect a wired connection, or for any Ubuntu failing to do this on hardware that previously worked fine. No, its not my settings (the network guy here also cannot fix it. No, it is not ipv6. No it is not the clock.

Its weird because it connected to the internet presumably to download the upgrades with no issue, in both the above upgrade steps, so I am assuming 24.04 broke my internet connection in a final installation step after all downloading was complete.

Also:

Clicking on the libre office writer icon does nothing, libreoffice calc icon does nothing, and so it goes on. This upgrade seems so broken that I cannot see any obvious solution other than, perhaps grudgingly admitting that Windows has cornered the market for a reason because I am several hours into this now, and to be honest if I had known that basic stuff that has been working for many years would be broken again, I would have definitely just left the whole thing alone for the forseeable future.

Any expert advice much appreciated.

Thanks, Paul

---

### Post by phatton1 on 2024-06-19
Sorry I can't be much help with this Paul, but there were several warnings not to upgrade to 24.04 yet. 
I have performed a clean install on my two computers and everything works well.
It may be worth backing up any data and clean installing.
The full install is fast, so you can be back up and running in less time than you've already spent and at the end of it you should have a good stable system again

---

### Post by Rubi1200 on 2024-06-19
There is always going to be a certain amount of risk upgrading the way you did. It could be software or hardware conflicts, it could be PPAs you added. We don't know because we don't know your system the way you do.

Two points to consider:

1. use a separate /home partition so that when you upgrade you only upgrade the root partition (backups still essential)
2. avoid updating via interim releases as you did

Best to usually backup data and do a fresh install or wait for the first point release for things to stabilize. In this case, that would be in August 2024.

To perhaps try and resolve some of this I would try booting recovery mode and use an older kernel to see whether the issues persist. Perhaps also consider reinstalling LibreOffice.

---

### Post by guiverc on 2024-06-19
I'll give some thoughts only.

- you give release details; but don't actually say which product (Server? Desktop? *flavor*?).. but I do note mention of LibreOffice thus possibly desktop...

- you can *non-destructively *re-install an earlier release; but there can be complications with this..   I've written about it [here ]("https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533")but do be aware that older programs can have problems using files that were used by later versions (*these issues are package/program specific, and not release specific*), but in most cases there are no issues.

- I wonder if you did any checking before you performed the upgrades.. eg. I always boot *live* systems and use the *Try Ubuntu* options to check out how my hardware does on a newer kernel stack; eg. 22.04 used 5.15 as GA stack & 6.5 currently on HWE, but 24.04 uses 6.8... I also hope you read the *release notes* for each upgrade step & ensured none of the known problems were going to be encountered, or if they were you took note of the mitigations...  Issues like networking/graphics or anything related to your hardware will show up in *live* testing usually.

- have you ensure the *release-upgrade* completed successfully; ie. your sources are all good, no issues/warnings/missing-lines etc on `sudo apt update` and then `sudo apt full-upgrade`... If you attempt to start programs (*you mention not starting*) from terminal are there any clues appearing on the terminal (*I find terminals easier than going to look up system logs as using GUI often requires*), or clues exist elsewhere (*such as /var/crash/ etc*)

---

### Post by ajgreeny on 2024-06-19
Like phatton1 I also clean installed (Xubuntu 24.04) with almost no problems of any sort other than not immediately installing all the packages I normally need so I suspect upgrading was your problem, not specifically 24.04 being buggy.

I assume you're aware that a direct version upgrade from 22.04 to 24.04 is not even offered yet,though being Linux, there are always workarounds to enable users to carry out such potentially problematic upgrades. 

You do not give any details of how you did the upgrade; did you manually change the repo versions from jammy to noble  and then cross your fingers and hope?

Give as much detail as possible and we may be able to help more. 

However make sure you have good usable backups before doing anything drastic as this will allow you to do a new clean install and then restore your backups should this end up as the easiest and quickest way forward.

---

### Post by Rex Bouwense on 2024-06-19
I too have done fresh installs of 24.04.  Three on my own computers (Ubuntu, Lubuntu, and Xubuntu) and a dozen more.  All are functioning correctly with the exception of the application camera which for some reason failed to recognize the webcam on some computers.  Not a big deal.  Merely installed Cheese and the problem was solved.  I used to wait until the first point release to do an install so the bugs would be patched until I realized that bugs, if any are discovered, are generally patched during the beta release.  Depending on the specs of the computer, Ubuntu 24.04 will install in 12 to 30 minutes.  Re-installing your data from your back up device, and configuring the computer according to your own desire takes as long as it takes.  (A separate home on the hard drive of course will cut that time as has already been pointed out by Rubi1200).  So, if you want the new LTS release before the first point release do a fresh install.  I have been a full-time Ubuntu user since 2008.

---

### Post by grahammechanical on 2024-06-19
I have a fresh install of Ubuntu 24.04 LTS. I do not find it particularly buggy. I have noticed a lot of after-release updates. It might just be my imagination, but it seems that there are a lot more after-release updates than with previous versions. I have not been counting but I think that LibreOffice has had at least two updates since the last week of April.

So, I agree with the advice to either wait until the first point release (six months after release) or put in a fresh install.

Regards

---

### Post by patrick_g2 on 2024-06-19
I have to agree with the subject of this thread. I am almost done with 24.04. I have installed it on my new machine 7 times and have yet to have a installation that I can trust. I have been running 22.04 on my old machine and it is pretty bullet proof. If I could find a down load of 22.04 I would install it instead and let 24.04 mature more. I have even been looking at the other Distros to see if I can find a current build that I can trust.

---

### Post by yancek on 2024-06-19
> If I could find a down load of 22.04 I would install it  

Are you joking??  Putting 'download ubuntu 22.04' in any search engine should get you there so if you can't do that, I can see why you're having problems.

[https://releases.ubuntu.com/jammy/](https://releases.ubuntu.com/jammy/)

---

### Post by nicolasdentremont on 2024-06-19
24.04 has been working fine here on my end. I started with vanilla then went to Xubuntu 24.04 with no issues to note.

---

### Post by pgershon on 2024-06-20
By "clean install" do you mean erase the drive first including data?
It might be helpful if you are able to point me towards linked instructions for specifically what you are suggesting.

Many thanks, Paul

---

### Post by pgershon on 2024-06-20
Its desktop.

Terminal: Libreoffice --writer
Warning: Failed to launch javaldx - java may not function correctly
/usr/lib/libreoffice/progream/soffice.bin: error while loading shared libraries libldap_r-2.4.so.2: cannot open shared object file: No such file or directory

---

### Post by pgershon on 2024-06-20
> **phatton1 said:**
> Sorry I can't be much help with this Paul, but there were several warnings not to upgrade to 24.04 yet. 
I have performed a clean install on my two computers and everything works well.
It may be worth backing up any data and clean installing.
The full install is fast, so you can be back up and running in less time than you've already spent and at the end of it you should have a good stable system again

By "clean install" do you mean erase the drive first including data?
It might be helpful if you are able to point me towards linked instructions for specifically what you are suggesting.

Many thanks, Paul

---

### Post by pgershon on 2024-06-20
> **ajgreeny said:**
> Like phatton1 I also clean installed (Xubuntu 24.04) with almost no problems of any sort other than not immediately installing all the packages I normally need so I suspect upgrading was your problem, not specifically 24.04 being buggy.

I assume you're aware that a direct version upgrade from 22.04 to 24.04 is not even offered yet,though being Linux, there are always workarounds to enable users to carry out such potentially problematic upgrades. 

You do not give any details of how you did the upgrade; did you manually change the repo versions from jammy to noble  and then cross your fingers and hope?

Give as much detail as possible and we may be able to help more. 

However make sure you have good usable backups before doing anything drastic as this will allow you to do a new clean install and then restore your backups should this end up as the easiest and quickest way forward.

How I did the upgrade:
sudo apt update
sudo apt dist-upgrade
sudo apt update
sudo apt list --upgradable | more
sudo apt upgrade
sudo apt install ubuntu-release-upgrader-core
grep 'lts' /etc/update-manager/release-upgrades
prompt=lts
sudo ufw allow 1022/tcp comment 'open portssh TCP/1022 as failsafe for upgrades'
sudo ufw status
sudo do-release-upgrade -d
sudo nano /etc/update-manager/release-upgrades
sudo do-release-upgrade
sudo snap refresh
sudo do-release-upgrade
sudo sed -i 's/Prompt=normal/prompt=lts/g' /etc/update-manager/release-upgrades
cat /etc/update-manager/release-upgrades
sudo update-manager -d
lsb_release -a
sudo apt-update && sudo apt upgrade

---

### Post by ajgreeny on 2024-06-20
My goodness!
You really did jump ahead of the system, didn't you!

I have to say that I have never come across such a long and complicated way to carry out a version upgrade but that's not surprising as i have always clean installed my root partition by choosing "Something else" ie, manual partitioning, leaving my/home partition untouched.

I shall have to leave this to others as I'm definitely out of my depth here dealing with something I've never done

---

### Post by currentshaft on 2024-06-20
> **pgershon said:**
> I trusted Canonical and upgraded from 22.04 lts to 24.04 lts on an optiplex 5090 that came with 20.04 installed. I trusted Canonical because prior upgrades have been issue-free.

This time, it was a major mistake, I did not realize 24.04 was buggy. Could I please have advice on how to back-grade if possible? THanks. I first upgraded from 22.04 to 23.10 then from there to 24.04. I can give more details if required, but it was all done with standard commands, I think, and I did not see any obvious errors.

There is no advice online that I can find: It is not since the 1990s that I had an OS that failed to connect to internet ("Connection failed: Activation of network connection failed"). This is a very standard wired connection, there is nothing I can find online for 24.04 failing to connect a wired connection, or for any Ubuntu failing to do this on hardware that previously worked fine. No, its not my settings (the network guy here also cannot fix it. No, it is not ipv6. No it is not the clock.

Its weird because it connected to the internet presumably to download the upgrades with no issue, in both the above upgrade steps, so I am assuming 24.04 broke my internet connection in a final installation step after all downloading was complete.

Also:

Clicking on the libre office writer icon does nothing, libreoffice calc icon does nothing, and so it goes on. This upgrade seems so broken that I cannot see any obvious solution other than, perhaps grudgingly admitting that Windows has cornered the market for a reason because I am several hours into this now, and to be honest if I had known that basic stuff that has been working for many years would be broken again, I would have definitely just left the whole thing alone for the forseeable future.

Any expert advice much appreciated.

Thanks, Paul

The level of entitlement in this post is palpable.

Why do you feel you're "owed" a "warning" because you lack system adminstration skills to debug problems with your computer?

And the lack of those skills is obvious from your approach to problem solving: ask the "network guy" - he doesn't know? Give up and rant on a forum.

How about ... what troubleshooting steps have you tried? What errors or specific issues are you seeing? What logs have you checked? You seem to have committed almost no effort to actually addressing your issues.

An adjustment in attitude and reduction in hyperbole will get you much further in life and especially when asking strangers for help.

---

### Post by pgershon on 2024-06-20
> **ajgreeny said:**
> My goodness!
You really did jump ahead of the system, didn't you!

I have to say that I have never come across such a long and complicated way to carry out a version upgrade but that's not surprising as i have always clean installed my root partition by choosing "Something else" ie, manual partitioning, leaving my/home partition untouched.

I shall have to leave this to others as I'm definitely out of my depth here dealing with something I've never done

- I got it from itsfoss which I have found/assumed to be completely trustworthy, so I trusted it.

---

### Post by pgershon on 2024-06-20
> **ajgreeny said:**
> My goodness!
You really did jump ahead of the system, didn't you!

I have to say that I have never come across such a long and complicated way to carry out a version upgrade but that's not surprising as i have always clean installed my root partition by choosing "Something else" ie, manual partitioning, leaving my/home partition untouched.

I shall have to leave this to others as I'm definitely out of my depth here dealing with something I've never done



[https://itsfoss.com/upgrade-ubuntu-to-newer-version/](https://itsfoss.com/upgrade-ubuntu-to-newer-version/)

---

### Post by pgershon on 2024-06-20
> **currentshaft said:**
> The level of entitlement in this post is palpable.

Why do you feel you're "owed" a "warning" because you lack system adminstration skills to debug problems with your computer?

And the lack of those skills is obvious from your approach to problem solving: ask the "network guy" - he doesn't know? Give up and rant on a forum.

How about ... what troubleshooting steps have you tried? What errors or specific issues are you seeing? What logs have you checked? You seem to have committed almost no effort to actually addressing your issues.

An adjustment in attitude and reduction in hyperbole will get you much further in life and especially when asking strangers for help.


->Nothing I wrote was ad hominem. Everything you have written is ad hominem. I think that speaks for itself.

---

### Post by pgershon on 2024-06-20
> **pgershon said:**
> ->Nothing I wrote was ad hominem. Everything you have written is ad hominem. I think that speaks for itself.

I also feel that if Ubuntu wants the reputation for being the most solid, stable, reliable distro, then it should be the truth. If that is not the reputation it wants, then I am not entitled to anything.

---

### Post by deadflowr on 2024-06-20
The warning is the -d flag.

---

### Post by QIII on 2024-06-20
Choosing to use that method of upgrade (do-release-upgrade) before the first dot release is prone to unpredictable results.  This is why it is recommended, by Canonical and all of us here, that you do a fresh install or that you don't upgrade an LTS release until after the first dot release of the next LTS -- best if you have created a separate /home directory at your first install time (which you do not format if you decide to do a fresh installation), back up all of your important files to another medium, and use

```
dpkg --get-selections > package_list
``` 

to save a list of your applications to a separate medium (after uninstalling all third-party applications) and then

```
dpkg --get-selections < package_list
```

when you have done a fresh installation.  

There is a bit more to it, of course, but it is all documented and available as advice here.

There is no need to cast aspersions.

Microsoft, by the way, "cornered the market" by the pure happenstance of having been at the right place at the right time and solidifying its desktop presence before Linux came along.  Notice that I said "desktop".  Linux (in some form) is used on more devices, by at least a margin of and order of magnitude, than Microsoft products.

---

### Post by #&amp;thj^% on 2024-06-20
+1 with deadflowr
Just a friendly helping hand:
This command will:
```

sudo do-release-upgrade --devel-release
```
Or the same for "sudo do-release-upgrade -d"
Why would someone want to:
> 
Motivation: For users interested in testing and contributing to the development of Ubuntu, upgrading to the latest development release is important. It allows users to access bleeding-edge features and actively participate in the development process.

Explanation:
[list]
    [*]sudo: Same as explained before.
    [*]do-release-upgrade: Same as explained before.
    [*]--devel-release: This option instructs the command to upgrade to the latest development release instead of the stable[/list]

Apt is very powerful, it's best to fully understand what you called your system to do.

---

### Post by pgershon on 2024-06-20
> **QIII said:**
> Choosing to use that method of upgrade (do-release-upgrade) before the first dot release is prone to unpredictable results.  This is why it is recommended, by Canonical and all of us here, that you do a fresh install or that you don't upgrade an LTS release until after the first dot release of the next LTS -- best if you have created a separate /home directory at your first install time (which you do not format if you decide to do a fresh installation), back up all of your important files to another medium, and use

```
dpkg --get-selections > package_list
``` 

to save a list of your applications to a separate medium (after uninstalling all third-party applications) and then

```
dpkg --get-selections < package_list
```

when you have done a fresh installation.  

There is a bit more to it, of course, but it is all documented and available as advice here.

There is no need to cast aspersions.

Microsoft, by the way, "cornered the market" by the pure happenstance of having been at the right place at the right time and solidifying its desktop presence before Linux came along.  Notice that I said "desktop".  Linux (in some form) is used on more devices, by at least a margin of and order of magnitude, than Microsoft products.

- Thanks. I realize I am not entitled to anything other than Ubuntu's reputation. Nothing more, nothing less. For example, a walk in the park is also a free gift, but if you fell into an drainage hole covered with weak plywood during that walk, which involved a trip to the hospital, I think you might feel like calling it out, even though it was free with no automatic expectations of benefit.

Just to asK: Do you think it is likely that the Aug 15 update will rescue my current system? Or do you think that literally my only option at this point is a clean install?

Also, I will note that the reason I upgraded now, was a previous experience of upgrading Ubuntu after the expiration of a repo, which took some time to figure out. That was an upgrade from 21.10 to 22.04 in April 2022, and I just wanted to stay completely on the lts path this time around and do everything promptly to avoid complications later. It backfired.

Thanks, Paul

---

### Post by QIII on 2024-06-20
This drainage hole is well marked. 

I only install interim releases in virtual machines for testing.  My daily drivers all get LTS versions.

Personally, I'd save my important data and do a clean installation.  That's what I do every time.  Even so, I wait for the first dot release to be sure any potential kinks have been worked on.  However, a clean install of 24.04 is not likely to be so fraught as a release upgrade even now.

---

### Post by currentshaft on 2024-06-20
> **pgershon said:**
> ->Nothing I wrote was ad hominem. Everything you have written is ad hominem. I think that speaks for itself.

Is this a joke? Your OP is literally one big ad hominem; in your own words, 24.04 is:

"buggy"
"a major mistake"
(implied) not modern
it "broke" your "internet connection"
not easy to use
worse than Windows
not worth its good reputation

Good riddance, Paul. Millions of happy Ubuntu users beg to differ with your conclusion.

It sucks your system is not working as expected. It is a common solution to try a fresh install to resolve such issues. Good luck.

---

### Post by wildmanne39 on 2024-06-21
Everyone please keep in mind the following from the Code of Conduct:
> The purpose of the Ubuntu Forums is to provide support for Ubuntu. We also want this to be a place where community can develop and we can enjoy one another's company. To achieve this, we strive to maintain an atmosphere that can be enjoyed by all and we ask all members of the community to be respectful at all times. This means please use etiquette and politeness. Treat people with respect. If you do this, the rest of the code of conduct won't need more than a cursory mention.
> Users agree not to post anything abusive, rude, obscene, vulgar, slanderous, hateful, threatening, advertising or marketing related, or sexually-oriented. Material that suggests illegal activity or contains illegal content is also forbidden. We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings. Given that our forums could be used by people at work and school we want to ensure they will not encounter material that will cause them problems or cause their access to our site to be limited, so all content should be safe for both.
> Trolling, Attacks and Flaming: These are always forbidden.

    Trolling is posting in a way that provokes emotional responses.
    Attacks and derogatory terms of any kind are not welcome. This includes references to any operating systems or the companies that produce them.
    Flames are messages that personally attack or call any people names or otherwise harass. These, along with any generally condescending posts will be edited or removed at the moderators discretion.
    If a thread is flame-bait (appears to be intended to start an argument or is likely to cause an argument rather than enhance discussion, as in trolling), it will be locked or removed without notice. Individual flame-bait comments in a post may be deleted or edited at the moderators' discretion.
    If the thread turns into an argument, it can be closed to further comment or removed without notice. Sometimes a moderator may split the thread or jail certain portions in order to keep the discussion going,this is not always possible.


Everyone's participation here is greatly appreciated but please note behavior, how we treat each other on the forum is of upmost importance, to learn and help users the forum members must be courteous to all users seeking help so if a thread needs attention of Staff please use the report button in the thread and report the post and we will take a look at it, to the OP you will get the most help by just stating the specs of your computer along with all information asked for, there is much information needed but two come to mind what wired network card are you using and what wifi card as well because there use to be an issue if a computer had an intel wired card and wifi card it needed a work around, I do not know that is still the case but there may have been a regression, I suggest booting the previous kernel and see if that works in my experience it usually does.

Thank you

---

### Post by TenPlus1 on 2024-06-21
I tried and tested each Ubuntu flavour when 24.04 was released and found that XFCE and KDE were the most stable among them all and the most optimized of desktops to be used for gaming, although I did prefer a minimal install and removed snaps for official .deb alternatives.

---

### Post by Impavidus on 2024-06-22
> **pgershon said:**
> Its desktop.

Terminal: Libreoffice --writer
Warning: Failed to launch javaldx - java may not function correctly
/usr/lib/libreoffice/progream/soffice.bin: error while loading shared libraries libldap_r-2.4.so.2: cannot open shared object file: No such file or directory

That at least is a clear error message. LibreOffice fails to start because it cannot find the libldap library, version 2.4. It turns out that the version of LibreOffice you get in Ubuntu 24.04 uses libldap version 2.6, which would be the version installed on 24.04. The LibreOffice on Ubuntu 22.04 uses version 2.5. Version 2.4 is used by LibreOffice on Ubuntu 20.04. In other words: you somehow got an outdated version of the LibreOffice executable. I'm surprised it actually worked on 22.04. Such an error may result from manual installation of programs or incomplete release upgrades. This should never happen with a clean install. It looks like your system was dirty already before starting the release upgrade; the upgrade just made the dirt more visible.

> **pgershon said:**
> - Thanks. I realize I am not entitled to anything other than Ubuntu's reputation. Nothing more, nothing less. For example, a walk in the park is also a free gift, but if you fell into an drainage hole covered with weak plywood during that walk, which involved a trip to the hospital, I think you might feel like calling it out, even though it was free with no automatic expectations of benefit.

Just to asK: Do you think it is likely that the Aug 15 update will rescue my current system? Or do you think that literally my only option at this point is a clean install?

Also, I will note that the reason I upgraded now, was a previous experience of upgrading Ubuntu after the expiration of a repo, which took some time to figure out. That was an upgrade from 21.10 to 22.04 in April 2022, and I just wanted to stay completely on the lts path this time around and do everything promptly to avoid complications later. It backfired.

Thanks, Paul
Installing upgrades won't fix your problem. Upgrades fix problems with the installed software, not with the configuration of your system. In theory, this can be solved by tracking down every piece of dirt on your system and fixing it, but it would take an expert and a lot of time. Better to try a fresh install. That's what an expert would do.

Interim releases like 21.10 are supported for just 9 months. LTS releases for 5 years, so there was no hurry to get off 22.04. And yes, one should indeed upgrade before the old version reaches end of life.

---

### Post by matt-rw on 2024-06-22
I am currently running 23.10.   I typically upgrade soon after new releases, but I read that 24.04 is buggy and one should wait for 24.04.1 (out in August).   Now, in this thread, I'm seeing that using --devel-release is an option.  Is that the consensus for an upgrade now?

---

### Post by #&amp;thj^% on 2024-06-22
> **matt-rw said:**
> I am currently running 23.10.   I typically upgrade soon after new releases, but I read that 24.04 is buggy and one should wait for 24.04.1 (out in August).   Now, in this thread, I'm seeing that using --devel-release is an option.  Is that the consensus for an upgrade now?

This "--devel-release" will take you to 24.10 not 24.04

If it were me and I like a better tested system, I'd wait until 24.04.2, however if your not faint of heart then go for it.

---

### Post by aljames2 on 2024-06-22
> **1fallen said:**
> This "--devel-release" will take you to 24.10 not 24.04

If it were me and I like a better tested system, I'd wait until 24.04.2, however if your not faint of heart then go for it.

Bingo, what I do.  At least wait for the .1, but in my production systems it will be even longer because it is not a 10 minute thing. Gosh, I’ll have another milestone birthday and start qualifying for my senior coffees before I’m on 24.04 LTS.  Ubuntu is wonderful!  22.04 LTS still has full support till April 2027.

---

### Post by #&amp;thj^% on 2024-06-22
> **aljames2 said:**
> Bingo, what I do.  At least wait for the .1, but in my production systems it will be even longer because it is not a 10 minute thing. Gosh, I’ll have another milestone birthday and start qualifying for my senior coffees before I’m on 24.04 LTS.  Ubuntu is wonderful!  22.04 LTS still has full support till April 2027.

Yep on my ZFS system I'm on 24.10 now.

This is just my findings and your mileage may vary, I like 24.10 a bit more, so improvements/fix's that are coming in will be a improvement for 24.04.1.

But I also know that you have gained some sound wisdom along the way.....I trust you'll do the right thing for yourself. :)

---

### Post by Impavidus on 2024-06-24
> **matt-rw said:**
> I am currently running 23.10.   I typically upgrade soon after new releases, but I read that 24.04 is buggy and one should wait for 24.04.1 (out in August).   Now, in this thread, I'm seeing that using --devel-release is an option.  Is that the consensus for an upgrade now?

23.10 will reach end of life on 11 July, 17 days from now. Get upgraded to 24.04 within the next two weeks. The recommendation to wait for the .1 release is for LTS&#8594;LTS upgrades.

The --devel-release option is there to upgrade when the upgrade path hasn't been released yet, but is still in testing (and therefore not recommended). The upgrade path from 23.10&#8594;24.04 was released weeks ago.

---

### Post by pgershon on 2024-06-25
> **currentshaft said:**
> Is this a joke? Your OP is literally one big ad hominem; in your own words, 24.04 is:

"buggy"
"a major mistake"
(implied) not modern
it "broke" your "internet connection"
not easy to use
worse than Windows
not worth its good reputation

Good riddance, Paul. Millions of happy Ubuntu users beg to differ with your conclusion.

It sucks your system is not working as expected. It is a common solution to try a fresh install to resolve such issues. Good luck.

As you know, its not a joke: 'Ad hominem' means against the person. Look it up if you know how to use the internet.

---

### Post by currentshaft on 2024-06-25
> **pgershon said:**
> As you know, its not a joke: 'Ad hominem' means against the person. Look it up if you know how to use the internet.

Why would I, when you have so gracefully demonstrated its meaning here for all to see?

---

### Post by gronbach on 2024-09-14
I'm not a Linux Guru.  
Maybe I'm a "power user" but even then that's a bit of a stretch.
I haven't spent years opening up the kernel of every release nor do i have every "sudo apt" command memorized. Some people are really hard core.  I just want something besides Windows.

That being said, I've been an Ubuntu user since version 8.04.  Not every upgrade has been perfect but none have been this bad in a long time.  I'm actually surprised. It's like a bunch of drunk monkeys threw together some scripts.  How very microsoft.

This original post was dated June 2024.  It is now 3 months later.  Has ANYONE at ubuntu bothered to look at the unmitigated disaster this LTS has made?

At first it wouldn't upgrade because of some ppa issue.  Once I got that fixed, then it was because of some other dpkg issue.  Once I got that fixed (or at least I thought I did) it changed my display driver from Nvidia to Mesa intel or something like that.

I googled every error in its entirety.  I did so may apt this, update that and fix this other thing that I lost track.  I will tell you that it all went to shizzle when I followed this advice here:
[https://github.com/oddmario/NVIDIA-Ubuntu-Driver-Guide?tab=readme-ov-file](https://github.com/oddmario/NVIDIA-Ubuntu-Driver-Guide?tab=readme-ov-file)

About half way through this process my laptop which is a dell Precision 7710 did the ubuntu equivalent of a blue screen.  "Oh no!  Something has gone wrong"  Really?  That's what you get?  So I got into my console through control-alt-f3, starting doing a bunch of other recommended apt this, ppa that, dpkg the other thing until it eventually wouldn't boot at all.  I got stuck behind something about not being able to change from disk cool to something... I don't even remember.

Ultimately I had to reinstall gnome.  So I've got my log back.  Hooray!!!  But now my graphics are Mario Nintendo first release bad.  I'm afraid to even try and fix anything else.  I think I'm going to back up my data and reinstall 22.04

---

