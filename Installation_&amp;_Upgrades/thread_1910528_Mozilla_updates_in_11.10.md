---
title: "Mozilla updates in 11.10"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by Tranas on 2012-01-17
Is there a simple way to update Firefox and Thunderbird to the 9.0.1 versions?
[versions 10 are set for release at the end of the month]

Neither Synaptic or the Ubuntu Software Center show either upgrade or full versions, and linking to an existing profile with the installed Ubuntu/Mozilla versions breaks existing addons. [8x is not compatible with updated addons in these profiles].

TIA

---

### Post by fantab on 2012-01-17
> **Tranas said:**
> Is there a simple way to update Firefox and Thunderbird to the 9.0.1 versions?
[versions 10 are set for release at the end of the month]

Neither Synaptic or the Ubuntu Software Center show either upgrade or full versions, and linking to an existing profile with the installed Ubuntu/Mozilla versions breaks existing addons. [8x is not compatible with updated addons in these profiles].

TIA

I am using 11.10 and Firefox version has been updated to 9.0.1.

just run updates from update manager.

---

### Post by spacecheck on 2012-01-17
For FF 9.0.1 I selected the "Pre-released updates oneiric-proposed" in the source settings then ran an update with Update Manager, then unchecked everything but FF 9.0.1 and the FF related packages. This worked fine also for T-bird. Afterwards, I reverted from the "proposed" sources, so I wouldn't have to keep seeing and de-selecting all the other proposed stuff.

Hope this helps. IF so, please use the thread tools to mark the thread Solved.

Good luck!

---

### Post by Tranas on 2012-01-17
> **spacecheck said:**
> For FF 9.0.1 I selected the "Pre-released updates oneiric-proposed" in the source settings then ran an update with Update Manager, then unchecked everything but FF 9.0.1 and the FF related packages. This worked fine also for T-bird. Afterwards, I reverted from the "proposed" sources, so I wouldn't have to keep seeing and de-selecting all the other proposed s!tuff.

