---
title: "upgrade question"
date: 2011-09-17
forum: Installation &amp; Upgrades
---

### Post by timmyhiggy on 2011-09-17
When I saw 11.04 I was initially a bit scared of unity, as I didn't realise it would move out of the way when you fullscreen something!
I tried it recently on someone else's computer and thought it was great and realised I was being stupid.
I have an up to date version of 10.10, should "apt-get upgrade" still work, or is it too far down the line?

---

### Post by Hakunka-Matata on 2011-09-17
> **timmyhiggy said:**
> When I saw 11.04 I was initially a bit scared of unity, as I didn't realise it would move out of the way when you fullscreen something!
I tried it recently on someone else's computer and thought it was great and realised I was being stupid.
I have an up to date version of 10.10, [COLOR=Red]should "apt-get upgrade" still work[/COLOR], or is it too far down the line?

sudo apt-get update
sudo apt-get upgrade

will get you the latest updates to your current Release.

---

### Post by Old_Grey_Wolf on 2011-09-17
The command "sudo apt-get upgrade" does not upgrade you to the next release, it only upgrade packages within the currently installed release.

If you are using 10.10 then go to the menu System > Administration > Update Manager. Then click the settings button, you will be asked for your password. Then look for the "Show new distribution releases:" and make sure that Normal releases is selected. Click the Close button.

You should now see an option in Update Manager to upgrade to 11.04.

You can do this from the command line by entering the following commands:
```
sudo apt-get install update-manager-core

sudo do-release-upgrade
```

---

