---
title: "upgrade from 8.10 to 9.4"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by shijumic on 2011-07-15
Hi All,

I am trying to upgrade my system after a long time. I would like to upgrade to 10.10 or 11.4 from 8.10. I am a newbie to ubuntu. I did the following things.

 lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 8.10
Release:    8.10
Codename:    intrepid

Note:I am using a company proxy to connect to internet

1. I updates the /etc/apt/sources.list with the following
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) intrepid-proposed main restricted universe multiverse2. Ran 'sudo aptitude update && sudo aptitude safe-upgrade' and succeded

3. When I ran 'sudo do-release-upgrade' , it hangs at 'Updating repository information' stage. Whrn I tried ' tail -f /var/log/dist-upgrade/main.log' - it is hung at the following step for a while

DEBUG url_downloadable: [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release)

When I tried this yesterday it was stuck at this stage and aborted like below 
, E:Some index files failed to download, they have been ignored, or 
old ones used instead. 

Restoring original system state

Aborting
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Is is some bugs with url_downloadable when I am using a proxy, if so how I can fix that? or is there any way for me to skip the 'Updating repository information' from the upgrade and move on. I am stuck at this stage. Would someone help me?

Thanks,
Shijumic

---

### Post by oldos2er on 2011-07-16
I suggest you do a fresh install of 10.10 or 11.04. Not only is 8.10 end-of-life, but 9.04 and 9.10 are too.

---

