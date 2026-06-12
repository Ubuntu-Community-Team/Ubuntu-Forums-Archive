---
title: "Ubuntu 11.04, Ubuntu 12.04.1, Upgrade"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by Odense on 2012-11-07
I am using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012.
I have my settings in the update manager set to only upgrade to the next LTS - but even if this has been available a long time I am not asked if I want to upgrade (I do get the updates to the 11.04 though.

I tried using the commands below - but with no result.

sudo rm -vf /var/lib/apt/lists/*
sudo apt-get update
sudo apt-get upgrade

So - how do I upgrade from Ubuntu 11.04 - the Natty Narwhal to Ubuntu 12.04.1 LTS
I know I can make a clean install - but I hope I can also go the upgrade route ?

---

### Post by snowpine on 2012-11-07
11.04 is not an LTS so you can't directly upgrade LTS to LTS.

I recommend to back up all your files, documents, settings to an external drive (better yet, 2 forms of backup!) and do a fresh install of 12.04.

---

### Post by Odense on 2012-11-07
I know I cannot do it in one go - but I am pretty sure it can be done in a few gos. and this is what I want to try - even though some might like a clean install better.
I know I can back up my files - but how do I back up my programs (and the extra packages I have added) and my settings ?

---

### Post by snowpine on 2012-11-07
Fresh reinstall is just one of your options; as you point out another option is an incremental "end of life" upgrade as described here:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

I think the first step would be to toggle the setting you mentioned in post #1, where you had set your system for LTS upgrades only (your next target, 11.10 is not an LTS).

---

### Post by Odense on 2012-11-08
Thanks - that worked :)
I was/am pretty sure I have tried toggling this setting before - but this time it worked right away :)
So - after getting classic instead of Unity with [http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
And setting the update back to only accept LTS I am ready for another year :)

---

