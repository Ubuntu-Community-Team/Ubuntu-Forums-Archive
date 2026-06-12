---
title: "Upgrading from 14.04, to 14.10, to 15.10 and 16.04"
date: 2016-03-16
forum: Installation &amp; Upgrades
---

### Post by RobGoss on 2016-03-16
Hello everyone I'm sure this question has been ask here more them once but! I wanted to see what's the best way for me to upgrade my current Ubuntu system with out messing things up.

I'm currently on **14.04, LTS** and wanted to get my system ready for the newest version of Ubuntu **16.04, **which will be released in a few weeks. From my understandings it's not possible to upgrade straight from **14.04** to **16.04** correct?

So will I need to upgrade to **14.10,** then **15.10,** in order to be ready for **16.04 **- when it's released in April. I was looking at a video I found on YouTube were they explained how to upgrade using the terminal and it specified to use the following commands ```
 sudo update-manager -d 
``` This will bring up the software updater and it advise me there is an upgrade available.

Well in fact it did say there was an upgrade available but it's telling me that **16.04** is now available and would I like to upgrade now. 

So you see I'm kinda confused about the correct way to upgrade my system with out messing up my current system, question, is this upgrade safe to take now even if 16.04 in not out yet?

Thanks so much for any help on this matter

---

### Post by grahammechanical on 2016-03-16
> From my understandings it's not possible to upgrade straight from **14.04** to **16.04** correct?

Wrong!

And that command will upgrade to a development version. That is the meaning of the -d switch. If you run that command after 16.04 is released an attempt will be made to upgrade your system to 16.10 development version. If you run that command now an attempt will be made to upgrade your system to the existing development version, xenial xerus (16.04 before it is released).

I say "an attempt" because the process may break the system. Best to wait until 16.04 is released and then run Update Manager. The upgrade will follow scripts constructed for that purpose by the developers. In fact for a few days after release date you will be nagged to upgrade every time you boot.

Preparation for upgrading is to 1) backup data; 2) revert the video driver to open source; 3) revert the desktop user interface to as default as possible. 4) disable any PPAs; 5) read the release notes.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)
> 
[h=2]Upgrading from Ubuntu 14.04 LTS or 15.10[/h] To upgrade on a desktop system: 


[LIST]
[*]Open the "Software & Updates" Setting in System Settings. 


[*]Select the 3rd Tab called "Updates". 
[*]Set the "Notify me of a new Ubuntu version" dropdown menu to "For any new version". 
[*]Press Alt+F2 and type in "update-manager" (without the quotes) into the command box. 
[*]Update Manager should open up and tell you: New distribution release '16.04 LTS' is available. 
[*]Click Upgrade and follow the on-screen instructions.
[/LIST]


Server installs require commands to upgrade but not desktop installs. Please see the section Upgrading to Development Release, if you do not believe me about the meaning of the -d switch.

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

Regards.

---

### Post by Bucky Ball on 2016-03-17
14.04 LTS will upgrade directly to 16.04 LTS. LTS> LTS upgrades have been around for awhile and leapfrog the interims in between. So do nothing. What you're wanting to do is dream the impossible dream (almost). You are going to need to get through two unsupported releases before you get to 15.10. Just not worth the effort (or the time). If you go that way, expect breakage, possibly unfixable, and put aside a good chunk of time (a day or two at least). 

Back up and clean install 15.10 or wait until 16.04 is available for upgrade from 14.04. If you upgrade to 16.04 now, still in development, expect unexepected breakage.

---

### Post by RobGoss on 2016-03-17
So is it best to wait until 16.04 is released then upgrade? both of you have different options which I'm sure has the correct answer I'm just not sure which one I should choose, wait or upgrade to the two version after 14.04. Thanks so much guys

---

### Post by howefield on 2016-03-17
> **RobGoss said:**
> So is it best to wait until 16.04 is released then upgrade? both of you have different options which I'm sure has the correct answer I'm just not sure which one I should choose, wait or upgrade to the two version after 14.04. Thanks so much guys

The fewer upgrades you do, the less chance of something breaking :)

Best (safest) option would be to wait 5 weeks (21st April) till 16.04 is released and upgrade direct from 14.04 to 16.04.

---

### Post by RobGoss on 2016-03-17
> **howefield said:**
> The fewer upgrades you do, the less chance of something breaking :)

Best (safest) option would be to wait 5 weeks (21st April) till 16.04 is released and upgrade direct from 14.04 to 16.04.

Sounds like a plan thank you guys so much for the help

---

