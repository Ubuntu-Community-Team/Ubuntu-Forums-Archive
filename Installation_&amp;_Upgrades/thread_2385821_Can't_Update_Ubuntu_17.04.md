---
title: "Can't Update Ubuntu 17.04"
date: 2018-02-25
forum: Installation &amp; Upgrades
---

### Post by h8away on 2018-02-25
I'm relatively new to ubuntu and I'm loving the OS so far, but uhm. Is there any specific reason why I cannot update? You see, I've been gone from the computer for a really long time and I have atleast 362 MB in updates that I can't push because it tells me "You have no internet connection" (but I do) and i've tested it on everything. :confused:

The sudo apt-get update stops at 20% than says this at the top of it, I was wondering if anyone could help me receive this update so I can stop pressuring?


Oh, and more one quick thing. The budgie desktop that I am currently using, doesn't have the side panel with all the apps on it. How may I obtain that bar?
[https://imgur.com/a/cRZ2A](https://imgur.com/a/cRZ2A)

And yes, I'm using my tv as my primary monitor because my laptop's screen is broken.

---

### Post by oldos2er on 2018-02-25
You can't update because 17.04 is no longer supported, see [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by h8away on 2018-02-25
Quick question, how do I update when I've reached end of life? Do I require a flash drive to re do the process? Or can I directly install the .iso file from Ubuntu 17.04? 
I feel very stuck right now.

---

### Post by h8away on 2018-02-25
> **oldos2er said:**
> You can't update because 17.04 is no longer supported, see [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I wrote the linux 17.10 iso to a flashdrive with my windows PC, but on my current linux laptop, I can't see the boot screen and I'm afraid I will mess up the laptop if I blindly go and randomly sequence until I hit the right mark. Is there anyway to update WITHOUT using the written image? Or is it too late for me? :confused:

---

### Post by oldos2er on 2018-02-25
You can try

```
do-release-upgrade
```, but I'm not certain that would work. If it doesn't, see [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by h8away on 2018-02-25
> **oldos2er said:**
> You can try

```
do-release-upgrade
```, but I'm not certain that would work. If it doesn't, see [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Thank you, the update is currently unpacking I should have it within the hour or two. If anything goes wrong, I will consult the website.

---

