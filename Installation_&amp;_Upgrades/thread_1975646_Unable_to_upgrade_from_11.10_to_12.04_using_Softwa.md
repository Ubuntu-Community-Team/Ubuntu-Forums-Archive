---
title: "Unable to upgrade from 11.10 to 12.04 using Software Up to Date"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by taro4cycle on 2012-05-07
I am trying to upgrade my desktop from Ubuntu 11.10 to 12.04 using Software Up to Date. When I click the Upgrade button I am presented with a Release Notes window so I click Upgrade. I am then prompted for a password for the system. I type in my password and click OK. The dialog box disappears. I wait for several seconds and nothing happens. 

At this point, probably something failed, but I don't know where the error logs are. I'm assuming they're somewhere in /var/log. 

I have applied all other updates for 11.10. I understand that the servers may be busy, so I'm willing to wait until another time. I just want to know what may be the root cause. 

Incidentally, I found a post somewhere suggesting that I can do the system upgrade using the command sudo do-release-upgrade -d. When I do this, I don't see any error messages and it appears that I can go ahead using this method. However, I'd like to do the upgrade using the UI.

I can provide more details on my hardware system if that help, as I built it up myself. 

Below are some other information:

$ lsb_release -a
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

$ uname -a
Linux xyz 3.0.0-19-generic #33-Ubuntu SMP Thu Apr 19 19:05:14 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Thanks.

Taro

---

### Post by vVvSHADOWvVv on 2012-05-07
> **taro4cycle said:**
> I am trying to upgrade my desktop from Ubuntu 11.10 to 12.04 using Software Up to Date. When I click the Upgrade button I am presented with a Release Notes window so I click Upgrade. I am then prompted for a password for the system. I type in my password and click OK. The dialog box disappears. I wait for several seconds and nothing happens. 

At this point, probably something failed, but I don't know where the error logs are. I'm assuming they're somewhere in /var/log. 

I have applied all other updates for 11.10. I understand that the servers may be busy, so I'm willing to wait until another time. I just want to know what may be the root cause. 

Incidentally, I found a post somewhere suggesting that I can do the system upgrade using the command sudo do-release-upgrade -d. When I do this, I don't see any error messages and it appears that I can go ahead using this method. However, I'd like to do the upgrade using the UI.

I can provide more details on my hardware system if that help, as I built it up myself. 

Below are some other information:

$ lsb_release -a
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric

$ uname -a
Linux xyz 3.0.0-19-generic #33-Ubuntu SMP Thu Apr 19 19:05:14 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Thanks.

Taro


I have already posted a thread regarding this. The problem is that the distro upgrade will not accept the sudo password.

[http://ubuntuforums.org/showthread.php?t=1975606](http://ubuntuforums.org/showthread.php?t=1975606)

&#7780;&#11367;&#480;&#7430;&#336;&#412;
shadowsgovernment.com

---

### Post by taro4cycle on 2012-05-07
[QUOTE=vVvSHADOWvVv;11915318]I have already posted a thread regarding this. The problem is that the distro upgrade will not accept the sudo password.

[http://ubuntuforums.org/showthread.php?t=1975606](http://ubuntuforums.org/showthread.php?t=1975606)

Hi, thanks for your comment. I never got a message like "invalid password". Did you see this in a dialog box or in a log file?

---

