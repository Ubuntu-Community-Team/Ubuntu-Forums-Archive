---
title: "How to rescue an old box"
date: 2012-04-18
forum: Installation &amp; Upgrades
---

### Post by satimis on 2012-04-18
Hi folks,

Ubuntu 9.04

I have an old box not running for years.  I just dig it out from the store room.  On running;

$ sudo aptitude update```

......
......
Err http://hk.archive.ubuntu.com jaunty/main Packages
  404 Not Found [IP: 91.189.92.180 80]
Err http://hk.archive.ubuntu.com jaunty/restricted Packages
  404 Not Found [IP: 91.189.92.180 80]
Err http://hk.archive.ubuntu.com jaunty/main Sources
  404 Not Found [IP: 91.189.92.180 80]
Err http://hk.archive.ubuntu.com jaunty/restricted Sources
  404 Not Found [IP: 91.189.92.180 80]
Err http://security.ubuntu.com jaunty-security/multiverse Packages
  404 Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com jaunty-security/multiverse Sources
  404 Not Found [IP: 91.189.92.167 80]
Err http://hk.archive.ubuntu.com jaunty/universe Packages
  404 Not Found [IP: 91.189.92.180 80]
Err http://hk.archive.ubuntu.com jaunty/universe Sources
  404 Not Found [IP: 91.189.92.180 80]
Err http://hk.archive.ubuntu.com jaunty/multiverse Packages
  404 Not Found [IP: 91.189.92.180 80]
Err http://hk.archive.ubuntu.com jaunty/multiverse Sources
  404 Not Found [IP: 91.189.92.180 80]
Err http://hk.archive.ubuntu.com jaunty-updates/main Packages
  404 Not Found [IP: 91.189.92.180 80]
Err http://hk.archive.ubuntu.com jaunty-updates/restricted Packages
  404 Not Found [IP: 91.189.92.180 80]
Err http://hk.archive.ubuntu.com jaunty-updates/main Sources
  404 Not Found [IP: 91.189.92.180 80]
Err http://hk.archive.ubuntu.com jaunty-updates/restricted Sources
  404 Not Found [IP: 91.189.92.180 80]
Err http://hk.archive.ubuntu.com jaunty-updates/universe Packages
  404 Not Found [IP: 91.189.92.180 80]
Err http://hk.archive.ubuntu.com jaunty-updates/universe Sources
  404 Not Found [IP: 91.189.92.180 80]
Err http://hk.archive.ubuntu.com jaunty-updates/multiverse Packages
  404 Not Found [IP: 91.189.92.180 80]
Err http://hk.archive.ubuntu.com jaunty-updates/multiverse Sources
  404 Not Found [IP: 91.189.92.180 80]
Reading package lists... Done   
```          

$ uname -a ```

Linux vm13 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

```

I expect to revive this box.  Please advise what shall I do?  TIA

B.R.
satimis

---

### Post by kc1di on 2012-04-18
hi,

You might want to give us the specs on that old box, processor type and speed amount of ram available ,etc.

the reason you get err 404 is because Ubuntu 9.04 has not been supported since Oct 2010 and it's repositories have been shutdown by now. 

If the old box can handle it try updating to 10.40 that will be supported for awhile yet. but not long.

---

### Post by satimis on 2012-04-18
> **kc1di said:**
> hi,

You might want to give us the specs on that old box, processor type and speed amount of ram available ,etc.

the reason you get err 404 is because Ubuntu 9.04 has not been supported since Oct 2010 and it's repositories have been shutdown by now. 

If the old box can handle it try updating to 10.40 that will be supported for awhile yet. but not long.

Hi,

Thanks for your advice.  The hardware has no problem.

RAM 4G
HD 600G
CPU AMD Phenon x2

Sorry I haven't mentioned this is a virtual PC.  Ubuntu9.04 is a client.  I have several clients running Ubuntu9.04 and several clients running Debian5.0.  All of them need to be upgraded.  I can't wipe them out because SugarCRM/R-project/mail server/webserver etc. are running on them.

I expect to upgrade them on latest ISO.  I did it before.  Please advise which ISO for LTS shall I download.  TIA

B.R.
satimis

---

### Post by Lars Noodén on 2012-04-18
Well, if it acting as a server, then download the server ISO.  That will be minimalistic.

Otherwise, if you want the lightest weight desktop, go with Lubuntu.  It uses LXDE, which is not demanding on system resources.

---

### Post by kc1di on 2012-04-18
> **satimis said:**
> Hi,

Thanks for your advice.  The hardware has no problem.

RAM 4G
HD 600G
CPU AMD Phenon x2

Sorry I haven't mentioned this is a virtual PC.  Ubuntu9.04 is a client.  I have several clients running Ubuntu9.04 and several clients running Debian5.0.  All of them need to be upgraded.  I can't wipe them out because SugarCRM/R-project/mail server/webserver etc. are running on them.

I expect to upgrade them on latest ISO.  I did it before.  Please advise which ISO for LTS shall I download.  TIA

B.R.
satimis

12.04 is the new LTS version - it will be released April 26th.

---

### Post by satimis on 2012-04-18
Hi all,

Thanks for your advice.

I'll wait for 12.04, the new LTS.  Meanwhile I'll upgrade Debian 5.0 to 6.0.  It'll take me some time


Hi Las,

Can I upgrade Ubuntu desktop to Lubuntu without affecting other software running on the former?  If YES, please advise how.  Pointers would be appreciated.  TIA

B.R.
satimis

---

### Post by Lars Noodén on 2012-04-19
> **satimis said:**
> Hi all,

Thanks for your advice.

I'll wait for 12.04, the new LTS.  Meanwhile I'll upgrade Debian 5.0 to 6.0.  It'll take me some time


Hi Las,

Can I upgrade Ubuntu desktop to Lubuntu without affecting other software running on the former?  If YES, please advise how.  Pointers would be appreciated.  TIA

B.R.
satimis


If you install the package 'lubunutu-desktop' it will give you Lubuntu in addition to whatever is already installed, which in this case is Ubuntu.  That will give you both.  It is possible to  remove things you are not using.  Also it is possible to switch over entirely to Lubuntu:
[http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

---

### Post by mastablasta on 2012-04-19
end of life can be upgraded: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
 
10.04 LTS is supported until april 2013
12.04 LTS will be supported until april 2017.

---

