---
title: "trying to upgrade from 12.04.5 to 14.04.4"
date: 2016-04-13
forum: Installation &amp; Upgrades
---

### Post by ctm2 on 2016-04-13
I'm genuinely perplexed. I've done 12.04->14.04 a number of times already, but I have this one server that's being absolutely stubborn.  To recap, this is what I've done so far:

-- checked apt/sources.list and sources.list.d to make sure no third party repositories in place
-- backed things up :-)

OK, so
```
apt-get update
apt-get dist-upgrade
(reboot)
apt-get install update-manager-core
do-release-upgrade
```

and all I get with that is:
```
# do-release-upgrade
Checking for a new Ubuntu release
No new release found

```
huh?

So, 
```
# grep -i prompt /etc/update-manager/release-upgrades
# Default prompting behavior, valid options:
Prompt=lts
```

that's okay. And
```
# lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise
```

okay... hrm.
```
# uname -r
3.2.0-101-generic
```

Is this some kind of kernel issue? That's a pretty old kernel there at this point, but I thought the *point* of LTS to LTS was to make the upgrades between each easy...!
I've googled around and while I see that there's been issues with 12.04->14.04 (though mostly earlier versions of the presently latest 12.04/14.04 versions), none of the suggestions I've come across have worked so far. (I have done do-release-upgrade -d since I have Prompt=lts specified, but that didn't do anything either).

So I'm stumped. Any additional ideas or insight as to what's going on? I suppose I can do a clean install, but now I'm plain annoyed and want to know what's going on... could be a tall order, of course, ha ha...

---

### Post by jdehart1 on 2016-04-13
I'm having a similar problem trying to use:
> do-release-upgrade
Checking for a new Ubuntu release
No new release found

And I've tried 

> do-release-upgrade -d
Checking for a new Ubuntu release
No new release found

> cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.5 LTS"

---

### Post by ctm2 on 2016-04-13
Keep in mind that the -d option will update to the latest development version, unless you have set things in _/etc/update-manager/release-upgrades_ to "lts" (see my grep stmt above). 

I'm starting to wonder if 14.04.4 is too new yet or something? It was released two months ago. (cf [https://lists.ubuntu.com/archives/ubuntu-announce/2016-February/000205.html](https://lists.ubuntu.com/archives/ubuntu-announce/2016-February/000205.html))

---

### Post by jdehart1 on 2016-04-13
Yes, I've tried "lts" and "normal" and it is always the same: "No new release found."

---

### Post by jdehart1 on 2016-04-14
I've gotten mine to find a new release now. I needed to reboot. I'm guessing there
was an update that needed a reboot to complete and maybe until that finished it couldn't
do a release upgrade.

---

### Post by ctm2 on 2016-04-21
> **jdehart1 said:**
> I've gotten mine to find a new release now. I needed to reboot. I'm guessing there
was an update that needed a reboot to complete and maybe until that finished it couldn't
do a release upgrade.

Well to follow up (I had already tried rebooting and no dice), I logged in today, did an update/dist-upgrade and tried do-release-upgrade and YAY SUCCESS.  >.<  So I dunno.  I did nothing other than the update/dist-upgrade between my original note and now... go figure.

---

