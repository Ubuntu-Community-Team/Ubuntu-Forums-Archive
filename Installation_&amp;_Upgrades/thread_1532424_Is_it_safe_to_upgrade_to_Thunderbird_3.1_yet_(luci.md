---
title: "Is it safe to upgrade to Thunderbird 3.1 yet? (lucid)"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by f1r3br4nd on 2010-07-16
I notice the repository Thunderbird version is 3.0.5 but 3.1 is already released. I'm on 3.0.4 and it took me forever to find a compatible version of the Lightning extension, which I really need.

Now I am afraid to upgrade to anything older than 3.1 because it might break Lightning, and I'm afraid to upgrade to 3.1 because maybe there's a reason it's not in the official repository yet (and because who knows if the latest version of Lightning really is compatible with the latest version of Thunderbird). 

My question is, is anybody out there currently running Thunderbird 3.1 with the Lightning extension on Kubuntu or Ubuntu 10.04, AMD64? Have you found it to be stable?

Thanks.

---

### Post by irfanahmed on 2010-08-02
I have upgraded to 3.1.2pre from the PPA repository. I have found it to be stable so far. I was using 3.0.5 from the main repository with Lightning 1.0b2. 

Here is what I did.

[LIST=1]
[*]Took a backup of my profile in ~/.thunderbird
[*]Added the PPA repository ([Instructions]("https://edge.launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa"))
[*]Opened Synaptics Package Manager and marked Thunderbird 3.0.5 for uninstallation and clicked Apply
[*]Marked Thunderbird 3.1 for installation and clicked Apply
[/LIST]

Problems that I have noticed so far

[LIST=1]
[*]The link in /usr/bin/thunderbird-3.1 is broken. It points to ../lib/thunderbird-3.1.2pre/thunderbird when it should point to **../lib/thunderbird-3.1.2pre/thunderbird-3.1**
[LIST]
[*]Make the above change and thunderbird should come up
[/LIST]
[*]The initial start page shows a 404.
[/LIST]

Once you start the new thunderbird, it transfers the profiles and you get your mail and settings.

---

