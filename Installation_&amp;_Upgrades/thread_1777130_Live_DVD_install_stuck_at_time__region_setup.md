---
title: "Live DVD install stuck at time / region setup"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by shnplr on 2011-06-07
Hi,

When performing a clean install of natty from Live DVD the screen freezes at the time /region setting (i.e. the "Where are you?" screen).

Is there any way to change which server the system performs it's look up to at install time?

Before starting another install I tried the following:

1. #sudo apt-get install ntp
2. #sudo gedit /etc/ntp.conf

<created a new server entry - commenting out all the others>

3. install from live DVD again but still hangs...

Note: 

a) If I just leave it, after a few (5?) minutes the install continues and the system time remains at New York time.

b) I notice there is another package ntpdate installed by default - is this what the install program is using?

typing "#sudo ntpdate" displays: 

<the time> ntpdate[2533]: no servers can be used, exiting


Thanks for any suggestions,

Paul

---

