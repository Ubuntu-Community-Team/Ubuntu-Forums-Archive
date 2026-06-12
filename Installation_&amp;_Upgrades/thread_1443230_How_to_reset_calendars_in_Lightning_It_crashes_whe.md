---
title: "How to reset calendars in Lightning? It crashes when starting Thunderbird"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by The Bright Side on 2010-03-30
Hey guys!

This is not the first time that Thunderbird's Lightning plugin crashes on me, but this time it pretty much killed the whole Thunderbird along with it. There is some event in my calendar that Lightning tries to remind me of, so every time I now open Thunderbird, the reminder window appears, but it is blank and Thunderbird completely freezes (gets greyed out by Ubuntu). Sometimes, the reminder window doesn't even appear.

Bottom line is, I cannot use Thunderbird together with Lightning anymore because some stupid calendar or event seems to be corrupted. I uninstalled Lightning and everything was fine, then re-installed it and it's back to dead.

Isn't there a way I can completely remove Lightning, including all its calendar data and settings, and then do a clean re-install? I'd hate to move away from it completely.

Thanks!

---

### Post by Pepe Lebuntu on 2010-05-05
Hey Bright side. You CAN go into Synaptics of course, and click on completely remove, then reinstall it afterwards. This should clean things up a bit, but I doubt that'll really help ultimately. I could be wrong and it could work fine, so give it a go. It certainly shouldn't hurt. Just back up your .thunderbird folder in your home directory first.

Having said that, I'm having similar problems now in TB3 and L1.0b1. What's happening for me is that, Lightning seems to double up entries from one Google calendar, and says they are from multiple ones.

Here's a Screenshot:

[IMG]http://dl.dropbox.com/u/1462498/Lightning.jpg[/IMG]

Any ideas? It's obviously slowing down Thunderbird as well.

---

### Post by Pepe Lebuntu on 2010-05-07
This is still being a bit of a pain, and now I can't actually put in new entries into my calendars! It worked fine five days ago on T2 and U9.10. What's going on here?

---

### Post by RanTheLab on 2010-08-14
> **Pepe Lebuntu said:**
> Hey Bright side. You CAN go into Synaptics of course, and click on completely remove, then reinstall it afterwards. This should clean things up a bit, but I doubt that'll really help ultimately. I could be wrong and it could work fine, so give it a go. It certainly shouldn't hurt. Just back up your .thunderbird folder in your home directory first.

Having said that, I'm having similar problems now in TB3 and L1.0b1. What's happening for me is that, Lightning seems to double up entries from one Google calendar, and says they are from multiple ones.

Here's a Screenshot:

[IMG]http://dl.dropbox.com/u/1462498/Lightning.jpg[/IMG]

Any ideas? It's obviously slowing down Thunderbird as well.
I have had a similar problem as this.  I have 5 different google calendars configured in lightning.  I was getting duplicate and inconsistent entries.  I thought I would get smart and try out evolution...after all a new application should have separate dataspace, right?  Well, the it did not help!  Add an entry on 1 calendar and it would show up on 2 others in lightning and evolution.  The entries are correct on the calendar in the web browser.  I noticed that the 3 calendars with the duplicate entries all had 'Make changes AND manage sharing', none of the others did for my user.  I changed that on 2 of them to just 'Make changes'.  That did not seem to help, but then I was starting with garbage.  

To cut to the chase, the data on the web is correct, but the data thru 2 different clients was not...is there a problem with the API these clients use when permissions are 'Make changes AND manage sharing'?

I solved this by deleting all my calendars and re-adding them (note the last calendar could not be deleted until after another was re-added).  So far so good.

UPDATE:
1 day later, I now have 5 (one for each calendar defined) entries for each calendar entry...

ANOTHER UPDATE:
Turning off the 'cache EXPIRAMENTAL' box has restored order to the system...guess working off line will not be an option.

---

### Post by The Bright Side on 2010-08-14
I feel bad for not marking this thread as "SOLVED" way back when. The solution for my particular problem is a bit embarrassing: whenever the notification pops up, a sound is played. If, at the same time, you have another app running that plays sound - for instance, Flash in Firefox or perhaps VLC in pass through mode - Lightning will freeze until the other application "frees up" the sound card.

It will then go "ba-ding!" and everything will be fine.

It's just a sound effect stuck in limbo, waiting to play.

Well, it was for me.

---

