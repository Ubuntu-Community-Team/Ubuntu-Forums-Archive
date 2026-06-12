---
title: "Trouble upgrading Jaunty server to Karmic"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by number nine on 2011-06-08
Hello,

I have a dedicated server running Ubuntu-server Jaunty. As you know, this OS no longer has security updates. I'm trying to upgrade it to the latest LTS (Lucid) but first thing's first: I'm having trouble upgrading from Jaunty to Karmic.

Here's the problem. I get the following when I try do-release-upgrade:

```
$ sudo do-release-upgrade -d
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg'
tar: Removing leading `/' from member names

Reading cache

Checking package manager

Can not upgrade

An upgrade from 'jaunty' to 'lucid' is not supported with this tool.

```

I don't understand why do-release-upgrade is insisting on trying to upgrade to Lucid instead of Karmic. I'm using the "-d" switch (though the same message appears if I don't) and I have updated /etc/update-manager/release-upgrades with "Prompt=normal" :

```

$ more /etc/update-manager/release-upgrades
# default behavior for the release upgrader
#

[DEFAULT]
# default prompting behavior, valid options:
#  never  - never prompt for a new distribution version
#  normal - prompt if a new version of the distribution is available
#  lts    - prompt only if a LTS version of the distribution is available
Prompt=normal

```

I have also followed the instructions here but am having the same issue: [https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

Does anybody have any suggestions to force an upgrade to Karmic instead of Lucid? (And no, sadly, re-installing is *not* an option as this is a server with no direct physical access)

---

### Post by Joe of loath on 2011-06-08
What I tend to do, is to change the distribution name in /etc/apt/sources.list to what you want, and then run sudo apt-get update && sudo apt-get dist-upgrade.

---

### Post by number nine on 2011-06-09
That's certainly what I would have done in the Debian days but with Ubuntu I always assumed there was some kind of "magic" behind do-release-upgrade. Maybe not?

Oh well, I don't have much choice now so I'll upgrade the "old fashioned way" :D Thanks!

---

### Post by Joe of loath on 2011-06-09
Not sure, the Debian way has always worked for me :p

---

### Post by oldos2er on 2011-06-09
> **number nine said:**
> An upgrade from 'jaunty' to 'lucid' is not supported with this tool.

I don't understand why do-release-upgrade is insisting on trying to upgrade to Lucid instead of Karmic. 

Possibly because, as of April 30, 2011 Karmic is EOL too.

---

