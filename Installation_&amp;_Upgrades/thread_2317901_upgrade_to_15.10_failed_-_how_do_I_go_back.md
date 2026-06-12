---
title: "upgrade to 15.10 failed - how do I go back?"
date: 2016-03-21
forum: Installation &amp; Upgrades
---

### Post by richard_day on 2016-03-21
Hi,
I was on ubuntu 14.xx LTS and rather rashly I decided to change my upgrade option to show all new releases and so attempted to upgrade to 15.10.
This was installing nicely, then the screen went black, there was no disk activity and it would not respond, so eventually I rebooted...
And I cannot get a system back up.

If someone knows what do next with their eyes shut then that would help, as I have not much information to give.
This laptop has a cracked screen and I use a vga cable to display to a TV.
I have never seen any boot information - the TV only displays anything when the desktop is ready.
The laptop screen glows white or is off - binary!

Currently on boot, the laptop screen glows for a minute then goes off - the caps lights are responsive on the keyboard, but then there is no disk activity.
I have tried newline.
I have tried down arrow, newline, down arrow down arrow  in case I am on the grub menu.
But there is no change or response.

I did originally install ubuntu blindly from a usb stick, and would do this again as there is no vital data on this laptop, but the mrs has been tidying and could have put it anywhere...

It could be the laptop has a hardware problem but that would be quite a coincidence, just after a failed upgrade.
So here I am. I just want to return to version 14.

Any ideas - I can try any ideas later this evening.

---

### Post by mastablasta on 2016-03-21
this Will be hard to troubleshoot. you are now the second one with similar issue. i am not sure why 15.10 pops up as there shouldnt' be any direct path from 14.04 to 15.10. upgrade should go like so:

14.04 LTS -> 14.10 -> 15.04 -> 15.10
or
14.04 LTS -> 16.04 LTS (when it comes out).

option 1:
boot with a live 15.10 USB, install the OS and overwrite the current mess (backup first). during install do not format the hard disk live boot should still get you to desktop where you can install and backup data.

option 2
same thing but with latest 14.04 install disk.

---

### Post by howefield on 2016-03-21
First off, you don't go back. At least not without a fresh install.

I tested the upgrade from 14.04 to 15.10 a couple of weeks ago and it went well, but also got a black screen for what seemed a longer period of time than it should have been, and like you eventually rebooted. Had to boot into Recovery mode from the Grub menu and select "dpkg - Repair broken packages" and all was well but if your laptop can't show the grub menu and the TV doesn't display until the system is booted looks like a fresh install is about the easiest way.

---

### Post by richard_day on 2016-03-21
OK thanks for the help.

update: I downloaded ubuntu 14.04.4 from windows, and rufus'ed an old disk drive in the absence of my missing usb stick.
Plugged it into offending laptop, but when attempting to guess when to hit F8 to get to the boot menu, and failing,
I noticed that the screen was staying lit up, rather than turning off after 10secs (no activity on the external disk either) - I was possibly finally in the Grub menu.
I can only think that having 2 ways of booting with the external drive attached triggered Grub despite my earlier attempts by holding shift at boot time.

Down arrow newline, down newline, down down newline I thought would start the dpkg repair option, but instead brought up a terminal window on the TV! But I was in. A quick google gave some likely commands:
**sudo apt-get update &#8211;fix-missing (failed - no internet access)**

  **sudo dpkg &#8211;configure -a (ran along time and errored)**

  [B]sudo apt-get install -f (not very happy)

[/B]None of this was very convincing, but a shutdown and restart got the desktop showing again, where I run the 15.10 update again in the hope that it would tidy itself up**, **and avoid trouble at a later date.So I think my issue is now resolved.

Thanks

---

### Post by kansasnoob on 2016-03-21
> **mastablasta said:**
> this Will be hard to troubleshoot. you are now the second one with similar issue. i am not sure why 15.10 pops up as there shouldnt' be any direct path from 14.04 to 15.10. upgrade should go like so:

14.04 LTS -> 14.10 -> 15.04 -> 15.10
or
14.04 LTS -> 16.04 LTS (when it comes out).

option 1:
boot with a live 15.10 USB, install the OS and overwrite the current mess (backup first). during install do not format the hard disk live boot should still get you to desktop where you can install and backup data.

option 2
same thing but with latest 14.04 install disk.

