---
title: "Upgrade from 8.0.4 LTS"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by okohll on 2011-03-16
Hello, what is the recommended way of upgrading to the latest version from hardy? My exact version is

root@gtwmbackup:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.4 LTS
Release:	8.04
Codename:	hardy

and I am on AMD64.

Trying a
do-release-upgrade
upgrade to intrepid fails because intrepid is no longer in 
[http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)

, even when I replaced [http://archive.ubuntu.com](http://archive.ubuntu.com) with [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) in
/var/lib/update-manager/meta-release

Commenting out intrepid and jaunty (unsupported) in the meta-release file attempts an upgrade to karmic, which fails with


Invalid package information 

After your package information was updated the essential package 
'ubuntu-minimal' can not be found anymore. 
This indicates a serious error, please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report.

---

### Post by coffeecat on 2011-03-16
You could have gone directly from 8.04 to 10.04. See here:

[https://help.ubuntu.com/community/LucidUpgrades#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS](https://help.ubuntu.com/community/LucidUpgrades#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS)

But your attempts to upgrade to intermediate obsolete versions may have complicated things.

---

### Post by mörgæs on 2011-03-16
Have you tested using a live CD that 10.04 or 10.10 work well on your system?

---

### Post by okohll on 2011-03-16
No I haven't, it's a remotely hosted server accessed over SSH. The hosts should be able to tell me if it's supported, I'll ask them.

Re coffeecat, that's what I tried originally, following the instructions under Upgrade for Ububntu Servers on that page. The response was

root@gtwmbackup:~# do-release-upgrade
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
extracting 'intrepid.tar.gz'
Failed to extract
Extracting the upgrade failed. There may be a problem with the network or with the server. 

- it tried to upgrade to intrepid even though it's marked as not supported.

---

### Post by okohll on 2011-03-16
Oops, sorry I made a mistake, I had marked Prompt=normal rather than Prompt=lts. Trying the latter now, it looks like it's getting further.

---

### Post by coffeecat on 2011-03-16
> **okohll said:**
> Oops, sorry I made a mistake, I had marked Prompt=normal rather than Prompt=lts. Trying the latter now, it looks like it's getting further.

I wondered why your system was trying to download intrepid.tar.gz. Good luck with that.

There's a misleading miscode in the contents links on the Lucid Upgrades community documentation page. If you click on "Network Upgrade for Ubuntu Servers" under the Upgrade from 8.04 LTS to 10.04 LTS heading, it takes you to the Upgrade Kubuntu 9.10 to 10.04 instructions. I wonder if that misled you - not your mistake at all.

---

### Post by rizky_ghardoe on 2011-03-16
have you tried the live CD 10.10??

---

### Post by mörgæs on 2011-03-17
By the way and off topic: Though last poster could sound like me, it is not. I only have one user name here.

---

### Post by okohll on 2011-03-17
Thanks, all working now. The only thing was the new kernel didn't get installed for some reason during the upgrade but my hosting company sorted that out.

---

### Post by mörgæs on 2011-03-17
Good, please mark the thread 'solved'.

---

