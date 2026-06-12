---
title: "Firefox-3.6"
date: 2010-01-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jmmL on 2010-01-22
I can't find any information about when firefox-3.6 will be included in lucid. Does anyone know?

---

### Post by Sslaxx on 2010-01-22
Dunno. Do bear in mind this is a LTS release. Ubuntu hasn't necessarily been consistent in the past with this, sometimes including a prior version, sometimes a beta, in a final release.

I'd hope that 3.6 should be included, myself.

---

### Post by prshah on 2010-01-22
> **jmmL said:**
> any information about when firefox-3.6 will be included in lucid. 

Considering that 3.7(ish) will be released in March, and Lucid in April, I'd guess that lucid will have 3.7.

---

### Post by Merk42 on 2010-01-22
After how they [laughably handled 3.0 - 3.5 in Jaunty](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211) I think they learned their lesson.
It should be [easier to upgrade Firefox in Lucid](https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model), of course, when all this will actually land is unknown

> **prshah said:**
> Considering that 3.7(ish) will be released in March, and Lucid in April, I'd guess that lucid will have 3.7.
[I wouldn't bet on ever seeing 3.7...](http://www.computerworld.com/s/article/9144820/Mozilla_dumps_Firefox_3.7_from_schedule_changes_dev_process)

---

### Post by SilverWave on 2010-01-22
It may take a couple of weeks but you can get it now from the Mozilla Daily Builds PPA

> **SilverWave said:**
> Just tested this on a standard Karmic install   and it still works fine :)
     
     ```
sudo add-apt-repository ppa:ubuntu-mozilla-daily
sudo apt-get update
sudo apt-get install firefox-3.6
```

This works for me :)

Full Details Here: [Install  The Newest Firefox ppa with command "add-apt-repository" (9.10 &  above)]("http://ubuntuforums.org/showthread.php?t=1352580")
> **SilverWave said:**
> _Install the latest: Firefox-3.6 &   Firefox-3.7a1(via UMD). Firefox3.5.7(via UMS)._

A new command in Karmic makes it easy to add a PPA repository and its   key, all at once.

:)

---

### Post by baizon on 2010-01-22
> **SilverWave said:**
> It may take a couple of weeks but you can get it now from the Mozilla Daily Builds PPA



This works for me :)

Full Details Here: [Install  The Newest Firefox ppa with command "add-apt-repository" (9.10 &  above)]("http://ubuntuforums.org/showthread.php?t=1352580")

I don't want to install pre-releases of FF. I hope it will be added soon to the Lucid repository.

---

### Post by kansasnoob on 2010-01-22
I'm using Ubuntuzilla and got it yesterday:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by lovinglinux on 2010-01-22
> **SilverWave said:**
> It may take a couple of weeks but you can get it now from the Mozilla Daily Builds PPA



This works for me :)

Full Details Here: [Install  The Newest Firefox ppa with command "add-apt-repository" (9.10 &  above)]("http://ubuntuforums.org/showthread.php?t=1352580")

You don't have to install firefox-3.6. Adding the PPA and installing updates will replace *firefox-3.5* package with Firefox 3.6. Nevertheless, you can still install it side-by-side as you did.

This behavior is different from when Shiretoko was released, which was always installed side-by-side.

It seems there is an update policy change for Firefox going on and we might start getting major updates in addition to security updates on stable releases. See discussion after post #343 at [http://ubuntuforums.org/showthread.php?t=1193567&page=35](http://ubuntuforums.org/showthread.php?t=1193567&page=35)

---

### Post by Seventh Reign on 2010-01-22
Has anyone read the absurd Firefox 3.6 Computerworld Article by Preston Gralla?

My sides still ache from laughing so hard at what he wrote and the comments following.  I dont know what is worse .. Ignorance and a lack of understanding or blatant lies and slander.

---

### Post by lovinglinux on 2010-01-22
> **Seventh Reign said:**
> Has anyone read the absurd Firefox 3.6 Computerworld Article by Preston Gralla?

My sides still ache from laughing so hard at what he wrote and the comments following.  I dont know what is worse .. Ignorance and a lack of understanding or blatant lies and slander.

Link please...

---

### Post by Merk42 on 2010-01-22
> **lovinglinux said:**
> Link please...

