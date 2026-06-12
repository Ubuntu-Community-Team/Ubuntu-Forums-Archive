---
title: "Upgrading from Dapper Drake 6.06.1 to Gutsy Gibbon 7.10"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by jdackle on 2007-10-21
So... What's your thoughts on how to do this?

Probably best to try and upgrade Dapper to Edgy, then Edgy to Feisty and only then to Gibbon, huh?
Man... I'm thinking I'm going to wait for the next LTS after all... lol
But I'd really like to upgrade now.

Any thoughts?


Thanks! :)

---

### Post by dpar on 2007-10-21
I believe you are right. You have to go from Dapper to Edgy to Feisty to Gutsy. Probably will be the same to get to the next LTS.
Or you can just do a fresh install directly to Gutsy:)

---

### Post by rvickers on 2007-10-22
I tried the upgrade path from Dapper and it failed so I just did a full install of Gutsy and every thing's fine now...

---

### Post by kashey_be on 2007-10-22
I have been using Ubuntu for a while now.
I did the upgrade path from Dapper to edgy to feisty and now to gutsy.
The procedure was very painful, especially in the edgy to feisty part where I lost usability of my vt's due to a typo which I had to manually correct.
A strong advice to anyone thinking of taking the same road:
If you can, better do a clean install.
However, if there's too much stuff changed & customized, and you don't remember how to repeat it, try the upgrade path, but be ready to spend some time on it.
Very recommended to people who study threw problems!

---

### Post by jdackle on 2007-10-22
Thanks to all for your replies! :)


A small personal note/opinion:
> **dpar said:**
> I believe you are right. You have to go from Dapper to Edgy to Feisty to Gutsy. Probably will be the same to get to the next LTS. IMHO if that is the case regarding the upgrade from one LTS version to the next, it feels a bit awkward, from the user's point of view. However, I do understand that from the developers perspective, it might be very awkward too to have it the other way...
And IMO it is true that if you only do that every three or five years... It's bearable... :-P


So, this is what I'll do:

1. Burn Gutsy on a CD so I can do a fresh install if #3 becomes too difficult or worse (always good to have that CD anyways... ;-))!

2. Backup my data! ;-)

3.Do the upgrade path dapper->edgy->feisty->gutsy, minding a couple documents I found on the wiki:
[Installation/UpgradeFromOldVersion]("https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion")
[UpgradeNotes]("https://help.ubuntu.com/community/UpgradeNotes")

I'll report back here afterwards. ;-)


Cheers!

---

### Post by jdackle on 2007-10-25
Ok, so...

I successfully did points 1 and 2...

Then... I started the upgrade from Dapper to Edgy...
All seemed well and the actual packages installation was done! :) But..
On the "Cleanup" stage it got an error and consequently aborted. :(
May have been related to my use of finch at that moment - finch segfaulted and though I could get back to it with no porblems, when I went to check on the upgrade... Those were the news...
The system was not so stable afterwards it seemed but the worse part was I could get no Internet access through my Speedtouch 330 USB modem... :(

To make a long story short I did a fresh install of Gutsy! :)
So now I'm on Gutsy! :)
But the Internet was not easy to get either - actually it was in the begining, then it vanished and the, without me knowing how or why it came back! It may have to do with my changing Firestarter to watch ppp0 instead of nas0 (this is the interface my modem has to setup to function and ppp0 links directly to it). Anyways...

There also seems to be a few bugs scattered around but nothing serious - mostly annoyances (including unsuspected program crashes - firestarter's GUI is one example but the iptables settings it sets in is kept in place, so...).

Overall, I'M HAPPY! :)

Thanks for your help, guys and gals!

Cheers! :)


P.S.: I won't set the status for this as SOLVED til I can test it a bit more... ;)

---

### Post by jdackle on 2007-10-25
**Internet** seems stable now. :)


But I had a problem with **pidgin** and **dbus**:
Pidgin started out working (kind of - see below) alright. But then... It stopped working. It just would not start. When I tried to run it from a terminal (to check for any output) that's when I got the message pidgin could not connect to dbus or something.
So I installled the pidgin I'd complied for Dapper in /usr/local and ran it from there: exact same result. So it's NOT pidgin *per se* that's causing the problem.

So then I uninstalled the old version I had for Dapper from /usr/local and reran the default Gutsy pidgin so I could post the exact debus-related message here - only this time, Pidgin worked!!:shock:
I think DBUS can be used to track changes to files and directories so it makes some sense that after changing the default path to the pidgin executable (in my system, /usr/local/bin is looked into before /usr/bin) and then back to the original, I dunno... it may have been what was needed to "wake up" dbus...?
But ... how did it become messed-up in the first place?? :confused:


So I guess that's it for now.
**Audacious**, cool discovery for me :), often stops playback of a mms: type-URL... Other than that, I'm loving it! Always've been a fan of XMMS, including over beep media player, but now I think it's time to be audacious! lol

Cheers!

---

### Post by dugald on 2008-02-27
I have to upgrade from Dapper to Gutsy (and everything in between) in order to get the latest mono packages and hopefully fix a problem I have with my web server.  It has no desktop installed, and is on a dedicated server somewhere far away.

I am really worried that upgrading is going to floor the server (which has to be available all day) but I have spent so long getting it set up that nor do I want to lose all of my settings by doing a fresh install.  I don't even have access to run one.

Not sure exactly how to proceed.  If I get it wrong and someone else has to sort it out for my at the hosting company, it could be very expensive.  The packages installed are minimal: apache, mod_mono, php, mySQL, proFTPd.  Does that make me any more likely to succeed?  Any advice before I start? :confused:

---

### Post by Fíona on 2008-03-18
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=629054](http://ubuntuforums.org/showthread.php?t=629054) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Don' t do it!!

After a fresh install of gusty gibbon, I'm now (after 2 months) starting to experience serious problems. The gibbon keeps crashing and/or hanging. I' ve been looking at the forums and it' s not completely clear to me if the problem is hardware or a wild beast (an unstable gibbon). 

One post advised downgrading to "6.06 LTS and stick with it until a few months after 8.04 LTS is released in April" .

---

### Post by PmDematagoda on 2008-03-18
I am sorry but just because you face severe problems on Ubuntu Gutsy does not imply that the release is dangerous, it could be something on your own part where you may have installed improper packages, messed up the configuration files or deleted some important files by accident.

Please refrain from spreading this type of information unless you have a credible source as this can just cause people to panic which is something that no one wants.

---

