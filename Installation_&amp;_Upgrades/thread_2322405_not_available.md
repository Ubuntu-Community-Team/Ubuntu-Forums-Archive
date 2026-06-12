---
title: "not available"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2016-04-27
On a legacy HP pavilion with 14.04 I type 'sudo do-release-upgrade' and I get back the message saying that there are no new versions available. I understand that 16.04 has already been released. Is there anything that should be edited?

Thanks.

---

### Post by oldos2er on 2016-04-27
My understanding is that the LTS to LTS upgrade won't be available until 16.04's first point release in July.

[http://www.omgubuntu.co.uk/2016/04/how-to-upgrade-ubuntu-14-04-to-ubuntu-16-04-lts](http://www.omgubuntu.co.uk/2016/04/how-to-upgrade-ubuntu-14-04-to-ubuntu-16-04-lts)

---

### Post by danielsender on 2016-04-27
I did upgrade from 15.10 to 16.04 on a different machine, so from 14.04 to 16.04 is a different upgrade?

---

### Post by BazBear on 2016-04-27
I'm having the same issue. None of terminal commands I've seen recommended have offered an upgrade to 16.04, and the only upgrade option Software Updater will offer is an upgrade to 15.10 (and only after I changed the upgrade option from "LTS only" to "any new version").

---

### Post by BazBear on 2016-04-27
> **oldos2er said:**
> My understanding is that the LTS to LTS upgrade won't be available until 16.04's first point release in July.

[http://www.omgubuntu.co.uk/2016/04/how-to-upgrade-ubuntu-14-04-to-ubuntu-16-04-lts](http://www.omgubuntu.co.uk/2016/04/how-to-upgrade-ubuntu-14-04-to-ubuntu-16-04-lts)You're correct that 14.04 LTS users won't *normally *be notified until 16.04.1 is released, but if you read further in the article it details a method that is supposed to get the upgrade notification to appear now. This doesn't seem to work, at least in Lubuntu.

---

### Post by BazBear on 2016-04-27
> **danielsender said:**
> On a legacy HP pavilion with 14.04 I type 'sudo do-release-upgrade' and I get back the message saying that there are no new versions available. I understand that 16.04 has already been released. Is there anything that should be edited?

Thanks.I found the command we are looking for in this thread [http://ubuntuforums.org/showthread.php?t=2322163](http://ubuntuforums.org/showthread.php?t=2322163)

```
sudo do-release-upgrade -d
```

[COLOR=#ff0000]Needless to say, there's probably good reasons why LTS releases don't offer an upgrade until the first point release of the next LTS, even if those reasons are just to be extra cautious that they won't hose a crap load of production machines before most of the bugs are ironed out.[/COLOR]

---

### Post by grahammechanical on 2016-04-27
Do not run do-release-upgrade -d unless you want to upgrade to the development release. The -d switch = development release.

And although I ran Xenial Xerus (16.04) as my daily driver all through its 26 weeks development period and I am now running Yakkety Yak (16.10) and will continue to use it as my daily driver for the next 26 weeks I would not risk upgrading a production machine with 14.04 on it to Yakety Yak using that command.

I might upgrade from 16.04 to 16.10 development version using that command but I would not use that command on 14.04 or 15.10. Not without keeping my fingers & toes crossed.

> 14.04 LTS to LTS upgrades will be enabled with the 16.04.1 LTS point release, in approximately 3 months time. 

To upgrade on a desktop system: 



[LIST]
[*]Open the "Software & Updates" Setting in System Settings. 
[*]Select the 3rd Tab called "Updates". 
[*]Set  the "Notify me of a new Ubuntu version" dropdown menu to "For any new  version" if you are using 15.10, set it to "long-term support versions"  if you are using 14.04 LTS. 
[*]Press Alt+F2 and type in "update-manager" (without the quotes) into the command box. 
[*]Software Updater should open up and tell you: New distribution release '16.04 LTS' is available. 
[*]Click Upgrade and follow the on-screen instructions. 
[/LIST]


The instructions should work for 15.10 to 16.04 upgrades. But will not work for 14.04 to 16.04 upgrades because of the statement made at the beginning of the quote.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

---

### Post by BazBear on 2016-04-27
> **grahammechanical said:**
> Do not run do-release-upgrade -d unless you want to upgrade to the development release. The -d switch = development release.

And although I ran Xenial Xerus (16.04) as my daily driver all through its 26 weeks development period and I am now running Yakkety Yak (16.10) and will continue to use it as my daily driver for the next 26 weeks I would not risk upgrading a production machine with 14.04 on it to Yakety Yak using that command.

I might upgrade from 16.04 to 16.10 development version using that command but I would not use that command on 14.04 or 15.10. Not without keeping my fingers & toes crossed.
I test ran it and it indeed was going to upgrade to Xenial, I simply closed it before it actually completed downloading anything. It is my understanding that Trusty will treat Xenial as a development release until 16.04.1 is released.

---