Looked for it myself:
[http://blogs.computerworld.com/15443/talling_firefox_3_6_one_more_reason_linux_isnt_ready_for_the_prime_time_mass_market?page=1](http://blogs.computerworld.com/15443/talling_firefox_3_6_one_more_reason_linux_isnt_ready_for_the_prime_time_mass_market?page=1)

Also, the responses are just as ignorant

"Use the PPA!" 
okay first off, how is a user going to find out that's an option? Plus it's DAILY so they'd get unstable alphas as well

"Wait for it to be in Ubuntu's repositories"
**Will** it be in Ubuntu (Karmic) repositories?

---

### Post by lovinglinux on 2010-01-22
> **Merk42 said:**
> Looked for it myself:
[http://blogs.computerworld.com/15443/talling_firefox_3_6_one_more_reason_linux_isnt_ready_for_the_prime_time_mass_market?page=1](http://blogs.computerworld.com/15443/talling_firefox_3_6_one_more_reason_linux_isnt_ready_for_the_prime_time_mass_market?page=1)

Also, the responses are just as ignorant

"Use the PPA!" 
okay first off, how is a user going to find out that's an option? Plus it's DAILY so they'd get unstable alphas as well

"Wait for it to be in Ubuntu's repositories"
**Will** it be in Ubuntu (Karmic) repositories?


Although I don't agree with the generalization and choice of words, he is kind if right. Software in Ubuntu is much easier to update, when it comes to security patches. But once the user wants the latest versions, he will need to use some "dirty" methods. Unfortunately, this is what happens on every major Firefox release. I don't want to extend the discussion, because there are lots of endless threads discussing the this, but I hope the info about Firefox update policy change in my previous post is correct. I don't care to install form PPA, Ubuntuzilla, Mozilla or whatever, but it is kind of frustrating to see the forum flooded with the same kind of discussions every time Mozilla releases a new major version.

---

### Post by Asraniel on 2010-01-22
i think that article was quite right, software installation is  a problem under ubuntu, if you want anything newer than the current version in the repository or something that is not in the reps.
Now how to solve that problem.. no idea

---

### Post by ronacc on 2010-01-22
just installed 3.7 (minefield) from the PPA and it is noticeably faster than 3.5 .

---

### Post by snowpine on 2010-01-22
> **Asraniel said:**
> i think that article was quite right, software installation is  a problem under ubuntu, if you want anything newer than the current version in the repository or something that is not in the reps.
Now how to solve that problem.. no idea

Use Arch!

:popcorn:

(oh wait, they don't have FF3.6 yet either! :))

---

### Post by andrewabc on 2010-01-22
Well the article does have it's points. Ubuntu doesn't ship an updated version of probably the most used and useful app until newest ubuntu version. Waiting 3-4 months for an updated browser (assuming you upgrade OS), does suck.

I can't benefit from better browser until
A. I update myself (not fun)
B. wait for new OS release (takes time)

Maybe Canonical throw some resources into getting an update out in a couple weeks at least?

---

### Post by snowpine on 2010-01-22
> **andrewabc said:**
> Well the article does have it's points. Ubuntu doesn't ship an updated version of probably the most used and useful app until newest ubuntu version. Waiting 3-4 months for an updated browser (assuming you upgrade OS), does suck.

I can't benefit from better browser until
A. I update myself (not fun)
B. wait for new OS release (takes time)

Maybe Canonical throw some resources into getting an update out in a couple weeks at least?

Ubuntu is not "rolling release." I hope Canonical does what they did for Jaunty (provide an optional firefox-3.5 package for those who want it), but not force the upgrade upon users who thought they were getting a stable release with 18 months of support for FF3.5.

Still curious to know which websites out there work with FF3.6 but not 3.5...

---

### Post by philinux on 2010-01-22
Feel for the LTS users. There still on 3.0.17 and thats even with backports.

---

### Post by andrewabc on 2010-01-22
> **snowpine said:**
> Ubuntu is not "rolling release." I hope Canonical does what they did for Jaunty (provide an optional firefox-3.5 package for those who want it), but not force the upgrade upon users who thought they were getting a stable release with 18 months of support for FF3.5.

Still curious to know which websites out there work with FF3.6 but not 3.5...

I agree with 3.6 in official repository for people to easily install. But last time for 3.0-3.5 in jaunty, they left it called shiretoko (yes I know the reason for name). And took a while to happen as well.

---

### Post by castrojo on 2010-01-22
[https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model](https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model)

---

### Post by lovinglinux on 2010-01-22
For those complaining...read post [#8](http://ubuntuforums.org/showpost.php?p=8707138&postcount=8) or the link posted on the previous post.

---

### Post by snowpine on 2010-01-22
> **whiprush said:**
> [https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model](https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model)

That could be very cool, especially for an LTS release! :KS

---

### Post by xebian on 2010-01-22
The problem is Firefox.  I can't comprehend nor could see any reason why they don't release a 64-bit version.

---

### Post by lovinglinux on 2010-01-22
> **xebian said:**
> The problem is Firefox.  I can't comprehend nor could see any reason why they don't release a 64-bit version.

You can get a 64bit version from *ubuntu-mozilla-daily* ppa or through the nightlies in the Mozilla FTP site. Is not an official release, but it works like a charm.

See the tutorial on my sig for instructions.

---

### Post by Merk42 on 2010-01-22
> **snowpine said:**
> Ubuntu is not "rolling release." I hope Canonical does what they did for Jaunty (provide an optional firefox-3.5 package for those who want it), but not force the upgrade upon users who thought they were getting a stable release with 18 months of support for FF3.5.

Still curious to know which websites out there work with FF3.6 but not 3.5...
Still curious to know why people think 3.6 after 5 betas and 2 RCs would be considered unstable...

> **lovinglinux said:**
> For those complaining...read post [#8](http://ubuntuforums.org/showpost.php?p=8707138&postcount=8) or the link posted on the previous post.
I think you mean [post #4](http://ubuntuforums.org/showpost.php?p=8706692&postcount=4) :P

---

### Post by lovinglinux on 2010-01-22
> **Merk42 said:**
> I think you mean [post #4](http://ubuntuforums.org/showpost.php?p=8706692&postcount=4) :P

Fair enough. I missed that one :)

---

### Post by snowpine on 2010-01-22
> **Merk42 said:**
> Still curious to know why people think 3.6 after 5 betas and 2 RCs would be considered unstable...

I am not saying Firefox is "unstable." I am saying that a so-called "stable" Linux release (as distinguished from "rolling release") does not give its users major upgrades through the normal update process.

Looks like Canonical may be reconsidering what constitutes a "major" vs. "minor" Firefox upgrade starting with Lucid.

---

### Post by NCLI on 2010-01-22
> **snowpine said:**
> I am not saying Firefox is "unstable." I am saying that a so-called "stable" Linux release (as distinguished from "rolling release") does not give its users major upgrades through the normal update process.

Looks like Canonical may be reconsidering what constitutes a "major" vs. "minor" Firefox upgrade starting with Lucid.

Not really, I think it's just that Mozilla will be drastically altering the way they do new versions of Firefox, and Canonical follows suit by modifying its own policy.

---

### Post by lovinglinux on 2010-01-22
> **NCLI said:**
> Not really, I think it's just that Mozilla will be drastically altering the way they do new versions of Firefox, and Canonical follows suit by modifying its own policy.

I also believe that is what is going on. As far as I could understand, it seems Mozilla is [dropping support for Firefox 3.5 six months from now](http://ubuntuforums.org/showpost.php?p=8707213&postcount=347). I don't know if that policy was already in place before the release of 3.6, but it looks to me that this would force Canonical to backport Firefox 3.6 into Karmic as well.

---

### Post by castrojo on 2010-01-22
Did you read the link I posted? Yes, it will come as an update to Karmic.

---

### Post by lovinglinux on 2010-01-22
> **whiprush said:**
> Did you read the link I posted? Yes, it will come as an update to Karmic.

Not really :) I just read that the subject is the same as the other link posted in my tutorial and that you say "**easier to upgrade Firefox in Lucid**". Anyway, as I said on the other thread, *ubuntu-mozilla-daily* is already upgrading *firefox-3.5* package to 3.6 instead that installing a separate *firefox-3.6* package. So I guess they are already complying with the new rules.

---

### Post by ccw on 2010-01-22
> **whiprush said:**
> Did you read the link I posted? Yes, it will come as an update to Karmic.

Do you know of any time frames set on these? The blueprint doesn't seem to mention any.

---

### Post by Merk42 on 2010-01-22
> **whiprush said:**
> Did you read the link I posted? Yes, it will come as an update to Karmic.

You mean the same link to the blueprints that both Lovinglinux and myself posted earlier?

work items (not bound by lucid release cycle):
TODO TODO TODO TODO
sounds promising...

...and the goal is Lucid's release? So what information is there that this'll even take affect with Hardy-Karmic before Lucid's release? (yea what CCW said)

---

### Post by castrojo on 2010-01-22
> **ccw said:**
> Do you know of any time frames set on these? The blueprint doesn't seem to mention any.

They're working on it right now.

---

### Post by exploder on 2010-01-22
Thanks whiprush!

---

### Post by kansasnoob on 2010-01-22
> **lovinglinux said:**
> Although I don't agree with the generalization and choice of words, he is kind if right. Software in Ubuntu is much easier to update, when it comes to security patches. But once the user wants the latest versions, he will need to use some "dirty" methods. Unfortunately, this is what happens on every major Firefox release. I don't want to extend the discussion, because there are lots of endless threads discussing the this, but I hope the info about Firefox update policy change in my previous post is correct. I don't care to install form PPA, Ubuntuzilla, Mozilla or whatever, but it is kind of frustrating to see the forum flooded with the same kind of discussions every time Mozilla releases a new major version.

Not to be argumentative but there's a certain degree of absurdity to that line of thought. Basically it boils down to this:

> I don't care to install form PPA, Ubuntuzilla, Mozilla or whatever

Are you aware of any OS that never requires you to download anything? MAC is no doubt the most "self-sustaining" but a 5 year old MAC is still a 5 year old MAC with updates.

Certainly with Windows there are continual updates to both the OS and all of the "anti-this-n-that" progs, but if you want an update/upgrade to a specific app it takes some effort.

Recent changes to Ubuntuzilla make it nearly effortless with i386/32 bit, 64 bit not so much, and Ubuntu has gotten better about pushing out updates earlier.

But if you really want safe, up to date Firefox - Thunderbird - Seamonkey look to Ubuntuzilla:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by Merk42 on 2010-01-22
> **kansasnoob said:**
> Certainly with Windows there are continual updates to both the OS and all of the "anti-this-n-that" progs, but if you want an update/upgrade to a specific app it takes some effort.

No it really doesn't.
By default Firefox in Windows (maybe OS X) goes "oh hi, there's 3.6 out, click me and I'll update you"
By default Firefox in Ubuntu does absolutely nothing! 
So it requires more effort in Ubuntu*


*the yet to be implemented launchpad feature not-withstanding



As this sub-forum is about Lucid, I did find it odd that Lucid had 3.5 and not the beta of 3.6. That is, unless the upgrade from 3.5 to 3.6 in Lucid will be a testbed for the launchpad blueprint for Hardy-Karmic.

---

### Post by kansasnoob on 2010-01-22
> **Merk42 said:**
> No it really doesn't.
By default Firefox in Windows (maybe OS X) goes "oh hi, there's 3.6 out, click me and I'll update you"
By default Firefox in Ubuntu does absolutely nothing! 
So it requires more effort in Ubuntu*


*the yet to be implemented launchpad feature not-withstanding



As this sub-forum is about Lucid, I did find it odd that Lucid had 3.5 and not the beta of 3.6. That is, unless the upgrade from 3.5 to 3.6 in Lucid will be a testbed for the launchpad blueprint for Hardy-Karmic.

It's nice how you quoted only the part of that you chose to. I went on to say:

> if you really want safe, up to date Firefox - Thunderbird - Seamonkey look to Ubuntuzilla

But, if you prefer the Windows way no one is holding you back :)

---

### Post by Merk42 on 2010-01-22
> **kansasnoob said:**
> It's nice how you quoted only the part of that you chose to. I went on to say:
Because I was comparing defaults in both cases.
and even if you want to throw the "well by default Windows doesn't come with Firefox at all" card, Windows by default updates to the latest major release of its default browser, Internet Explorer.


> **kansasnoob said:**
> But, if you prefer the Windows way no one is holding you back :)
Considering the "Windows way" is to get it automatically or force it by going to Help > Check for updates, I'd say that Ubuntu is holding me back from doing it that way*

*again this seems to be getting 'fixed' in [that blueprint for Lucid](https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model)

---

### Post by lovinglinux on 2010-01-22
> **kansasnoob said:**
> Not to be argumentative but there's a certain degree of absurdity to that line of thought. Basically it boils down to this:

Are you aware of any OS that never requires you to download anything? MAC is no doubt the most "self-sustaining" but a 5 year old MAC is still a 5 year old MAC with updates.

Certainly with Windows there are continual updates to both the OS and all of the "anti-this-n-that" progs, but if you want an update/upgrade to a specific app it takes some effort.

Recent changes to Ubuntuzilla make it nearly effortless with i386/32 bit, 64 bit not so much, and Ubuntu has gotten better about pushing out updates earlier.

But if you really want safe, up to date Firefox - Thunderbird - Seamonkey look to Ubuntuzilla:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

I think you misunderstood me. I have been running Firefox 3.6 since beta, I have no problems whatsoever with any of the alternative installation methods. I have already used all of them at some point and for me, they are all very easy. They are definitively not an issue. In fact, I have an entire section of my [Firefox tutorial](http://ubuntuforums.org/showthread.php?t=1193567) dedicated to installation methods. Indeed Ubuntuzilla is one the best solutions for 32bit users, specially since they switched from a script to a repository. 

What I was saying is that the author of that article was right, in the sense that he, like many newcomers and others users not very tech-savvy, finds difficult to update Firefox when a new major release comes out. Because of that, the forums are flooded with complains and endless discussions. Take a look for example t[his thread](http://ubuntuforums.org/showthread.php?t=1387172&page=7). It is already becoming such a boring discussion why people don't like the way Ubuntu deals with Firefox updates. Not to mention the complains about the name of the installed browser. For now, nobody complained about Namoroka, but search the forums for Shiretoko and you will see.

Anyway, to put an end on this discussion, I just have to say that this is not going to happen anymore, because Mozilla has changed the way they deal with major updates and [Canonical is adapting to it](http://ubuntuforums.org/showpost.php?p=8706948&postcount=345). So is very likely that we will see Firefox 3.6 being backported into Karmic. Mozilla is going to [drop support for Firefox 3.5 in six months](http://ubuntuforums.org/showpost.php?p=8707213&postcount=347), so there is not much Canonical can do about it.

I'm currently using Firefox 3.6 64bit form *ubuntu-mozilla-daily* and they are already complying with the new rules. Instead of installing firefox-3.6 package side-by-side with the official version (like Shiretoko did), when you use the PPA it actually upgrades the *firefox-3.5* package.

---

### Post by zekopeko on 2010-01-22
Let me get this straight. Mozilla will start rapidly updating Firefox, similar to a rolling distro. Support for major release will last for 6 months after the next major release. We are basically getting a fully bundled Firefox that uses it's own dependency version not the system wide ones. This change will be applied to Hardy and later releases.

Did I miss something?

---

### Post by lovinglinux on 2010-01-22
> **zekopeko said:**
> Let me get this straight. Mozilla will start rapidly updating Firefox, similar to a rolling distro. Support for major release will last for 6 months after the next major release. We are basically getting a fully bundled Firefox that uses it's own dependency version not the system wide ones. This change will be applied to Hardy and later releases.

Did I miss something?

I guess you got it right. I don't understand some stuff on that blueprint, but the quote below is very clear.

> Mozilla moved to a monthly security update cycle early in 2009; next step planned is to stop doing stable release branches for any distro-relevant amount of time. For instance, they consider to release firefox 3.6 as a minor update to firefox 3.5 and want to a 3-4 month cycle for such minor-major version upgrades. Also it happens more frequently now that they bump reqtuirements on system libs like cairo and sqlite3 in minor version upgrades.
This is in line with what is planned by chromium and it's unfeasible to try to do our own stable release branch maintenance as this would require far more resources than we can get at any point in the future.
Instead we should prepare for what is coming and ensure that we can follow major-minor version upgrades in a timely fashion.
Main topics addressed by this blueprint are:

1. how to prepare the firefox package so we can follow the major-minor version upgrade path.
2. how to deal with xulrunner reverse-dependencies 

I'm just not sure about being fully bundled with it's own dependencies.

---

### Post by zekopeko on 2010-01-22
> **lovinglinux said:**
> I guess you got it right. I don't understand some stuff on that blueprint, but the quote below is very clear.

I'm just not sure about being fully bundled with it's own dependencies.

They mention version bumps for cairo and sqlite. Various programs in the default install use those two (not sure about sqlite but GTK+ uses cairo to draw itself). So the only way to avoid upgrading them (and potentially breaking A LOT of stuff) is to bundle the newer versions with FF. I think they will simply ship FF from Mozilla with the Ubufox extension. They also mention activating the built in upgrade system.

---

### Post by lovinglinux on 2010-01-22
> **zekopeko said:**
> They mention version bumps for cairo and sqlite. Various programs in the default install use those two (not sure about sqlite but GTK+ uses cairo to draw itself). So the only way to avoid upgrading them (and potentially breaking A LOT of stuff) is to bundle the newer versions with FF. I think they will simply ship FF from Mozilla with the Ubufox extension. They also mention activating the built in upgrade system.

Yep, it makes sense.

---

### Post by NCLI on 2010-01-23
What's all the stuff about Webkit I see in the spec?

---

### Post by 23meg on 2010-01-23
> **Merk42 said:**
> No it really doesn't.
By default Firefox in Windows (maybe OS X) goes "oh hi, there's 3.6 out, click me and I'll update you"
By default Firefox in Ubuntu does absolutely nothing! 
So it requires more effort in Ubuntu*


Nice comparison. I'm reminded of how Internet Explorer behaves in Windows (if Microsoft is pushing people to upgrade) versus how it behaves in Ubuntu running under WINE.

---

### Post by 23meg on 2010-01-23
[QUOTE=Merk42]Windows by default updates to the latest major release of its default browser, Internet Explorer.[/QUOTE]

Not necessarily; that happens only in cases where Microsoft deems it suitable to push people to upgrade through Windows Update, as opposed to simply making the upgrade available online. Sounds familiar?

---

### Post by Merk42 on 2010-01-23
> **23meg said:**
> Not necessarily; that happens only in cases where Microsoft deems it suitable to push people to upgrade through Windows Update, as opposed to simply making the upgrade available online. Sounds familiar?

Actually I just did a fresh install of XP and was immediately pushed via Windows Update from IE6 to IE8
Also I could opt in/out by going to Windows Update manually.

In either case it's not like I had to upgrade to Vista (or even the latest service pack) to get IE7 or IE8.

Microsoft has pushed out updates the IE7 and IE8 after they came out.  Even before they are pushed out via automatic updates, one can manually go to Windows Update and get it sooner. The only reason there are so many people running IE6, is corporations opting out of the upgrade due to outdated proprietary Intranet software.

---

### Post by exploder on 2010-01-23
Firefox 3.6 is going to make it into Lucid and the developers are working on it. I don;t see why there is so much discussion about this. :) Just the fact that the developers are even looking at ways to upgrade Firefox for the future is encouraging in my opinion. My Wife has Firefox 3.6 on her Windows 7 machine and in all honesty I don't see any huge difference between it and 3.5. I will just wait and see what the developers come up with.

---

### Post by 23meg on 2010-01-23
> **Merk42 said:**
> Actually I just did a fresh install of XP and was immediately pushed via Windows Update from IE6 to IE8

Microsoft made that decision after eight years of deliberately **not** pushing people to upgrade IE6, due to various reasons, not the least important of which was to give longer comfort to large corporate deployments. Hence my saying "not necessarily".

[QUOTE=Merk42]In either case it's not like I had to upgrade to Vista (or even the latest service pack) to get IE7 or IE8.[/QUOTE]

You could have had to, had Microsoft seen fit. Both IE and Windows are proprietary products entirely controlled by Microsoft, so the direct comparison to Ubuntu and Firefox misses some points.

---

### Post by 23meg on 2010-01-23
> **exploder said:**
> I don;t see why there is so much discussion about this. :) 

1) People like debating.

2) It's Merk42's favourite topic.

---

### Post by Merk42 on 2010-01-23
> **23meg said:**
> Microsoft made that decision after eight years of deliberately **not** pushing people to upgrade IE6, due to various reasons, not the least important of which was to give longer comfort to large corporate deployments. Hence my saying "not necessarily".

What are you talking about? That's never how it went.

[list=1][*]Microsoft releases IE7/IE8
[*]IT departments could download and install a separate tool to make IE7/IE8 never show up as an automatic update
[*]Over the next few weeks IE7/IE8 trickled into a few user's Automatic Updates, until after some time it had eventually trickled into everyone's
[*]If a user didn't want to wait for IE7/IE8 to go to Automatic Updates, they could manually go to Windows/Microsoft Update and get IE7/IE8 that way.[/list]
I'm sure you don't like people spreading misinformation about Ubuntu, please don't spread misinformation about Windows.

> **23meg said:**
> 1) People like debating.

2) It's Merk42's favourite topic.

Really? More so than "here's the awful GNOME Shell" or "hey look no new theme again?" :P

Seriously though I'm very happy with what's going on with 3.6 with that blueprint. I was even the first to point it out.

I was just commenting on the validity of the points in that ComputerWorld article some people had a problem with.

---

### Post by exploder on 2010-01-23
> Really? More so than "here's the awful GNOME Shell" or "hey look no new theme again?"

Seriously though I'm very happy with what's going on with 3.6 with that blueprint. I was even the first to point it out.

I was just commenting on the validity of the points in that ComputerWorld article some people had a problem with.

You and I had a pretty good debate a while back. :D I did come away with a different point of view on a few things. I also agree that what is in the blueprint looks good and makes a lot of sense, it would be a very welcome improvement.

Take care Merk42.

---

### Post by 23meg on 2010-01-23
> **Merk42 said:**
> What are you talking about?

My point, as my first post sums up, is that Microsoft decides whether or not to push people to upgrade to a new IE version at each IE release, and per each supported Windows version at the time. It's not guaranteed that every version of IE will be automatically upgraded to the latest available on every Windows version at any given time.

> **Merk42 said:**
> Seriously though I'm very happy with what's going on with 3.6 with that blueprint. I was even the first to point it out.

I was just commenting on the validity of the points in that ComputerWorld article some people had a problem with.

I know; It was just a passing jest. But don't tell me it's not at least *among* your favourite topics :)

