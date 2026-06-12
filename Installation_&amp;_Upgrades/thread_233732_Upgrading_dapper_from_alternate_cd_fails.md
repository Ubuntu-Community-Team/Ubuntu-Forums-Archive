---
title: "Upgrading dapper from alternate cd fails"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by zxee on 2006-08-10
I'm on a dial up connection so upgrading from apt-get is not an option. 
The dapper install I have is a test release-the last one before it when final, but I wanted to try an upgrade from a more recent iso (I dl from free wifi w/my powerbook so I have the final release of 6.06).
The trouble is that while synaptic will use the cd, it pulls off about 300 pkgs+ but then it still wants to download-mostly security stuff-I believe. 
If I don't let it download the upgrade fails because of missing packages.:sad: 
I just saw that there is a point release out. If I go out and wardrive for that will it upgrade my system, or is there another way to do this? 
Thanks for any input.

---

### Post by zxee on 2006-08-10
I did check out the howto for cd upgrades here: [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)
Using apt-get it stills wants to dl 232MB

479 upgraded, 17 newly installed, 1 to remove and 0 not upgraded.
Need to get 232MB/464MB of archives.
After unpacking 236MB of additional disk space will be used.
Do you want to continue [Y/n]? n

---

### Post by confused57 on 2006-08-10
Here's an excellent "HowTo" upgrade using the alternate cd:
[http://psychocats.net/ubuntu/dapper.php](http://psychocats.net/ubuntu/dapper.php)

Edit:  I thought maybe the key would be commenting out(#) all the repositories, except the cd-rom?

---

### Post by zxee on 2006-08-10
Thanks for the reply. That guide is for upgrading from breezy to dapper.
I have a dapper testing install that I want to upgrade to the final release with the final release alternate cd.

---

### Post by zxee on 2006-08-11
I went out a captured the new release i.e 6.0.6.1 (alternate cd)
I then used it with synaptic. Synaptic still needs to download more packages however-probably too much for my pathetic connection. I tried to let it download anyway but I keep getting this:

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/d/dasher/dasher-data_4.0.2-0ubuntu3_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/d/dasher/dasher-data_4.0.2-0ubuntu3_all.deb)
  Error reading from server. Remote end closed connection


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mozilla-thunderbird/mozilla-thunderbird_1.5.0.5-0ubuntu0.6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mozilla-thunderbird/mozilla-thunderbird_1.5.0.5-0ubuntu0.6.06_i386.deb)
  Error reading from server. Remote end closed connection


 Does anyone know what's up with this? Thanks
Added: I was able to successfully download everything after a couple of tries and now my system is upgraded to:
:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper :D

---

