---
title: "'do-release-upgrade' from 12.04 LTS finds no new release"
date: 2017-01-12
forum: Installation &amp; Upgrades
---

### Post by rst-alum on 2017-01-12
I'm belatedly trying to upgrade my 12.04 LTS machine to 14.04 LTS, which I think is supposed to be supported. (And in fact, /etc/motd at one point was updated to note that a new release was available.)

However, when I try 'do-release-upgrade', it tells me 'No new release found'.  I could just do a '1,$s/precise/trusty/' in /etc/sources.list{,.d/*}, follow with
"apt-get update; apt-get upgrade; apt-get dist-upgrade" and hope for the best, but that ... makes me nervous.

(To add to the confusion, this is an older Dell Sputnik machine, with 'precise-dell' and 'precise-oem-sp1' in the sources. trusty-dell exists, but so do a plethora of more specific trusty-dell-foos.)

Any help for the perplexed?

---

### Post by deadflowr on 2017-01-12
Look in the file /etc/update-manager/release-upgrades
if the line says Prompt=normal, it needs to be changed to Prompt=lts.
I do not think  there is a normal for 12.04 anymore, which would be to 12.10.

You then need to re-run a sudo apt-get update,
After that do-release-upgrade should run and offer 14.04.

---

### Post by rst-alum on 2017-01-12
It had somehow got set to 'Prompt=never'. Thanks!

---