---

### Post by lovinglinux on 2010-01-23
> **exploder said:**
> I also agree that what is in the blueprint looks good and makes a lot of sense, it would be a very welcome improvement.

Since yesterday, you [can't install Firefox 3.6 side-by-side with 3.5 using *ubuntu-mozilla-daily* ppa](http://ubuntuforums.org/showthread.php?t=1352580&page=5). You get an update to Firefox 3.5. So new policy is really in motion.

---

### Post by exploder on 2010-01-23
> Since yesterday, you can't install Firefox 3.6 side-by-side with 3.5 using ubuntu-mozilla-daily ppa. You get an update to Firefox 3.5. So new policy is really in motion.

Thanks! Now this is good information , sounds like thing are heading in the right direction.

---

### Post by lovinglinux on 2010-01-23
> **zekopeko said:**
> Let me get this straight. Mozilla will start rapidly updating Firefox, similar to a rolling distro. Support for major release will last for 6 months after the next major release. We are basically getting a fully bundled Firefox that uses it's own dependency version not the system wide ones. This change will be applied to Hardy and later releases.

Did I miss something?

You was right about Firefox being bundle with dependencies. Firefox does not depend on xulrunner anymore. See discussion after post #43 at [http://ubuntuforums.org/showthread.php?t=1352580&page=5](http://ubuntuforums.org/showthread.php?t=1352580&page=5)

I'm already running it without xulrunner.

---

### Post by exploder on 2010-01-23
> You was right about Firefox being bundle with dependencies. Firefox does not depend on xulrunner anymore. See discussion after post #43 at [http://ubuntuforums.org/showthread.php?t=1352580&page=5](http://ubuntuforums.org/showthread.php?t=1352580&page=5)

I'm already running it without xulrunner. 

Thanks for the information, this is really sounding good!

---

### Post by Merk42 on 2010-01-23
I'm a little confused with the verbiage in the blueprint.
> ubuntu releases will be updated to the next still supported firefox branch once the current firefox branch of that ubuntu release goes EOL upstream

So does that mean that Ubuntu won't update firefox until the installed version is EOL?
Meaning for Karmic, it won't be updated to 3.6 until 3.5 is EOL?

---

### Post by exploder on 2010-01-23
> So does that mean that Ubuntu won't update firefox until the installed version is EOL?
Meaning for Karmic, it won't be updated to 3.6 until 3.5 is EOL?

I think this is the case. I had to read it a couple of times too to be certain I understood this correctly.

---

### Post by Merk42 on 2010-01-23
> **exploder said:**
> I think this is the case. I had to read it a couple of times too to be certain I understood this correctly.

Well if that's the case, and someone correct me if I'm wrong...

I don't think in that example Karmic would get 3.6, as I'm guessing Firefox would be well beyond 3.6 by the time 3.5 were EOL.

---

### Post by exploder on 2010-01-23
> I don't think in that example Karmic would get 3.6, as I'm guessing Firefox would be well beyond 3.6 by the time 3.5 were EOL.

You might be right. The good side of this is at least there is a chance of Firefox being updated where previously there was no chance. You never know, if things work out well they might change things further and update Firefox to stable new releases as a regular practice. Things are at least going in the right direction. :D

---

### Post by Merk42 on 2010-01-23
> **exploder said:**
> You might be right. The good side of this is at least there is a chance of Firefox being updated where previously there was no chance. You never know, if things work out well they might change things further and update Firefox to stable new releases as a regular practice. Things are at least going in the right direction. :D

Yeah, not complaining or anything, just want some clarification about that part I quoted

---

### Post by SilverWave on 2010-01-23
> **SilverWave said:**
> It may take a couple of weeks but you can get it now from the Mozilla Daily Builds PPA

This works for me :)

