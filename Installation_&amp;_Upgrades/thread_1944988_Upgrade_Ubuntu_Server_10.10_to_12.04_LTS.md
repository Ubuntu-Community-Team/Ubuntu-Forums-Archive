---
title: "Upgrade Ubuntu Server 10.10 to 12.04 LTS"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by alliance1975 on 2012-03-22
I have Ubuntu 10.10 server installed on a small home server used for raid backups and as a print server. I manage it from my Arch desktop through Webmin. All works very well. My reading of some forums suggests I should have installed 10.04 server as it was an LTS version. Those same readings suggest that to upgrade to 12.04 server LTS will require single step upgrades to 11.04 then to 11.10 and finally to 12.04 LTS.

I plan to start soon to see if the intermediate upgrades work and do a final upgrade 12.04 soon after it becomes available.

Any warnings or suggestions would be helpful.

As I recall I never created a root password, I just entered an initial user name and password and performed all admin work via sudo. Should I establish a root password and do all upgrades from root?

---

### Post by oldfred on 2012-03-22
Ubuntu does not need a root password and  on the forum we discourage use of a root password. Just use sudo.

Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://xkcd.com/149/](http://xkcd.com/149/)

I have only done desktops, but after upgrades from 6.06 to 9.04 and then a clean install of 9.10 as I was converting from 32bit to 64bit, I now suggest clean installs. You do need good backups, but it does an automatic houseclean of old stuff like logs, old apps etc.

I also like to test new install before old install is gone. I have several drives now, and just install the new version to a new 25GB / (root) partition. Then if I forgot to backup some setting somewhere I can still go back and get it.

---

### Post by darkod on 2012-03-22
No, you don't need intermediate upgrades. Since it is LTS version it can upgrade directly to the next LTS, of course after it is officially released.

The LTS server versions are configured by default to upgrade to the next LTS, not normal release.

EDIT: Sorry, I just noticed you have 10.10. I misread it as 10.04 which is also LTS. In this case you will need to upgrade version to version.

---

### Post by alliance1975 on 2012-03-22
Thank you darkod and oldfred, it is as I suspected. Perhaps a fresh install is what is needed. I dread that, but it will re-educate me on server/webmin.

The whole os is loaded on a 16gb flash card.

---

### Post by oldfred on 2012-03-22
Flash devices have dropped a lot in price recently. I would invest in another 16GB flash drive and install to that. Then you have a test environment and a working install.

---

### Post by alliance1975 on 2012-03-22
That is an excellent suggestion oldfred. Thank you. I will mark this thread solved.

---

### Post by frogotronic on 2012-04-02
> **darkod said:**
> No, you don't need intermediate upgrades. Since it is LTS version it can upgrade directly to the next LTS, of course after it is officially released.

The LTS server versions are configured by default to upgrade to the next LTS, not normal release.

EDIT: Sorry, I just noticed you have 10.10. I misread it as 10.04 which is also LTS. In this case you will need to upgrade version to version.

I don't think so...putting in a 12.04 liveCD into my 10.10 install gave me the option of UPGRADING.

Don't know about the server, but might also be the same.

- CH     ):P

---

### Post by darkod on 2012-04-03
> **cement_head said:**
> I don't think so...putting in a 12.04 liveCD into my 10.10 install gave me the option of UPGRADING.

Don't know about the server, but might also be the same.

- CH     ):P

You see, never tried that. :)

Come to think of it, the alternate cd was always offering that I think. It seems now the live cd is also doing it. I am not sure about the server cd also.

---

### Post by alliance1975 on 2012-04-10
@c_h, thank you for your reply. Using the live CD is an unexpected alternative. However, since it is a server and benefits other family members I went with the safe approach recommended by oldfred and purchased a second 16gb flash to establish the new 12.04 server and get it working. I will have the 10.10 in reserve if needed.

---

