---
title: "do-release-upgrade &quot;No new release found&quot;"
date: 2023-10-15
forum: Installation &amp; Upgrades
---

### Post by palteater on 2023-10-15
Every new release I get this for many days after the date.

I live in Sweden, is there some delayed release schedule for Europe or something? Even when I set it to download from "Main server"?

If I google for "do-release-upgrade" I get loads of other people having problems with their upgrades, so clearly it does work. And no - I am not restricting to LTS.

I usually end up doing a clean install, since the ISO is available long before the do-release-upgrade works.

---

### Post by guiverc on 2023-10-15
You haven't specifically mentioned what release you're asking about, but I'll assume it's Ubuntu 23.10 which hasn't finished it's release yet.

If it is, I wrote an answer here earlier today; so I'll mostly refer/paste that - [https://askubuntu.com/questions/1489169/cant-upgrade-from-ubuntu-23-04-to-23-10/1489215#1489215](https://askubuntu.com/questions/1489169/cant-upgrade-from-ubuntu-23-04-to-23-10/1489215#1489215)

----

[LEFT][COLOR=#232629][FONT=-apple-system]The release of Ubuntu 23.10 has not actually completed.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]You can refer to this notice for clues

[/FONT][/COLOR]

[COLOR=#232629][FONT=-apple-system][URL="https://discourse.ubuntu.com/t/announcement-ubuntu-desktop-23-10-release-image-is-being-updated-to-resolve-a-malicious-translation-incident/39365"]https://discourse.ubuntu.com/t/announcement-ubuntu-desktop-23-10-release-image-is-being-updated-to-resolve-a-malicious-translation-incident/39365

[/URL][/FONT][/COLOR]

[COLOR=#232629][FONT=-apple-system]The respins of ISOs were done, and are currently in QA (*Quality Assurance*) testing, the status you can view by looking at

[/FONT][/COLOR]

[COLOR=#232629][FONT=-apple-system][URL="https://iso.qa.ubuntu.com/qatracker/milestones/449/builds"]https://iso.qa.ubuntu.com/qatracker/milestones/449/builds

[/URL][/FONT][/COLOR]

[COLOR=#232629][FONT=-apple-system]Currently the respun ISOs are not marked "(ready)" you'll note.

[/FONT][/COLOR]

[COLOR=#232629][FONT=-apple-system]After the ISOs are released, and the release cycle of Ubuntu 23.10 completes; the Ubuntu Release team will explore the option of opening the *upgrade* cycle

[/FONT][/COLOR]

[COLOR=#232629][FONT=-apple-system]The [Ubuntu release upgrader tools]("https://launchpad.net/ubuntu-release-upgrader") check this file for status of upgrade

[/FONT][/COLOR][/LEFT]

[LIST]
[*][https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release) 
[/LIST]
[LEFT][COLOR=#232629][FONT=-apple-system]
which is simple text (*thus easily read*) where you'll note no Ubuntu 23.10 currently lists; that is why the upgrade process is not seen.

[/FONT][/COLOR]

[COLOR=#232629][FONT=-apple-system]You can force *release-upgrade* via use of -d as per instructions provided on Ubuntu 23.10 release notes & announcements, ie. read this link

[/FONT][/COLOR]

[COLOR=#232629][FONT=-apple-system][URL="https://help.ubuntu.com/community/ManticUpgrades"]https://help.ubuntu.com/community/ManticUpgrades

[/URL][/FONT][/COLOR]

[COLOR=#232629][FONT=-apple-system]The -d works as it will force use of the following file, where *mantic* or 23.10 is seen

[/FONT][/COLOR]
[/LEFT]

[LIST]
[*][https://changelogs.ubuntu.com/meta-release-development](https://changelogs.ubuntu.com/meta-release-development) 
[/LIST]
[LEFT][COLOR=#232629][FONT=-apple-system]
For best results; I suggest waiting though. I've seen 9+ emails hitting my inbox on the weekend representing work being performed on the *release-upgrade* bugs, the upgrade path will be open when the current work is completed.

[/FONT][/COLOR]

[COLOR=#232629][FONT=-apple-system]Ubuntu 23.10 currently hasn't fully released; but the release is the initial step for new installs. After release completes, the *Ubuntu Release team* start evaluating the *release-upgrade* steps, opening the *taps* when its deemed ready; which has not occurred yet.

FYI:  I'm on the *Ubuntu News* team, and we've not yet published the release of Ubuntu 23.10, as it's not reached the *trigger* point in the release cycle for our post to be created & published. I'm also a Lubuntu team member, yet Lubuntu has completed all it's steps, as we got our *go ahead* from the *Ubuntu Release team* prior to the ISO issue being discovered; we use `calamares` (as installer) and thus are not impacted & weren't thus required to *pause* release.

[/FONT][/COLOR]The [Ubuntu Release team]("https://launchpad.net/~ubuntu-release") have checklists they perform in releases, as they aid in steps being completed correctly, with processes done in order.

A  release occurs, firstly for new users who want to perform a fresh  install. This is the official release and relates to the ISO as is used  for new installs. This hasn't yet completed for 23.10 (*refer my other post*) yet, but should in a day or so.

The ISO release is always a thursday; 2nd to 4th thursday of April or October (*not the last thursday unless the cycle was delayed a week*). The Release team usually have a meeting early in the following week to assess the state of the *release-upgrade* issues that were found in QA, and decide if it's *stable* enough for existing users, or they should wait & re-assess at a subsequent meeting. The goal of this is *stability*.  

Given the release hasn't yet completed;ISO release  is still the focus. Normally the release finishes on the Thursday the  week before, and late Monday is the review on whether or not the *release-upgrade*  system is stable & should be opened. We're not late Monday yet, so  this wouldn't be expected for 23.10 yet even if the release issues had  not occurred.
[/LEFT]

---

### Post by palteater on 2023-10-16
All right, thank you for that answer!

---

### Post by nador2 on 2023-10-20
> **guiverc said:**
> You haven't specifically mentioned what release you're asking about, but I'll assume it's Ubuntu 23.10 which hasn't finished it's release yet.


Why is this not mentioned here? [https://help.ubuntu.com/community/KineticUpgrades/Kubuntu](https://help.ubuntu.com/community/KineticUpgrades/Kubuntu)

---

### Post by guiverc on 2023-10-20
> **nador2 said:**
> Why is this not mentioned here? [https://help.ubuntu.com/community/KineticUpgrades/Kubuntu](https://help.ubuntu.com/community/KineticUpgrades/Kubuntu)

The upgrade I was writing about was *lunar* (23.04) to *mantic* (23.10), ie. [https://help.ubuntu.com/community/ManticUpgrades](https://help.ubuntu.com/community/ManticUpgrades)

The link you mention was the Kubuntu specific page relating to *jammy* (22.04) upgrades to *kinetic* (22.10), which isn't possible anymore as [Ubuntu 22.10 (*kinetic*) is *End of Life*]("https://fridge.ubuntu.com/2023/07/27/ubuntu-22-10-kinetic-kudu-end-of-life-reached-on-july-20-2023/")which will mean the Ubuntu *release-upgrader tool *on checking th*e [meta release file]("https://changelogs.ubuntu.com/meta-release") *will not allow it due to the "*Supported: 0*" in that file.

KineticUpgrades was from the prior release to *kinetic* or 22.10
LunarUpgrades was from the prior release to *lunar* or 23.04
ManticUpgrades is from the prior release to *mantic* or 23.10

A page is created for each release, covering the supported upgrades.

---

### Post by palteater on 2023-10-22
Okay, now several days have passed, 23.10.1 is released, and "sudo do-release-upgrade" still doesn't work for me.

It has been like this for many releases now. Years. Why is there a week-or-more delay for me each time when it does not seem to be so for other people?

---

### Post by guiverc on 2023-10-22
Very little has changed.

- The 23.10 status tracking document still reports the release is ***in progress** - *[https://discourse.ubuntu.com/t/mantic-minotaur-23-10-release-status-tracking/37887](https://discourse.ubuntu.com/t/mantic-minotaur-23-10-release-status-tracking/37887)

- Those who want to upgrade can still do so as using the method provided in the release announcements & release notes - [https://help.ubuntu.com/community/ManticUpgrades](https://help.ubuntu.com/community/ManticUpgrades)  though not forcing it is still the preferred option

- The release announcement has made it to the Ubuntu Fridge - [https://fridge.ubuntu.com/2023/10/16/ubuntu-23-10-mantic-minotaur-released/](https://fridge.ubuntu.com/2023/10/16/ubuntu-23-10-mantic-minotaur-released/)

- the date I'd suggest is earliest for it to open is *close*, but still hasn't been reached yet (*I've commented this in a number of places, reddit & on the added comments under my answer on this post too *[https://askubuntu.com/questions/1489169/cant-upgrade-from-ubuntu-23-04-to-23-10/1489215#1489215](https://askubuntu.com/questions/1489169/cant-upgrade-from-ubuntu-23-04-to-23-10/1489215#1489215))  

My date is based on what I normally see; which is the earliest the release *taps *are turned on is the MONDAY AFTER I've posted to the fridge. I'm on the Ubuntu News team, thus see the release through those eyes to an extent (*and I've been posting to the fridge since 2017*).  if it's delayed, the indications are usually rather evident in the RELEASE STATUS document I provided; which has a **BLOCKER BUG** IN RED HIGHLIGHTED.  (FYI:  *The MONDAY I'm using is not my local time as its tuesday my local; Ubuntu uses UTC by default*)

Yes that blocker bug has many components to it marked as FIX RELEASED; alas not all yet*. *I'm aware of that blocker bug personally as I QA tested for it with Lubuntu & did not experience it; but you need to have firefox open to experience it and I did not. There is a bug currently on opening the *nn* repository, which I've been told needs to occur before all blocker bugs can be marked as released, but that may occur after the weekend fitting my guessed timeline anyway.

The upgrade can be forced as already stated & documented on [https://help.ubuntu.com/community/ManticUpgrades](https://help.ubuntu.com/community/ManticUpgrades)

---

### Post by palteater on 2023-10-23
Oh. Well - thank you for information and patience.

My confusion is cleared up - 23.10 **is** released (the ISO is right there). It is the _update_ that isn't, due to some bug. 

And I take it that this is a common thing, because I haven't been able to upgrade within a week for the last dozen releases. I am not complaining, I just state that I think I understand the process now. Because from my POV it has been like "*Sure, you can buy the new car and drive it out of here today. Unless you want to change in your old car, then we have none in stock.*"

---

### Post by guiverc on 2023-10-24
> **palteater said:**
> "*Sure, you can buy the new car and drive it out of here today. Unless you want to change in your old car, then we have none in stock.*"

The ISO being released for new installs has users drive away with a brand new card.

The *release-upgrade* process is like taking in your last years model (*or a model many generations ago that you've release-upgraded many times*), and having all parts of the card upgraded with newer parts, but your changes (*stickers on the windows, changed radio/stereo etc*) survive on that car, so when you drive it away it's got the new engine (*it was swapped* *along with many other components*) but everything that was yours (*the stickers, altered radio, even the dints the kids made with that soccer ball months ago*) remain.

The *development* teams worry about all issues that will impact new users (new installs) prior to ISO release, as they can worry about the *release-upgrade* issues now, in the period between ISO release & the opening of the *'taps*' for upgrades.

I have noted users report issues with the forced upgrade, including a bug that was marked as 'resolved'... but I'm not a *developer*, and not aware of everything the need to consider before turning those '*taps*'.  I do note *noble* or 24.04 can now be found at [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/), maybe we'll see the upgrade open early next week (*early the week is common**, as if there are problems Canonical employees aren't made to work over the weekend*).

---

