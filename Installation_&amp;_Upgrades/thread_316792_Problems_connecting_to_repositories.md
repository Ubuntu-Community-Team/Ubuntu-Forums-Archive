---
title: "Problems connecting to repositories"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by jeffbarish on 2006-12-11
Starting about 9 days ago, I have been unable to connect to us.archive.ubuntu.com.  I get "Could not connect to us.archive.ubuntu.com" and "connection timed out" except at security.ubuntu.com.  I switched to a mirror at [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu).  It worked great once (last Thursday), but now I get "Cannot initiate the connection to mirrors.cat.pdx.edu" and "network is unreachable".  It's hard to believe that the Ubuntu archive has been down for 9 days, especially considering that I have seen only 1 other comment about difficulties connecting.  It's even harder to believe that two repositories could be down for a period of days.  Is it possible that there is something in my system that could be preventing me from connecting?  I have no trouble pinging either repository.  Is it possible that delays in my DSL connection are causing the problem?

---

### Post by taurus on 2006-12-11
Remove the "us." from all the lines with "us.archive.ubuntu.com" in /etc/apt/sources.list.  Then, run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by jeffbarish on 2006-12-11
Thanks.

I have 763 upgradable packages now.  I expect to have problems after doing such a large upgrade.  In the event the problems are serious, will I be able to get back to where I started by restoring /usr and /etc from a snapshot on an unused partition?

---

### Post by taurus on 2006-12-11
When was the last time you updated your machine?  And is it Dapper or Edgy that you are using?

---

### Post by jeffbarish on 2006-12-11
I did a clean install of Edgy from 6.10RC.  I've been updating continually, but I didn't notice until recently that the sources.list that came with 6.10RC specified dapper, not edgy.  When I changed the entries to edgy, I had 763 upgradable modules.  From your question, I suppose that my situation must be bad.  It took about 2 weeks to get everything working after the original installation, so I am hoping to avoid a reprise of that experience.  Nevertheless, if the upgrade is going to be a waste of time, I'd rather get started now on a fresh install of the true 6.10.

---

### Post by taurus on 2006-12-11
Well, there you have it.  You are running the beta and you want to upgrade to the stable of Edgy...  Probably won't break your system if you update it but always back up personal/important files if you're not sure.

---

### Post by jeffbarish on 2006-12-15
In case anyone is wondering, updating from 6.10RC to 6.10 (763 packages) did not work.  Adept had 39 packages that it could not install because of conflicts.  The system would no longer boot.  Restoring /usr and /etc did not make the system bootable.  I had to do a fresh installation of 6.10.  That installation did not go smoothly because of a bug in the installer (it doesn't recognize reiserfs).  It's been a rough week, but 6.10 is finally running.  It looks and runs better than 6.10RC, so at least I have something to show for all the effort.

---

