---
title: "1st day and already I'm 2 years behind"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by mr.scissorkick on 2010-06-16
So a while ago my buddy gave me a live CD for Ubuntu.  He said it was the cat's meow, the bee's knees, etc.
I tried it for a few days, but mostly stuck with Windows because I liked my effortless wireless capabilities.  Eventually, I stopped using Ubuntu altogether.  Recently, Vista stopped loading (long story), so I dug up the live CD and here I am... I decided to get down to the nitty gritty and get my atheros wireless card all linuxed out.  The good news, there was a thread stickied dealing with that exact maneuver; the bad news, apparently the advice was made absolute when the first Ibexes became Intrepid.  Well, what about us yayhoos who are rockin' the old school Hardy Heron? 
Should I just upgrade?  If so, is it as easy as putting a CD in and clicking a few times? Because that's how I got Mr. Heron to make a nest in my PC.
If I am allowed to shun innovation and stay true to my 8.04, where can I find the obsoletified instructions for  the atheros ar5007?

---

### Post by lechien73 on 2010-06-17
Since Hardy was the previous LTS (Long Term Support) release, there's a direct upgrade path to the latest LTS release - 10.04 Lucid Lynx.

This page contains the upgrade notes:
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

Hope it goes well for you - enjoy your moments of Lucid-ity :)

---

### Post by darkod on 2010-06-17
If the wi-fi is your most important issue you should download the image for Lucid, burn a cd and use Try Ubuntu to load live mode. See if the card is working. If it is, it should work after you install or upgrade too.

If it's not, the upgrade will probably make it stop working. Although it doesn't sound like it's working right now.

Depending what type of card it is, usb or internal, you can try to get the exact chip model by:

lsusb

or

lspci

and search for a procedure/driver for that exact chipset.

---

### Post by Rasa1111 on 2010-06-17
:lol: funny title. :)

good advice darkod.

 I would just download [Lucid Lynx~Here]("http://releases.ubuntu.com/lucid/")
and then burn it to a cd, 
then run it from the CD, and if all works well..
then yeah, it will only be a few easy clicks.

---

### Post by leorolla on 2010-06-17
Yeah, that's what you should do... boot from Ubuntu 10.04 and see if it works well there.

If your computer boots from USB you don't even need to spend a CD :)

Simple way: get Ubuntu 9.10+ running somewhere. If you have no idea where, you can install it inside Wubi and removing it takes a couple of seconds. Then open System-Adminstration->StartupDiskCreator and write it to an empty pendrive.

---

### Post by dabl on 2010-06-17
Funny title!  :lolflag:

Here's your situation, bluntly:  If the learning curve that you are facing is one mile high, then the difference between 8.04 (or 9.10) and 10.04 is the last two feet.  You might was well strap on the latest version and learn it, as to learn the prior version plus (sooner or later) the difference to 10.04.

---

### Post by Boondoklife on 2010-06-17
> **dabl said:**
> You might was well strap on the latest version and learn it, as to learn the prior version plus (sooner or later) the difference to 10.04.

Not only that, but there maybe a bug you run into with 8.04 that is not present in 10.04. You could very well drive yourself insane trying to fix something that has already been fixed.

---

### Post by mr.scissorkick on 2010-06-17
Thanks to all those willing to read such a long post. I am in the upgrade process as I type (fetching file 560 of 1617). 
Hope this works, right?  At least I'll be one of the cool kids until Masochistic Marmoset is released...


Edit: Lucid is the answer. My wireless card never new what hit it. Thanks again.

---

### Post by Rasa1111 on 2010-06-18
> **mr.scissorkick said:**
> Thanks to all those willing to read such a long post. I am in the upgrade process as I type (fetching file 560 of 1617). 
Hope this works, right?  At least I'll be one of the cool kids until Masochistic Marmoset is released...


Edit: Lucid is the answer. My wireless card never new what hit it. Thanks again.

 haha, niice!  :guitar:

---

