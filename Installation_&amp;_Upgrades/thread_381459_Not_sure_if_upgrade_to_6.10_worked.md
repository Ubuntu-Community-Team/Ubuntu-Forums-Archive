---
title: "Not sure if upgrade to 6.10 worked?"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by The_Architect on 2007-03-10
I executed the 'gksu "update-manager -c"' command and saw that some updates were being downloaded after this I was prompted to restart my ststem which I did.
I was exepcting to see the newer versions of the Firefox, Evolution etc.. after my system restarted but I see the same old versions.

Is there something more that needs to be done?

---

### Post by Kateikyoushi on 2007-03-10
You could repeat it one more time, I had to do it two times to upgrade everything.

---

### Post by The_Architect on 2007-03-11
Oh boy!
Anyway I just logged out of Ubuntu and back to XP. I will switchover after sometime and check it out.

---

### Post by Kateikyoushi on 2007-03-11
This should tell you which release you are running.

```
cat /etc/lsb-release
```

---

### Post by The_Architect on 2007-03-11
That gives me the following
> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"


Also I tried "gksu update-manger -c" several times more but it says that my system is up to date.

What do I do to upgrade to edgy?

---

### Post by Kateikyoushi on 2007-03-11
Update manager did not work for me either (and recently for some other people either) so I went the other, not recommended way, and my system worked but I had to dist-upgrade more than one time.

Read here what other ways you could try to upgrade. [LINK]("https://help.ubuntu.com/community/EdgyUpgrades")

---

### Post by The_Architect on 2007-03-11
Yeah thats what I did too and it worked (just finished now).
Everything looks like it was upgraded now.
Thanks for all the help.

Is there anything else I need to do after this? ot is this it?

---

### Post by Kateikyoushi on 2007-03-11
This is it if the previous commands says you are uding edgy 6.1.

---

