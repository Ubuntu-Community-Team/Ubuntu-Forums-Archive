---
title: "What happened to Edgy?"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by dchenbecker on 2008-05-28
I'm trying to do a do-release-upgrade on an Edgy box and when I run it I get a ton of 404 errors and it quits. I just checked

[http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/)

And edgy is gone! Dapper is still there, so I'm wondering what exactly happened...

Thanks,

Derek

---

### Post by 505 on 2008-05-28
Edgy was supported until 18 months after release. I guess it's time is up. Dapper is a LTS release (just as hardy), meaning it will get Long Term Support, being 3 years for the desktop and 5 for servers.

---

### Post by Slim Odds on 2008-05-28
If you don't want to upgrade annually (more or less) then you'd better stick with the LTS releases.

Edgy support ended 2008-04-25

---

### Post by dchenbecker on 2008-05-28
OK, is there any way for me to do an upgrade at this point? This server slipped through the cracks which is why it was still on Edgy.

Thanks,

Derek

---

### Post by LeoSolaris on 2008-05-28
Burn a copy of 8.04, and upgrade from it. You'll have to made sure the cd is on the sources list, but it should be.

Leo

---

### Post by Slim Odds on 2008-05-28
> **dchenbecker said:**
> OK, is there any way for me to do an upgrade at this point? This server slipped through the cracks which is why it was still on Edgy.

Thanks,

Derek


Try this: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by dchenbecker on 2008-05-28
Yeah, I'm just editing my sources.list to feisty and crossing my fingers. After that I can do a do-release-upgrade.

Thanks for the help!

Derek

---

### Post by toniturn on 2008-05-29
> **dchenbecker said:**
> Yeah, I'm just editing my sources.list to feisty and crossing my fingers. After that I can do a do-release-upgrade.


Did this work? I'm stuck with edgy on one of my servers, and can't use the recommended upgrade procedure

[URL="https://help.ubuntu.com/community/FeistyUpgrades#head-e471fe0c514bab31d4fac24a8a8fde382e8c7aaf"]https://help.ubuntu.com/community/FeistyUpgrades#head-e471fe0c514bab31d4fac24a8a8fde382e8c7aaf
[/URL]
because update-manager-core is not installed, and now I cannot install it from the edgy repository any longer.

Any input would be greatly appreciated!

Toni

---

### Post by dchenbecker on 2008-05-29
Yes, it worked for me. Just replace "edgy" in your /etc/apt/sources.list with "feisty", do an "aptitude update" and then "aptitude dist-upgrade". Once that's complete I restarted and then installed update-manager-core and did the normal do-release-upgrade.

Derek

---

