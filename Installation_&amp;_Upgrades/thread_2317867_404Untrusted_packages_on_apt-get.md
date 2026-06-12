---
title: "404/Untrusted packages on apt-get"
date: 2016-03-20
forum: Installation &amp; Upgrades
---

### Post by joe_cool22 on 2016-03-20
Hi, I'm very new to Ubuntu, so I respectfully ask for your patience. When I try to do apt-get install, apt-get upgrade or apt-get update, I'm getting errors like the following:

```
Err http://security.ubuntu.com saucy-security/main Sources
  404  Not Found [IP: 2001:67c:1360:8c01::19 80]

And the associated warning:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/saucy-security/main/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::19 80]


```

I'm still running 13.10, so that might explain something. Isn't one of those commands meant to update the OS as well as several other things? Right now I'm trying to install the .deb from here:

[http://blogs.unity3d.com/2015/08/26/unity-comes-to-linux-experimental-build-now-available/](http://blogs.unity3d.com/2015/08/26/unity-comes-to-linux-experimental-build-now-available/)

And I'm getting similar errors. Also, there's a dependency on lib32stdc++6, and it seems to have the same kinds of errors there as well.

Thanks for your patience.

---

### Post by westie457 on 2016-03-20
Welcome to UF.

The information on this page should help you. [https://help.ubuntu.com/community/TrustyUpgrades](https://help.ubuntu.com/community/TrustyUpgrades)
Then you might be able to install the .deb.

Be aware that various changes in packages from 13.10 to 14.04 may mean breakage to your system.

Back-up your important data first and be prepared for doing a clean install of 14.04.

If you want to try the upgrade using the terminal look here. [http://askubuntu.com/questions/5763/upgrading-from-the-command-line](http://askubuntu.com/questions/5763/upgrading-from-the-command-line)

---

### Post by grahammechanical on 2016-03-20
Ubuntu 13.10 reached end of life 17th July 2014.

As is normal practice the software repositories for 13.10 were closed. It would have happened a long time ago. And that is why you are getting the "404 Not Found." message. The URLs to the repositories are now broken links. So, you are getting the standard internet broken link message.

Untrusted packages usually refers to software that we install from places other than the Ubuntu repositories. It is up to you if you want to trust the authors of that software.

Do a fresh install of Ubuntu 14.04.4 or 15.10 and upgrade to 16.04 by the end of summer or 16.04 when it is released at the end of April (supported for 5 years).

Regards

---

