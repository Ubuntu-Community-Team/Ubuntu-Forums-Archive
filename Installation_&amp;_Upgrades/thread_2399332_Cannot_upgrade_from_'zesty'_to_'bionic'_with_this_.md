---
title: "Cannot upgrade from 'zesty' to 'bionic' with this tool"
date: 2018-08-24
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2018-08-24
Ubuntu has told me that software updates are no longer provided for 17.04, and that to stay secure I should upgrade, but when I hit the upgrade button, after the upgrade tool downloads, an error is output:

```
Cannot upgrade from 'zesty' to 'bionic' with this tool
```

I assume the problem is that this tool does not account for the edge case of those missing an upgrade.

Must I first upgrade to 16.10, and if so can you please tell me how to do this?

---

### Post by Dáire Fagan on 2018-08-24
Some things I have tried:

> dusf@contraption:~$ sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autorem[sudo] password for dusf: 
Hit:1 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) zesty InRelease
Hit:2 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) zesty InRelease     
Err:3 [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) zesty-getdeb InRelease                  
  Could not connect to archive.getdeb.net:80 (144.76.200.19). - connect (111: Connection refused)
Hit:4 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) zesty-updates InRelease            
Hit:5 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) zesty-security InRelease           
Hit:6 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) zesty InRelease        
Hit:7 [http://ppa.launchpad.net/papirus/papirus/ubuntu](http://ppa.launchpad.net/papirus/papirus/ubuntu) zesty InRelease         
Hit:8 [http://ppa.launchpad.net/plt/racket/ubuntu](http://ppa.launchpad.net/plt/racket/ubuntu) zesty InRelease              
Hit:9 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) zesty InRelease           
Hit:10 [http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu) zesty InRelease
Hit:11 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) zesty InRelease       
AppStream system cache was updated, but problems were found: Metadata files have errors: /var/cache/app-info/xmls/fwupd.xml
Reading package lists... Done
W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/zesty-getdeb/InRelease](http://archive.getdeb.net/ubuntu/dists/zesty-getdeb/InRelease)  Could not connect to archive.getdeb.net:80 (144.76.200.19). - connect (111: Connection refused)
W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh-cache > /dev/null; fi'
E: Sub-process returned an error code




I also input update-manager -cd, which outputs the error:
> 
'Failed to download repository information. Check your Internet connection'.

> dusf@contraption:~$ cat /etc/apt/sources.list## EOL upgrade sources.list# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty-updates main restricted universe multiverse 
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty-security main restricted universe multiverse




---

### Post by Impavidus on 2018-08-24
The upgrade tool is designed to upgrade your system from 17.04 to 17.10, but not to 18.04. A tool to upgrade from 17.04 to 18.04 was never made, as 17.04 had already reached end-of-life when 18.04 was released. So your options are either to upgrade to 17.10, then to 18.04, but this is a bit hard, slow and unreliable, as 17.10 has also reached end-of-life. Or you can do a fresh install of 18.04, which is the recommended option.

---

### Post by Dáire Fagan on 2018-08-24
> **Impavidus said:**
> The upgrade tool is designed to upgrade your system from 17.04 to 17.10, but not to 18.04. A tool to upgrade from 17.04 to 18.04 was never made, as 17.04 had already reached end-of-life when 18.04 was released. So your options are either to upgrade to 17.10, then to 18.04, but this is a bit hard, slow and unreliable, as 17.10 has also reached end-of-life. Or you can do a fresh install of 18.04, which is the recommended option.

I would really prefer not to do a fresh install, as I have a very custom setup involving LUKS encryption on specific partitions, something which the installer for some reason still does not offer (options I last checked are encrypt everything in one large partition install, or just the home partition). It could take me days to get everything working correctly, and as so often with Ubuntu upgrades and installs, I fear something will go wrong.

How is upgrading to 17.10, and then to 18.04 unreliable? Surely most people upgraded from 17.04 to 17.10, and then on to 18.04? Can I not just do what they did?

---

### Post by Impavidus on 2018-08-24
Here is a guide on end-of-life upgrades: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
Don't forget to make backups and be prepared for a fresh install if things go wrong

Upgrades are always less reliable than fresh installs, double upgrades quadratically so. Although I had no problems at all upgrading from 17.04 to 17.10 and six months later to 18.04.

---

### Post by oldos2er on 2018-08-24
> **dusf said:**
> How is upgrading to 17.10, and then to 18.04 unreliable? 

Because 17.10 is also EOL.

I would make a full system backup before upgrading.

---

