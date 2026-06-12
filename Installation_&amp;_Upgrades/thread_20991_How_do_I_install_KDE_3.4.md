---
title: "How do I install KDE 3.4??"
date: 2005-03-19
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-03-19
I have just installed KDE 3.2.3 through synaptic. But now I just read that there is a KDE 3.4 but I cannot find that in synaptic. How do I upgrade my current version of KDE to 3.4??

---

### Post by emperor on 2005-03-19
KDE 3.4 is in Hoary! So you will need to update to Hoary or there may be a backport available for Warty, not sure. I did a apt-get update/upgrade after editing my repo list. Hoary fixs more things than it breaks!

---

### Post by bigblop on 2005-03-19
How do I see which Ubuntu I have?? And what is Hoary and backport??

---

### Post by emperor on 2005-03-19
Warty. is 4.10, 2.6.8 kernel, kde 3.2
Hoary is 5.04, 2.6.10 linux kernel and kde 3.4 is the only choice.

Sounds like you are running Warty as Hoary is not actually released yet, won't be until April 5th. Then number after the release name above is the date of the release, month and then the day. However you can savely upgrade now, you just need to upgrade your packages frequently with the synaptic package manager or apt-get from a level 2 or 3 boot, the recovery choice from grub.

check your "repo" source listing in: /etc/apt/sources.list
in xterm type: cat /etc/apt/sources.list

I would not recommend "backports" to a new user, you would be better off to just
upgrade to Hoary. see: [http://www.ubuntuguide.org/#upgradewartytohoary]("http://www.ubuntuguide.org/#upgradewartytohoary")

Backports are when a newer package (like KDE 3.4) in a new distro release (like Hoary) is created for a previous distribution release, in this case Warty..

Here's the backport link:
[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

