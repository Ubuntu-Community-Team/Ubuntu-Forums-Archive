---
title: "Upgrade 6.06 to 8.04 Failing from console"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by pdragon04 on 2008-05-09
Decided to try and upgrade my 6.06 server to 8.04 today and haven't had any luck. It's giving me the following error:

root@server:~# do-release-upgrade -d
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'hardy.tar.gz'
authenticate 'hardy.tar.gz' against 'hardy.tar.gz.gpg'
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 56, in ?
    fetcher.run()
  File "/usr/lib/python2.4/site-packages/UpdateManagerCore/DistUpgradeFetcherCore.py", line 183, in run
    self.runDistUpgrader()
  File "/usr/lib/python2.4/site-packages/UpdateManagerCore/DistUpgradeFetcherCore.py", line 148, in runDistUpgrader
    os.execv(self.script,args)
OSError: [Errno 13] Permission denied


I've run "apt-get update" and "apt-get upgrade" and everything is up to date. The server has run absolutely fine for several years now, so not sure what's wrong. Anyone have any ideas? Tried asking in #ubuntu-server, but had them stumped there. Really trying to avoid a reload from scratch.

---

### Post by Pumalite on 2008-05-09
You might want to try this:

sudo sed -i 's/dapper/hardy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

I haven't tried it myself, but it should work

---

### Post by pdragon04 on 2008-05-09
I really do appreciate the help, but if anyone could confirm this is works, and why I'm getting the error I am, I'd appreciate it. This is a live server I'm upgrading. I've got everything backed up of course and could recover with a clean install. Would just MUCH longer than upgrading and waste a lot of time.

---

### Post by pdragon04 on 2008-05-09
Someone else in IRC was having similar upgrade problems, but with different errors. Bug was reported.

[https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/228849](https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/228849)

---