Full Details Here: [Install  The Newest Firefox ppa with command "add-apt-repository" (9.10 &  above)]("http://ubuntuforums.org/showthread.php?t=1352580")

Update:

> **SilverWave said:**
> [COLOR=RoyalBlue]Note that the way  Firefox is being built and maintained in Ubuntu is changing.[/COLOR][COLOR=Blue]

[/COLOR]As an example, they are quite far along with reducing    dependencies.
Unlike a few days ago, installing firefox-3.6 now does   not install  xulrunner-1.9.2.
See the notes section below for full details.

**Installing Firefox-3.6** via the ubuntu-mozilla-daily PPA
You now can't run firefox-3.6 side-by-side with 3.5 as  you could up to a   couple of days ago.
Rather you are upgrading your existing Firefox-3.5 to the    Firefox-3.6.1  package.
The old "sudo apt-get install firefox-3.6" command will no longer work.

**New Firefox 3.6 Installation Instructions** (Karmic)
     ```

sudo add-apt-repository ppa:ubuntu-mozilla-daily

```  **Now install Firefox as below** (or via the Synaptic  Package  Manager).
     ```

sudo apt-get update
sudo apt-get install firefox
```(Alternatively "sudo apt-get install  firefox-3.5" works as well).

Checkout post #[43]("http://ubuntuforums.org/showthread.php?p=8708092#post8708092") for the latest news.
________________________________________________

