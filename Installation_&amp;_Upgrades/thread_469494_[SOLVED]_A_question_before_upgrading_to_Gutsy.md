---
title: "[SOLVED] A question before upgrading to Gutsy"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by sci-fi guy on 2007-06-09
I would like to upgrade to Gutsy, but I see [here]("http://onlyubuntu.blogspot.com/2007/04/ubuntu-710-gutsy-gibbon-release-dates.html") that new discs will be released every three weeks or so.  I would rather not have to download another disc every time, I am wondering if the changes from disc 1 to disc 2 etc. will be downloadable from the automatic updates instead.

---

### Post by koshari on 2007-06-10
basicly yes, automatic upgrades would keep you up to date, keep in mind it will be a lot more frequent than a released candidiate.

why doyou want to run 7.10?

---

### Post by sci-fi guy on 2007-06-10
Largely because I want to have the latest and greatest, and am willing to tolerate a little instability for that.  And if I can report bugs to the developers at the same time, all the better.

---

### Post by bdoe on 2007-08-28
Not quite sure where to post this, as I am not planning to upgrade to Gutsy until it is released officially, but I need some advice.

I am planning to do a clean install of Gutsy when it comes out, but I don't want to lose any of my existing data.  What is the best way to go about doing a clean install while preserving my data and settings?  And what of installed programs?

Also, if I were to decide to do an in-place upgrade instead of a clean install, would this preserve all my data, settings, and programs?  Is this the advisable way to go, or would this cause problems with outdated files later on down the road?

I am currently running Ubuntu 7.04 Feisty 64-bit.

---

### Post by merlinus on 2007-08-28
Save everything in /home, which contains preferences, settings, and configurations.  Make sure hidden files are showing.

In fact, it is usually best to create a separate /home partition during installation, so that way you will not have to back up that data.

You can simply choose to not format that partition during upgrading or reinstalling.

And upgrades are usually dicey at best, so it is better to do a clean install and then reinstall required apps.  Settings, etc. for same will be retained in /home.

-merlin

---

