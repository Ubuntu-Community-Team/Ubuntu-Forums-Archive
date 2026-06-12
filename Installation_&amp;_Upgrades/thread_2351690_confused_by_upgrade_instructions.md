---
title: "confused by upgrade instructions"
date: 2017-02-05
forum: Installation &amp; Upgrades
---

### Post by Gnusboy on 2017-02-05
Hello

I'm trying to upgrade from Ubuntu 14.04 to 16.04 and the instructions are confusing to me.
The directions say I should upgrade to 14.10, then to 15.04 and then to 15.10 and finally to 16.04
But ... there are other instructions that are different ...

[h=2]Upgrading from Ubuntu 14.04 LTS or 15.10[/h] To upgrade on a desktop system: 

[LIST]
[*]Open the "Software & Updates" Setting in System Settings. 

[*]Select the 3rd Tab called "Updates". 
[*]Set  the "Notify me of a new Ubuntu version" drop-down menu to
[*]
[*]"**For any new  version" if you are using 15.10, set it to "long-term support versions"  if you are using 14.04 LTS. **
[*]
[*]Press Alt+F2 and type in "update-manager" (without the quotes) into the command box. 
[*]Software Updater should open up and tell you: New distribution release '16.04 LTS' is available. 
[*]Click Upgrade and follow the on-screen instructions.
[*]
[/LIST]
Going by what I see I need to do the 14.10 + 15.04 + 15.10 + 16.04 - this all sounds simple except I can't find any of the versions between 14.04 (mine) and 15.10 - 
all I can find is a direct upgrade to 16.04 - which can goof up my system.

I've backed up most of my important data. etc., but I would be distressed to lose any of the remaining files on my system. (the data backup is a different problem)
So, I'd like to get a definitive instructions for getting to 16.04.
I hope someone can help.
Thanks.

---

### Post by Bucky Ball on 2017-02-05
There is absolutely no reason whatsoever to upgrade through all those releases. LTS upgrades directly to LTS. You reckon going through a handful of upgrades to get to 16.04 is NOT going to screw up your system??? There is a MUCH better chance it will happen trying to do that than a direct upgrade LTS to LTS. What makes you think one has more chance of screwage than another? You are trusting a handful of upgrades over one!

Go to the 'Software and Updates> Updates' tab, set 'Notify me of a new Ubuntu version' to 'For long-term support versions'. Close and save those changes. Use the Software Updater and you should be informed that 16.04 LTS is ready to go. Go for it!

Be warned: ALWAYS backup your machine before doing upgrades. Disable or remove any PPAs you have added manually and, if you've added video drivers, good idea to switch back to the open-source ones before the upgrade. You want to get the machine as 'vanilla' as possible.

Any website that tells you to upgrade through umpteen versions is sending you down the garden path. Many people won't go near net upgrades and backup and do a clean install whenever they want to upgrade. An upgrade to the next release, maybe. Upgrading through two or three releases to get to where you want to go? Don't bother. Will take forever and generally a problematic learning curve which you may or may not be prepared for.

The reason you can't find those other releases is because they no longer exist, theoretically. They are not supported and end-of-life. Not to say you're not more than welcome to go on the goose chase as going this way is not impossible, but put aside a decent chunk of time to research how to do it, have extremely reliable backups and a notepad and prepare for the learning curve when things possibly crash and burn as you work through the EOL releases. 

Good luck.

---

### Post by Gnusboy on 2017-02-06
Thanks Bucky.

If I understand, I can go straight from 14.04 directly to 16.04, right?
Backing up my system has been a real hassle. My system is getting progressively fluky for some time and it's a big problem.
All that works is to find the important files and put them on DVD. Hence, the desire to upgrade.  

I actually got all that upgrade info from the official Ubuntu documentation. Crazy, eh?

[h=1][SIZE=3]**General Upgrade Information:**[/SIZE][/h] To avoid damaging  your running system, upgrading should only be done from one release to  the next release (e.g. Ubuntu 12.04 to Ubuntu 12.10) or from one LTS  release to the next (e.g. Ubuntu 10.04 LTS to Ubuntu 12.04 LTS). If you  wish to 'skip' a version, you can back up your data and do a fresh  installation, or progressively upgrade to each successive version. [B] For  example, to upgrade from Ubuntu 11.10 to Ubuntu 12.10, first upgrade to  12.04, then upgrade 12.04 to 12.10.

[/B]

---

### Post by Impavidus on 2017-02-06
Yes, you can go directly from 14.04 LTS to 16.04 LTS.

As long as LTS releases have existed, the rule has been that you can upgrade from any release to the next and from any LTS release to the next LTS release. But upgrading to a release that is no longer supported is difficult and serves no real purpose. The currently supported releases are 12.04 LTS, 14.04 LTS, 16.04 LTS and 16.10.

Upgrading rarely fixes a fluky system. It's more likely to make it even more fluky. I had a system upgraded LTS to LTS from 6.06 to 14.04. It slowly became more fluky. A fresh install of 16.04 fixed it.

---

### Post by Bucky Ball on 2017-02-06
> **Gnusboy said:**
>  My system is getting progressively fluky for some time and it's a big problem.
All that works is to find the important files and put them on DVD. Hence, the desire to upgrade.

That is not good. Trying to upgrade a broken system will upgrade you to a broken system. Two suggestions: fix 14.04 LTS then upgrade to 16.04 LTS via the net, or backup what you need and do a clean install. I recommend the latter.

> [B] For  example, to upgrade from Ubuntu 11.10 to Ubuntu 12.10, first upgrade to  12.04, then upgrade 12.04 to 12.10.

[/B]

And you're not on an interim release like 11.10 or 12.10. You're running 14.04 LTS which upgrades directly to 16.04 LTS, leap-frogging everything in between, which is good because 15.04 and 15.10 are both EOL and you can't go there anyway. No point referring back to the instructions you first looked at. They do not apply to your situation.

---

### Post by RobGoss on 2017-02-06
I would recommend doing a clean installation and avoid all the headache that will come from trying to upgrade from so many releases

Backup any important data and files a you have and start new, you will be glad you did because it will save you a lot of time

You've stated your current system is not performing as it should that leads me to believe a clean installation is best

---

### Post by Geoffrey_Arndt on 2017-02-06
In my view, the instructions for upgrading via the interim releases (such as 16.10 to 17.04) are intended for updating WHEN the interim is released,  . . . not two years later.   In other words, you progress up the ladder in stages, one step at a time and not simultaneously.   I have upgraded via that method, . . . no issues at all.   That actually seems a more stable/reliable method than updating LTS to LTS (but I have no experience in this particular method).

I concur with the others posting here . . . just save off your data to a large usb flashstick (v3 if possible) or to an external usb hdd.    Then do a fresh, clean install.    But, it's your choice.   If you do the LTS upgrades, be sure to disable any non-standard software sources (ppa's etc.)

---