A little more detail would be helpful. Selected 'source settings' where? [Let's try TBird first]

Update manager sees no updates - TBird remains at version 8.

---

### Post by Tranas on 2012-01-17
I presume that the 'source settings' are in System Settings, however the suggested choice on this particular box produces 89 possible updates - in some mysterious sort of order - one of which is a generic 'Thunderbird'. 

Problem is, it is shown as 9.0 build 2 [are you feeling lucky today??] - whatever that is. 

To get this one unknown, I need to 'uncheck' 88 boxes?? Then reconfigure source settings.

Apparently, the update manager naming conventions differ from those of Firefox, and from what I know, the 9.0.1 is a stable build that has been out since December 23 - hardly something Pre-release. This whole procedure appears somewhat mickey-mouse.

YMMV

---

### Post by dino99 on 2012-01-17
either 9 or 9+, you will dont see the difference :(

for better knowledge about packages, use synaptic

---

### Post by snowpine on 2012-01-17
"Proposed" updates are **not recommended/approved as stable**, Firefox 9.0.1 is the 11.10 repos, repeat: **you do not need to enable the proposed repo**. 

If you want new software the day it is released, you can download it (for example from mozilla.org) and install it on your machine in about 30 seconds. You take responsibility for your own system (this is the beauty and freedom of "open source").

If you want automatic updates fed to you by the Ubuntu Team then you wait a few days until they've tested these updates for breakage. For Firefox 9.0.1 it took about 4 days [as you can read here]("http://changelogs.ubuntu.com/changelogs/pool/main/f/firefox/firefox_9.0.1+build1-0ubuntu0.11.10.2/changelog"). I guess we have different definitions of "mickey-mouse;" personally my definition of mickey-mouse is "updates that bork our customers' computers because we didn't test them". :(

---

### Post by goofey24 on 2012-01-17
??

---

### Post by Tranas on 2012-01-17
> **snowpine said:**
> "Proposed" updates are **not recommended/approved as stable**, Firefox 9.0.1 is the 11.10 repos, repeat: **you do not need to enable the proposed repo**. 

If you want new software the day it is released, you can download it (for example from mozilla.org) and install it on your machine in about 30 seconds. You take responsibility for your own system (this is the beauty and freedom of "open source").

If you want automatic updates fed to you by the Ubuntu Team then you wait a few days until they've tested these updates for breakage. For Firefox 9.0.1 it took about 4 days [as you can read here]("http://changelogs.ubuntu.com/changelogs/pool/main/f/firefox/firefox_9.0.1+build1-0ubuntu0.11.10.2/changelog"). I guess we have different definitions of "mickey-mouse;" personally my definition of mickey-mouse is "updates that bork our customers' computers because we didn't test them". :(

9.0.1 has been out for better than three weeks, certainly more than a couple of days by my count. Considering that both Firefox and Thunderbird are the default browser and mail programs for Ubuntu 11.10 seems it should be normal to expect them to get more than ho-hum attention in the update system. 

The native Update Manager will *NOT* update Tbird 8.0, it is not shown as an available update and Synaptic does not have it either. 

I am glad you tested 9.0.1 - I would appreciate it if you could explain the simple way  to update [the installed from the Ubuntu live CD] version 8.

TIA

---

### Post by snowpine on 2012-01-17
Firefox 9.0.1 has been in the 11.10 repos since Dec 28 as several people are trying to tell you. It took Canonical 4 days **including Christmas** to give you this update, asking nothing from you in return.

Then the question you should be asking yourself is not "why isn't Ubuntu providing me with timely updates?" but "why is my system not up to date with the updates Ubuntu has so thoughtfully provided?"

Here is some basic reading material on software sources and the update manager: 

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Personally here is my basic troubleshooting procedure for update related issues:

```
cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Tranas on 2012-01-17
> **snowpine said:**
> Firefox 9.0.1 has been in the 11.10 repos since Dec 28 as several people are trying to tell you. It took Canonical 4 days **including Christmas** to give you this update, asking nothing from you in return.

Then the question you should be asking yourself is not "why isn't Ubuntu providing me with timely updates?" but "why is my system not up to date with the updates Ubuntu has so thoughtfully provided?"

Here is some basic reading material on software sources and the update manager: 

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Personally here is my basic troubleshooting procedure for update related issues:

```
cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
```

Try Thunderbird - not Firfefox.

The question *you* should be asking is why Ubuntu's native Update Manager does not work for Thunderbird. 

Those are interesting links, but I think Canonical handles the repositories for Firefox and Thunderbird on Ubuntu, as you have already proudly pointed out. 

I am just a user. I did not install either Firefox or Thunderbird - they are part of the Ubuntu install package by default. I want a simple way to update and figured update manager was intended to be just that - but in this case, it does not work.

sudo apt-get dist-upgrade

<gets the following on the box in question>

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Which, as far as I can tell, is nothing more than the geek command line version of the what the Update Manager GUI presents. aka nothing to upgrade.

Which is why that box remains at TB 8 - the update manager does not see *any* ugrade for Thunderbird [regardless of what others have pointed out] unless I enable 'proposed repo' <gasp>

---

### Post by snowpine on 2012-01-17
> **Tranas said:**
> Try Thunderbird - not Firfefox.

Sorry if my reply was misguided. Your post #1 suggested you were having difficulty updating Firefox to 9.0.1, and that is what I replied to.

The latest Thunderbird in the 11.10 repos is 8.0+build1-0ubuntu0.11.10.1 according to: [http://packages.ubuntu.com/oneiric/thunderbird](http://packages.ubuntu.com/oneiric/thunderbird)

Is that what you have on your system? If so then your 11.10 looks up to date as far as I can see.

---

### Post by spacecheck on 2012-01-17
> the update manager does not see *any* ugrade for Thunderbird [regardless  of what others have pointed out] unless I enable 'proposed repo'  <gasp>I did not get an update shown for either FF or Tbird, even after the absolutely extraordinary super magnifabulous holiday efforts of the npu Ubuntu developers.

So on the 30th, I went ahead and enabled "oneiric-proposed" sources to see if FF 9.0.1 & Tbird were available, especially because there was an extremely important security update involved(!!!).

Lo and behold, thar she blows! So, as I mentioned before, I quickly selected the updates I felt necessary and installed them posthaste. Sorry if anyone gets upset with my having handled in this so obviously evil manner...

As evidence of install timing, please allow me to expose the respective /var/log/apt history:
```
Start-Date: 2011-12-30  14:14:56
Commandline: aptdaemon role='role-commit-packages' sender=':1.48'
Upgrade: thunderbird:amd64 (8.0+build1-0ubuntu0.11.10.1, 9.0+build2-0ubuntu0.11.10.1), xfce4-weather-plugin:amd64 (0.7.4-1, 0.7.4-1ubuntu0.1), firefox:amd64 (8.0+build1-0ubuntu0.11.10.3, 9.0.1+build1-0ubuntu0.11.10.2), firefox-locale-en:amd64 (8.0+build1-0ubuntu0.11.10.3, 9.0.1+build1-0ubuntu0.11.10.2), xul-ext-ubufox:amd64 (1.0-0ubuntu2.1, 1.0.2-0ubuntu0.11.10.1), firefox-gnome-support:amd64 (8.0+build1-0ubuntu0.11.10.3, 9.0.1+build1-0ubuntu0.11.10.2)
End-Date: 2011-12-30  14:19:37
```I had to do this for BOTH my Ubuntu 11.10 AND my Xubuntu 11.10 systems...

@Tranas - You can either open the **Software Center**, click the **Edit** menu and choose **Software Sources** applet, or select "Update Manager" and click the "Settings" button, or even edit the source.list directly, to add repositories, be they "proposed" or not. ", 9.0+build2-0ubuntu0.11.10.1" has been available in "proposed" since at least 30th Dec. It also contained a security update...

Screenshot shows the location for source selections.

Remember, if a suggestion resolves your problem, be sure to use the thread tools to mark the thread solved.

Have fun!

---

### Post by Tranas on 2012-01-17
> **spacecheck said:**
> I did not get an update shown for either FF or Tbird, even after the absolutely extraordinary super magnifabulous holiday efforts of the npu Ubuntu developers.

FF did not show up in updates for me initially, but I never pursued the issue further. I have no problem with the concept in Ubuntu - and given the flakiness of FF upgrades seems perfectly logical to test it.

[QUOTE=So on the 30th, I went ahead and enabled "oneiric-proposed" sources to see if FF 9.0.1 & Tbird were available, especially because there was an extremely important security update involved(!!!).[/QUOTE]

I did not find locating the above update 'user friendly'. Am not sufficiently familiar with Ubuntu to understand why there is a difference in naming conventions

Lo and behold, thar she blows! So, as I mentioned before, I quickly selected the updates I felt necessary and installed them posthaste. Sorry if anyone gets upset with my having handled in this so obviously evil manner...

As evidence of install timing, please allow me to expose the respective /var/log/apt history:
```
Start-Date: 2011-12-30  14:14:56
Commandline: aptdaemon role='role-commit-packages' sender=':1.48'
Upgrade: thunderbird:amd64 (8.0+build1-0ubuntu0.11.10.1, 9.0+build2-0ubuntu0.11.10.1), xfce4-weather-plugin:amd64 (0.7.4-1, 0.7.4-1ubuntu0.1), firefox:amd64 (8.0+build1-0ubuntu0.11.10.3, 9.0.1+build1-0ubuntu0.11.10.2), firefox-locale-en:amd64 (8.0+build1-0ubuntu0.11.10.3, 9.0.1+build1-0ubuntu0.11.10.2), xul-ext-ubufox:amd64 (1.0-0ubuntu2.1, 1.0.2-0ubuntu0.11.10.1), firefox-gnome-support:amd64 (8.0+build1-0ubuntu0.11.10.3, 9.0.1+build1-0ubuntu0.11.10.2)
End-Date: 2011-12-30  14:19:37
```I had to do this for BOTH my Ubuntu 11.10 AND my Xubuntu 11.10 systems..[/QUOTE]

and even in the above it is both 9.0+build2 and 9.0.1+build1. So I presume that the devs are customizing the 9.01 version for 11.10 [I think...]. The base issue remains - almost a month after a major build, TB is not in the Updater [on my installation] and I am left with either rolling back Win users to 8x or not using Ubuntu for mail on the same profiles. PITA

[QUOTE=@Tranas - You can either open the **Software Center**, click the **Edit** menu and choose **Software Sources** applet, or select "Update Manager" and click the "Settings" button, or even edit the source.list directly, to add repositories, be they "proposed" or not. ", 9.0+build2-0ubuntu0.11.10.1" has been available in "proposed" since at least 30th Dec. It also contained a security update...

Screenshot shows the location for source selections.[/QUOTE]

Your method is a workaround and does not solve my issue IMHO. My users are not geek enabled - they need a simple method to update/upgrade. At this point, I am trying to figure out if it is just a mistake that the upgrade has not posted, this is all by intent because the upgrade is not stable, or the update system is broken.

---

### Post by Tranas on 2012-01-17
> **snowpine said:**
> Sorry if my reply was misguided. Your post #1 suggested you were having difficulty updating Firefox to 9.0.1, and that is what I replied to.

The latest Thunderbird in the 11.10 repos is 8.0+build1-0ubuntu0.11.10.1 according to: [http://packages.ubuntu.com/oneiric/thunderbird](http://packages.ubuntu.com/oneiric/thunderbird)

Is that what you have on your system? If so then your 11.10 looks up to date as far as I can see.

No problem. [in post #4 I could have been more precise] Yes, that is exactly my problem - I am at 8x on the box in question, the Updater sees no updates for it and accessing updated profiles on Win machines breaks the profiles - makes the Ubuntu machine useless for mail.

So my primary questions now are -

 1) is it just a mistake that the upgrade has not posted?
2) is this is all by  intent because the upgrade is not stable? or -
3) is the update system is  broken?

---

### Post by vasa1 on 2012-01-18
> **Tranas said:**
> Is there a simple way to update Firefox and Thunderbird to the 9.0.1 versions?
[versions 10 are set for release at the end of the month]

Neither Synaptic or the Ubuntu Software Center show either upgrade or full versions, and linking to an existing profile with the installed Ubuntu/Mozilla versions breaks existing addons. [8x is not compatible with updated addons in these profiles].

TIA

> I have removed FF from my 11.10 install.
[Source]("http://ubuntuforums.org/showpost.php?p=11620055&postcount=2")

So you just need information on Thunderbird now. My suspicion is that the staff are overworked and that there aren't qualified volunteers coming forward.

---

### Post by Tranas on 2012-01-18
> **vasa1 said:**
> [Source]("http://ubuntuforums.org/showpost.php?p=11620055&postcount=2")

So you just need information on Thunderbird now. My suspicion is that the staff are overworked and that there aren't qualified volunteers coming forward.

 Thanks. Firefox 9.0.1 now shows up in Synaptic, However Thunderbird [and Chromium] - stale update.  Will wait and see how this works out. 11.10 is temporary in any event as I expect to move to 12.04  Just want to be sure the 'system' works.

---

### Post by vasa1 on 2012-01-18
> **Tranas said:**
> Thanks. Firefox 9.0.1 now shows up in Synaptic, However Thunderbird [and Chromium] - stale update.  Will wait and see how this works out. 11.10 is temporary in any event as I expect to move to 12.04  Just want to be sure the 'system' works.

You may find this link helpful:
[https://code.launchpad.net/~mozillateam/thunderbird/thunderbird-trunk.head](https://code.launchpad.net/~mozillateam/thunderbird/thunderbird-trunk.head)

If anyone knows of a better way to "monitor" progress, do share :)

---

### Post by snowpine on 2012-01-18
> **Tranas said:**
> 1) is it just a mistake that the upgrade has not posted?
2) is this is all by  intent because the upgrade is not stable? or -
3) is the update system is  broken?

4) Ubuntu is not a "rolling release" distribution. Applications are "frozen" at their current version on release day, therefore 11.10 will always have applications dating from October 2011. (Newer apps go into the next release, 12.04 in this case). 

5) Firefox is the one exception to this policy due to the new Mozilla quick-release cycle.

6) Users can easily upgrade individual applications as needed, for example Thunderbird daily builds are available [here]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa").

---

### Post by Tranas on 2012-01-18
> **snowpine said:**
> 4) Ubuntu is not a "rolling release" distribution. Applications are "frozen" at their current version on release day, therefore 11.10 will always have applications dating from October 2011. (Newer apps go into the next release, 12.04 in this case). 

5) Firefox is the one exception to this policy due to the new Mozilla quick-release cycle.

6) Users can easily upgrade individual applications as needed, for example Thunderbird daily builds are available [here]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa").

Well maybe this kind of parsing is part of the Ubuntu 'culture' doubethink. You maybe suggesting apps available thru upgrade manager are 'frozen' as of October 2011?? What kind of sense does that make?

I look at the Wiki, and I see standard support through first quarter of 2013.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_12.04_LTS_.28Precise_Pangolin.29](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_12.04_LTS_.28Precise_Pangolin.29)

Install from live CD, run Update Manager, install is current. It aint rocket science.

<begin parse standard support lol>

---

### Post by snowpine on 2012-01-18
> **Tranas said:**
> Well maybe this kind of parsing is part of the Ubuntu 'culture' doubethink. You maybe suggesting apps available thru upgrade manager are 'frozen' as of October 2011?? What kind of sense does that make?

It makes a lot of sense if you think about it. Ubuntu has always worked that way, so do most Linux distros.

Here is an analogy: Imagine you bought a 2011 model car, now it is 2012. You take your car to the dealership for an oil change. Do they replace your engine with the engine from the 2012 model? Do they replace your tires? Your dashboard? Your radio? Of course not. Why? Because your car is designed to run safely and reliably for many years using the parts it came off the assembly line with. Maybe in 2015 Ford starts putting laser steering wheels in their cars... Does that mean you go out to your garage one morning and your 2011 model magically has a laser steering wheel now? 

Ubuntu works the same way. Let's say you install 12.04 in April and it works great. It recognizes your hardware, provides the applications you want, and generally meets your needs in every way. Why would Canonical suddenly replace parts of your perfectly-functional system in 2013, or 2014, etc? That would be completely nuts and interrupt the work flow of the users who chose "long term support" specifically because they didn't want to mess with frequent updates.

If you don't like this philosophy (sounds like you don't) then you may be happier with one of the small minority of distros with a "rolling release" schedule like Arch, Gentoo, Debian Unstable, etc. These don't have separate releases (like Ubuntu has 11.10, 12.04, etc) but rather each individual application is updated whenever an update becomes available from the upstream developer (Mozilla etc). You get small updates on a daily/weekly basis rather than a big update every 6 months as with Ubuntu. Different strokes for different folks. :)

---

### Post by Tranas on 2012-01-18
> **snowpine said:**
> Different strokes for different folks. 

To be sure.

But this is just one of the reasons you have 1% of the market [and apparently proud of it].

Because even giving it away free, most folks are not willing to put up with your version of the stroke.

---

### Post by snowpine on 2012-01-18
> **Tranas said:**
> To be sure.

But this is just one of the reasons you have 1% of the market [and apparently proud of it].

Because even giving it away free, most folks are not willing to put up with your version of the stroke.

Who do you mean by "you" exactly? Everyone on Ubuntu Forums is just an ordinary guy or gal like you, hanging out and talking about Ubuntu. I am not responsible for Ubuntu so arguing with me will accomplish nothing. ;)

If Ubuntu is not right for your needs, then we are friendly and will help you find the right tool for the job. Maybe you would be happier with a "rolling release" distro like Arch? Or maybe you would like some easy instructions to install the latest Thunderbird in 30 seconds; would that change your opinion of Ubuntu if you knew how easy it was?

(Out of curiosity, when you run Windows Update on an Windows PC, does it automatically update your Thunderbird to the latest version?)

---

### Post by snowpine on 2012-01-18
You may find this article interesting. It is written for another distro (Red Hat) but the basic concepts apply equally to Ubuntu. The author explains how "freezing" application version numbers is important to a stable, long-term support release:

[https://access.redhat.com/security/updates/backporting/?sc_cid=3093](https://access.redhat.com/security/updates/backporting/?sc_cid=3093)

---

### Post by Tranas on 2012-01-19
> **snowpine said:**
> Who do you mean by "you" exactly? Everyone on Ubuntu Forums is just an ordinary guy or gal like you, hanging out and talking about Ubuntu. I am not responsible for Ubuntu so arguing with me will accomplish nothing. ;)

If Ubuntu is not right for your needs, then we are friendly and will help you find the right tool for the job. Maybe you would be happier with a "rolling release" distro like Arch? Or maybe you would like some easy instructions to install the latest Thunderbird in 30 seconds; would that change your opinion of Ubuntu if you knew how easy it was?

(Out of curiosity, when you run Windows Update on an Windows PC, does it automatically update your Thunderbird to the latest version?)

Neither Thunderbird or Firefox are installed by default by Windows.

They are by Ubuntu.

The 1% likes your system. Most do not.

---

### Post by vasa1 on 2012-01-19
> **Tranas said:**
> Neither Thunderbird or Firefox are installed by default by Windows.

They are by Ubuntu.

The 1% likes your system. Most do not.

You're not gaining anything by these posts. As is pointed out, the majority of us come here to help or be helped.

---

### Post by snowpine on 2012-01-19
> **Tranas said:**
> Neither Thunderbird or Firefox are installed by default by Windows.

They are by Ubuntu.

The 1% likes your system. Most do not.

Not sure what you hope to accomplish with this attitude. I am just a guy taking time out of his busy day, volunteering to help you choose the right operating system for your needs. I don't use Ubuntu personally, and based on your posts, I don't think it is the right choice for you either (you seem to have a fundamental misunderstanding of the design philosophy, like saying "this pizza needs more noodles"). 

Since I've already clearly stated my suggestions (learn how to install the applications you want--it's easier than you think!--or switch to a rolling release distro), my work here is done, good luck. :)

---

### Post by spacecheck on 2012-01-19
> **Tranas said:**
> Neither Thunderbird or Firefox are installed by default by Windows.

They are by Ubuntu.

The 1% likes your system. Most do not.
I submit the forums here contain a much greater percentage of users who like the system. In the alternative, I submit there is a much greater percentage of users here, who are unhappy or dis-infatuated with the main non-opensource, semi-monoplist alternative OS.

@snowpine - >  Here is an analogy: Imagine you bought a 2011 model car, now it is 2012.  You take your car to the dealership for an oil change. Do they replace  your engine with the engine from the 2012 model?... Poor analogy. More apt would be an analogy asking whether or not a specific software solution, reprogrammed to resolve an error discovered in the 2011 car's chip/BIOS control, might be installed during the stipulated oil change, perhaps to optimize fuel-efficiency, or realign ESP or ABS, or enhance electronic braking or accelerator controls, or possibly vehicle entrance control systems, to prevent accidents, injury or to improve protection of personal/property security and function.

Such software security updates are no longer unusual, even in vehicles. For personal or non-production computer systems, add-on software requires continual maintenance to protect personal data and system security. This applies no less to T-bird than to FF. Just like FF, T-bird has also moved to an accelerated versioning system, with many of the critical security updates applicable to FF also being applicable to T-bird, a recent example of which may be seen here:

 [http://www.h-online.com/open/news/item/Critical-holes-in-Firefox-Thunderbird-and-SeaMonkey-1399340.html](http://www.h-online.com/open/news/item/Critical-holes-in-Firefox-Thunderbird-and-SeaMonkey-1399340.html)

> (Out of curiosity, when you run Windows Update on an Windows PC, does it  automatically update your Thunderbird to the latest version?)Unlike Windows, Ubuntu selects a series of different. open-source applications to provide a similar functionality as the expensive closed-sourced competition. On a one to one comparison, one would have to admit that Windows does indeed not only update the OS, but also updates or upgrades the Mail and Browser systems included, at least to include security updates, and (currently) takes no steps to hinder the security/version updates/upgrades to 3rd party applications.

> I don't use Ubuntu personally This is a comment seriously belied by your own personal profile description, "Ubuntu addict and loving it". Although the comments made in your [post #7]("http://ubuntuforums.org/showpost.php?p=11618694&postcount=7") are certainly at least partially correct, it should also be recognized that dual systems are often reliant upon a unified data source and profile (T-bird, for example), and these can suddenly experience problems, when an application can be updated and security-patched in one system, yet not in the other, even when such updates are regularly available for both systems.
> 
personally my definition of mickey-mouse is somewhat irrelevant. Either the OP pulls the T-bird 9+ package from "oneiric-proposed" and does his own testing with it first, ultimately deciding whether or not it "borks" the systems in his own environment, before choosing for/against an Oneiric-compatible T-bird roll-out, or he chooses an alternative solution, most of which have been mentioned already.

@Tranas - > Your method is a workaround and does not solve my issue IMHO. My users  are not geek enabled - they need a simple method to update/upgrade. Yes, it is a workaround. These are often necessary, in life and in IT. If your users are not "geek enabled", they should probably not have profiles allowing them to be updating or installing software on their own systems. Users will be users, so it does not reflect poorly upon the user, if s/he happens to install untested, unsafe, harmful or even 'system-borking' software. It does reflect poorly upon the administrator, for not having prevented it.

Have fun!

---

### Post by snowpine on 2012-01-19
> **spacecheck said:**
> This is a comment seriously belied by your own personal profile description, "Ubuntu addict and loving it". 

That should say "Ubuntu **FORUMS** addict and loving it." ;)

I am a little out of the loop, so if you say the policy has changed and Thunderbird 9 is coming down the pipeline, then I stand corrected.

---

### Post by spacecheck on 2012-01-19
> if you say the policy has changed and Thunderbird 9 is coming down the pipeline, then I stand corrected.I neither wrote that, nor do I see how you may have gotten that impression. I wrote that it is currently available in the "Oneiric-proposed" repository (or was, on Dec. 30th).

May the Ubunt be with u!

---

### Post by snowpine on 2012-01-19
> **spacecheck said:**
> I neither wrote that, nor do I see how you may have gotten that impression. I wrote that it is currently available in the "Oneiric-proposed" repository (or was, on Dec. 30th).


Which implies the update is coming soon for all Oneiric users. (Or am I misunderstanding the meaning of "proposed"?)

When I used Ubuntu the policy was to never update browser version, I understand they changed this policy a year or two ago, due to changes in Mozilla releases/support. That's the historical background so you understand where my comments are coming from. :)

---

### Post by spacecheck on 2012-01-19
> Which implies the update is coming soon for all Oneiric users. (Or am I misunderstanding the meaning of "proposed"?)Even based on the definition of "proposed" it could not be validly assumed, that a proposed "update is coming soon for all Oneiric users", but merely that it has been proposed and is available for testing in the 'proposed' repository.

A more logical assumption would be, that if a proposed update should fail testing in the proposed version it would probably NOT be "coming soon", but that IF it passes testing, it MAY be "coming soon".

Fortunately, I have not been disappointed in the past, by installing 'proposed' updates for Mozilla-related items.

May the buntu be with U!

---

### Post by snowpine on 2012-01-19
> **spacecheck said:**
> Even based on the definition of "proposed" it could not be validly assumed, that a proposed "update is coming soon for all Oneiric users", but merely that it has been proposed and is available for testing in the 'proposed' repository.

A more logical assumption would be, that if a proposed update should fail testing in the proposed version it would probably NOT be "coming soon", but that IF it passes testing, it MAY be "coming soon".

Fortunately, I have not been disappointed in the past, by installing 'proposed' updates for Mozilla-related items.

Thanks for the clarification, I have never used Proposed myself. If I understand you correctly then there is no guarantee/timeline if/when TB 9 is coming to 11.10? Therefore my suggestion to the OP to take control of his computer and install the software he needs today, rather than wait for a hypothetical update tomorrow. :)

---

### Post by spacecheck on 2012-01-19
> If I understand you correctly then there is no guarantee/timeline if/when TB 9 is coming to 11.10?There is a guarantee that TB has come to 11.10, because it has already come to at least my machines. I have not (yet) experienced any problem with it.

In [post #15]("http://ubuntuforums.org/showpost.php?p=11619844&postcount=15"), the OP mentioned a specific problem with TB8 on Ubuntu 11.10 being able to properly/functionally use the TB9 profiles on Win systems.

A suggestion to use direct Mozilla versions, or pull daily builds, although valid perspectives, do not reflect any additional integration and/or testing sufficient to make a candidate for the "proposed" repo. In addition, it removes a future ability to pull security and recommended updates for a version that has eventually moved from 'proposed' to 'implemented'.

On the other hand, the OP is a member of the 'community' and has a need he would like fulfilled. The "proposed" repository gives him an opportunity to pull a compatible upgrade version for testing. If it suits his needs, causes no problems and does the job, he can roll out to the systems in question, thus fulfilling the need he has expressed. He can be a valued member of the community by giving feedback on the results of his testing and implementation. As citing in the link about repositories:
> "Pre-released Updates (lucid-proposed)".  The testing area for updates.  This repository is recommended only to those interested in helping to  test updates and provide feedback.  
I think it may safely be assumed, that this policy is not exclusive to "Lucid".

Have fun!

---

### Post by snowpine on 2012-01-19
Well said, spacecheck. :)

---

### Post by spacecheck on 2012-01-19
> **snowpine said:**
> Well said, spacecheck. :) Thank you very much!

spacecheck
(just don't let it bounce!)

---

### Post by lovinglinux on 2012-01-20
Closed for review

---