That is no longer the case,  Trusty now offers to upgrade to Wily if the release upgrade setting is changed from notifying for LTS only to any new release:

.[http://ubuntuforums.org/showthread.php?t=2312528](http://ubuntuforums.org/showthread.php?t=2312528)

---

### Post by Bucky Ball on 2016-03-21
> **richard_day said:**
> Hi,
I was on ubuntu 14.xx LTS and rather rashly I decided to change my upgrade option to show all new releases and so attempted to upgrade to 15.10.
This was installing nicely, then the screen went black, there was no disk activity and it would not respond, so eventually I rebooted...
And I cannot get a system back up.

Welcome. Have seen a few people do this and I have no idea why Canonical (presuming they're responsible for it) decided to provide an upgrade path of this nature. This 'long jump' leap has never happened before. Perhaps a new 'innovation'. Perhaps something to do with something else. Sure they have their reasons. 

The net result that I have seen has been new users upgrading from 14.04 to 15.10 a month before the next LTS is released, possibly unaware that LTS upgrades directly to LTS, leapfrogging the interim releases in between. In other words, if you waited a month you could have upgraded directly to 16.04 LTS from 14.04 LTS. *shrugs*

Guess we learn the hard way but glad you got things sorted out. Hope your experiences help others, but they'll be redundant shortly as 14.04 users will be able to go straight to the next LTS shortly.

Good luck, enjoy the ride and see the first link in my signature at the bottom of this post if you're happy you are 'resolved' and 'solved'. :)

---

### Post by Dedamraz on 2016-03-22
> **richard_day said:**
> 
Down arrow newline, down newline, down down newline I thought would start the dpkg repair option, but instead brought up a terminal window on the TV! But I was in. A quick google gave some likely commands:
**sudo apt-get update –fix-missing (failed - no internet access)**

  **sudo dpkg –configure -a (ran along time and errored)**

  [B]sudo apt-get install -f (not very happy)

[/B]None of this was very convincing, but a shutdown and restart got the desktop showing again, where I run the 15.10 update again in the hope that it would tidy itself up**, **and avoid trouble at a later date.So I think my issue is now resolved.

Thanks
Hm, I actually had the same problem where Internet access was the issue, and dpkg encountered a timeout.
Eventually I managed to install a fresh and clean 15.10 version via USB Boot but with specifically this installation technique (since all other options failed miserably on country select freeze screen) so there is no need to go back tbh:
1. Something else
2. Deleted all existing partitions
4. Created new partitions in following order: SDA, Swap, /, /home
5. Onwards the installation went smoothly

Do note that I have been battling with the installation for about 4-5 hours since every single time it either froze, or didn't want to download updates, nor connect to internet sometimes. Terminal commands were useless as well since my account had no permissions (wtf?).

This all has absolutely no logical sense at all to anyone who has at least 5% knowledge about computers, but it worked. Foul magic I tell you...

---

### Post by richard_day on 2016-03-22
> **Bucky Ball said:**
> Welcome. Have seen a few people do this and I have no idea why Canonical (presuming they're responsible for it) decided to provide an upgrade path of this nature. This 'long jump' leap has never happened before. Perhaps a new 'innovation'. Perhaps something to do with something else. Sure they have their reasons. 

The net result that I have seen has been new users upgrading from 14.04 to 15.10 a month before the next LTS is released, possibly unaware that LTS upgrades directly to LTS, leapfrogging the interim releases in between. In other words, if you waited a month you could have upgraded directly to 16.04 LTS from 14.04 LTS. *shrugs*

What drew me into this mess was a new timeout message whenever I checked for updates.
I thought that I had somehow been sent down a release dead end, so the setting to check for the latest release looked appealing.
As a casual home user, long term support was not an issue, not that I fully appreciated I was changing streams.

Further research shows that actually it was just the google chrome repository that was timing out, and Ubuntu was fully up to date.

To many the information shown would have been crystal clear, along with the risk I was taking with this long leap update.
To those who have easy access to Grub, and a release cd it would an easy problem to fix.
So I guess this is not a big deal, but I feel I had not done too much wrong, yet was it was fiddly to get out of the situation.

Oh well - until next time!

thanks and issue closed.

---

### Post by Bucky Ball on 2016-03-22
We live and learn ... which is a good thing! Happy Ubuntu-ing. :)

---

