---
title: "Update Manager Crashes"
date: 2015-08-08
forum: Installation &amp; Upgrades
---

### Post by ChuckyZ28 on 2015-08-08
So I have an older laptop (1.6ghz Intel Processor, 512mb RAM) I have  tried to put off doing the update because the last time I tried to  update the computer itself was totally unusable, I began having a little  alert diamond pop up that says my system is outdated (10.04) and that I  needed to update, but when I bring the update manager up I receive a notification saying that I need to update, but as soon as I touch anything it immediately  crashes, I backed up what little files I had, and reformatted the hard  drive and reinstalled a fresh OS (10.04) and I am still getting the same  errors. I do not have a DVD burner, and my PC does not support USB  booting so I am stuck using my 10.04 disk. Does anyone have any idea of  what exactly is going on here, and maybe some solution for me?

[ATTACH=CONFIG]263718[/ATTACH]


 [ATTACH=CONFIG]263716[/ATTACH]

---

### Post by deadflowr on 2015-08-08
> [COLOR=#000000]Does anyone have any idea of what exactly is going on here, and maybe some solution for me?[/COLOR]
Yep, 10.04 is no longer supported and the repositories for it are gone.
You have two options with the setup you have

1)Do an in place release upgrade to 12.04.
Of course this option will bring in unity and all upgrades to all packages you have.

2)Download ubuntu minimal cd and do an install with that.

Both methods require a functional network connection.

The release upgrade method only requires you to change the repository source list one time.
So you would keep your existing system.
As mentioned earlier, release-upgrades install upgraded packages for all packages, so the more you've installed, the longer and bigger the upgrade will take.

The mini option on the other hand, will only install the base system at first and allow you to choose additional packages after the base is installed.
So you can select a different, more comfortable, desktop interface if unity is not to your liking.

Reference on end of life upgrades here
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) 

asnd reference for mini here
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
added bonus amjjawad's mini how-to with screenshots for better understanding here
[http://amjjawad.blogspot.com/2013/07/ubuntu-mini-iso-installation-process.html](http://amjjawad.blogspot.com/2013/07/ubuntu-mini-iso-installation-process.html)

Hope it helps.
Not much we can do with the existing setup.

---

### Post by ChuckyZ28 on 2015-08-08
> **deadflowr said:**
> 1)Do an in place release upgrade to 12.04.
Of course this option will bring in unity and all upgrades to all packages you have.

How do I do this, and will it run on my poor system specifications? Like I said, in the past I tried an update but caused my system hell because it could not support it, I had to reinstall the older 10.04 to get my PC back.

---