---

### Post by exploder on 2010-01-23
As tempting as it might be to install Firefox 3.6 right now I think it is better to wait for this to enter the Lucid repos and stick to the development cycle. I can't really report any bugs with Firefox if I bypass the system.

The Developers are doing a good job handling this release and I will wait and trust their judgement on how this update is addressed. It is best to exercise patience and wait for an official update.

---

### Post by jppr on 2010-01-24
short and simple question ... when firefox 3.6 is updated in repos? :confused: tomorrow? next week? next month? next summer, next christmas, next year?

---

### Post by portis on 2010-01-24
Looks like firefox 3.6 is entering the repo.
It's waiting in the queue.
chromium-browser as well.

[https://launchpad.net/ubuntu/lucid/+queue](https://launchpad.net/ubuntu/lucid/+queue)

---

### Post by baizon on 2010-01-24
> **portis said:**
> Looks like firefox 3.6 is entering the repo.
It's waiting in the queue.
chromium-browser as well.

[https://launchpad.net/ubuntu/lucid/+queue](https://launchpad.net/ubuntu/lucid/+queue)

Nice, thanks for the info :grin:

---

### Post by exploder on 2010-01-24
Thanks portis! I bookmarked the queue for future reference.

---

### Post by jppr on 2010-01-25
[https://launchpad.net/ubuntu/lucid/+source/firefox/3.6+nobinonly-0ubuntu1](https://launchpad.net/ubuntu/lucid/+source/firefox/3.6+nobinonly-0ubuntu1)

---

### Post by ccw on 2010-01-25
> **jppr said:**
> [https://launchpad.net/ubuntu/lucid/+source/firefox/3.6+nobinonly-0ubuntu1](https://launchpad.net/ubuntu/lucid/+source/firefox/3.6+nobinonly-0ubuntu1)

That means it should hit the lucid repos shortly.

---

### Post by praveenmarkandu on 2010-01-25
> **Seventh Reign said:**
> Has anyone read the absurd Firefox 3.6 Computerworld Article by Preston Gralla?

My sides still ache from laughing so hard at what he wrote and the comments following.  I dont know what is worse .. Ignorance and a lack of understanding or blatant lies and slander.

what a noob! seriously. i mean if one of my friends or family had trouble un-tar-ing a file, i would understand. this guy write a tech column. what a disgrace.

---

### Post by zika on 2010-01-25
> **praveenmarkandu said:**
> what a noob! seriously. i mean if one of my friends or family had trouble un-tar-ing a file, i would understand. this guy write a tech column. what a disgrace.Just an illustration who writes about SW and HW on big net and that everybody is an "expert". Hilarious!

---

### Post by LKjell on 2010-01-25
> **praveenmarkandu said:**
> what a noob! seriously. i mean if one of my friends or family had trouble un-tar-ing a file, i would understand. this guy write a tech column. what a disgrace.

Got a link?

---

### Post by zika on 2010-01-25
> **LKjell said:**
> Got a link?[...](http://blogs.computerworld.com/15443/talling_firefox_3_6_one_more_reason_linux_isnt_ready_for_the_prime_time_mass_market)

---

### Post by LKjell on 2010-01-25
The computer tech guy do have a point. Remember that this issue was discussed when we had 3.0 to 3.5 transition.

---

### Post by baizon on 2010-01-25
> **lkjell said:**
> the computer tech guy do have a point. Remember that this issue was discussed when we had 3.0 to 3.5 transition.

+1

---

### Post by tad1073 on 2010-01-25
When is firefox going to hit the repo's?

I don't want to use the daily ppa, fonts with those builds look awful.

---

### Post by phillw on 2010-01-25
At a guess ... it's getting closer, unless they're going to make us wait a while longer ;-) --> [https://launchpad.net/ubuntu/lucid/+queue?queue_state=0&queue_text=firefox](https://launchpad.net/ubuntu/lucid/+queue?queue_state=0&queue_text=firefox)

Regards,

Phill.

---

### Post by kj74 on 2010-01-25
> **tad1073 said:**
> When is firefox going to hit the repo's?

I don't want to use the daily ppa, fonts with those builds look awful.
And they are going to look afwul with the archive build...Exactly same as the ppa version.

---

### Post by blur xc on 2010-01-25
I didn't check exactly what version it is, but my shiretoko (in 9.04) recently upgraded itself to namaroka (sp?).  The only reason I even noticed is because the quick launch icon on the panel quit working, and a couple of firefox add-ons also quit.  A day or two later, updates for them came through and all has been good since.

BM

edit- I'm reasonably certain this came from the official ubuntu repos, as I don't ever recall adding a Mozilla PPA.

---

### Post by seeker5528 on 2010-01-25
> **Merk42 said:**
> By default Firefox in Windows (maybe OS X) goes "oh hi, there's 3.6 out, click me and I'll update you"
By default Firefox in Ubuntu does absolutely nothing! 

If you get the packaged-for-your-distribution (.deb) version of Firefox, you don't want Firefox looking for updates, the same way you don't want Firefox to look for updates for packaged-for-your-distribution extensions.

If stuff that is known to the package management system is replaced by stuff that is not known, then you can have problems later on if the package manager runs into situations where it failed to remove something because it didn't know about it or expects something to be there that isn't, or other things that rely on that software may fail because of changed ABI or behaviour.

If you get Firefox from Mozilla.com and install it then it looks for updates for it's self. 

Typically if you get Firefox extensions off the internet either through normal mozilla.com channels for from a third party site as an .xpi package, Firefox will look for updates to that plugin.

Later, Seeker

---

### Post by Merk42 on 2010-01-25
You quoted something I said 5 pages ago, and thought everyone knew what the issue was.

My, and the person who wrote the article's point was that neither Firefox NOR Ubuntu look for an update of 3.5 -> 3.6.  I know the policy and all that, but just saying what is the expected behavior.

Thankfully Ubuntu did admit to the policy being an issue in this case, and with Firefox 3.6 now in Lucid we are [one step closer to that policy changing](https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model).

---

### Post by jppr on 2010-01-26
Just updated ff 3.6 and works fine = )

---

### Post by dino99 on 2010-01-26
what is that dark browny icon on top ?

can't we have a more sexiest design instead of that big s***  :o

---

### Post by exploder on 2010-01-26
> what is that dark browny icon on top ?

can't we have a more sexiest design instead of that big s*** 

You just need to reboot.

---

### Post by | MM | on 2010-01-26
Firefox should have a stable release ppa included in the default repo list ... or something.

---

### Post by cecilpierce on 2010-01-26
I see 3.6 fixed the 'hover over a thread' time so it don't disappear after 5 seconds, that's been a pain in the neck for me.

---

### Post by philinux on 2010-01-26
> **cecilpierce said:**
> I see 3.6 fixed the 'hover over a thread' time so it don't disappear after 5 seconds, that's been a pain in the neck for me.

I Dont get those tooltips. Cant remember disabling them either.

---

### Post by nanotube on 2010-01-26
> **cecilpierce said:**
> I see 3.6 fixed the 'hover over a thread' time so it don't disappear after 5 seconds, that's been a pain in the neck for me.

yea the tooltips now display for as long as you hover the mouse. works great for the image title tags on [http://xkcd.com](http://xkcd.com) too :)

---

### Post by blur xc on 2010-01-26
I'm really confused, please help me out here.  I just checked the repos for 9.04 (aptitude search firefox) and it came up w/ 3.0, 3.5, 3.6, and 3.7.  As a matter of fact, I'm posting this from 3.7 Minefield.

Why wouldn't it be available for Lucid if I already have it for Jaunty?

BM

---

### Post by Merk42 on 2010-01-26
> **blur xc said:**
> I'm really confused, please help me out here.  I just checked the repos for 9.04 (aptitude search firefox) and it came up w/ 3.0, 3.5, 3.6, and 3.7.  As a matter of fact, I'm posting this from 3.7 Minefield.

Why wouldn't it be available for Lucid if I already have it for Jaunty?

BM

For one thing, you must have additional repos to have all that available.
Another thing, is that with the default repos, 3.6 **is now** in Lucid.

---

### Post by altonbr on 2010-01-26
> **Merk42 said:**
> For one thing, you must have additional repos to have all that available.
Another thing, is that with the default repos, 3.6 **is now** in Lucid.

Just to confirm his findings: [https://launchpad.net/ubuntu/lucid/+source/firefox/3.6+nobinonly-0ubuntu1](https://launchpad.net/ubuntu/lucid/+source/firefox/3.6+nobinonly-0ubuntu1)

---

### Post by ElSlunko on 2010-01-26
> **| MM | said:**
> Firefox should have a stable release ppa included in the default repo list ... or something.

ppa:mozillateam/firefox-stable

---

### Post by seeker5528 on 2010-01-27
> **Merk42 said:**
> My, and the person who wrote the article's point was that neither Firefox NOR Ubuntu look for an update of 3.5 -> 3.6.  I know the policy and all that, but just saying what is the expected behavior.

Expecting your managed software to treat updates in the same way as unmanaged versions on another platform is not correct.

You should expect a stable managed environment to only have security updates. Not sure how strictly that is adhered to with Ubuntu, but the 3.5 to 3.6 update is a little more than just a security update.

If security issues require going to a newer version as opposed to backporting the fix, then security trumps stability, but to the extent possible should be minimally disruptive to maintain as much stability as possible. This is why Debian has the volatile repository with a very small number of packages. 

If you have backports enabled, then you might have an expectation that enough people want an up to date Firefox for a version to be supplied that way not too long after an upstream release. Since I have never stuck with a stable release for an extended period of time, don't know what the policy is there either.

Windows and Mac software are not provided in a managed way so comparing the free-for-all case to the managed case is wrong.

The point about Firefox being harder to install is semi-valid. The same page where the download is available has what I consider to be pretty plainly written/easy to follow instructions, but I deal with enough people who have trouble downloading and running the installer in Windows that I don't put up too much of an argument about that.

Once you have installed Firefox from mozilla.com as you would on Windows or Mac and are comparing apples to apples, it behaves in the expected way.

Later, Seeker

---

### Post by exploder on 2010-01-27
seeker5528, you make some very valid points. I never really thought about how the stability of the system as a whole could be influence by a major upgrade to Firefox. There are things that a major upgrade could potentially effect.

---

### Post by SilverWave on 2010-01-29
Anyone having trouble with ff3.6 fonts... may want to have a look at this setting...

[http://kb.mozillazine.org/Browser.di..._min_font_size]("http://kb.mozillazine.org/Browser.display.auto_quality_min_font_size")

As I wanted text to be **optimized for display quality** I set
     ```
browser.display.auto_quality_min_font_size = 0 
```
Worked for me.

---

### Post by proxess on 2010-01-29
Search deeply in Launchpad, the Firefox 3.6 builds for Lucid are there. I've got them with the a recent xulrunner build, they work fine.

---

### Post by jerrylamos on 2010-01-29
Firefox 3.6 and kernel 2.6.32-12 hang after playing one video on BBC news.  That's using Flash.  

The video runs thru once but Firefox is hung, "Force Quit" time.

Anyone know of a bug report?

Jerry

---

