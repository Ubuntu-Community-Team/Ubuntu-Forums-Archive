---
title: "How to Upgrade from Edgy Eft 6.10 ------&gt; Fiest Fawn 7.04 (Working Method)"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by SFHasan on 2007-04-19
Hello All,

I searched around for my query for a while, but was not able to find a concrete working solution. Instead there were varied expereince and advices about how to go for the upgrade tp Feisty Fawn 7.04. I decided to put it up over here for the Ubuntu Gurus to suggest a solution.

My hardware configuration is as follows ;

HP Pavillion Laptop Dv1000, Celeron 1.7 Ghz, 512MB RAM, 80GB HardDisk and the usual peripherals which are always a part of the package. I am running Edgy Eft Ubutu 6.10 and have all the necessary software installed (with some Beryl Eye Candy too) and all seems to be working just fine.

I just wanna know that what is the easiest and reliable method of upgrading my system to Ubuntu 7.04 Feisty Fawn, wihout losing any of my existing programs / configuration / data files. Whether should I use the 'Update Manager" method or should I run a clean boot from the bootable CD of 7.04 and it will give me an option to upgrade my existing installation.

Any of you folks out there got a similar scenario and in case can give me a working suggestion, I would be grateful. Since instead of experimenting and losing my existing configuration and then again spending hours to download and setup everything again according to the requirements, it is better to learn from other's experiences.

Thanks in advance for co-operation and taking time to read my post.

Best Regards,
S.F.Hasan.

---

### Post by mority on 2007-04-19
I didn't have the time to try an upgrade from Edgy to Feitsy so far. But I upgraded three boxes from Dapper to Edgy back then.
First I tried the more "official" method with 'gksu -c update-manager' or something like that. Well, the update-manager crashed with a fatal error due to a bug in some pre- or post-install script of the nessus package and left my system in a horrible state.
After that experience I used the classy Debian style method of modifying sources.list and running 'aptitude update && aptitude upgrade'. That worked on two boxes absolutely perfectly.

---

### Post by Calash on 2007-04-19
I did a successful upgrade last night by using update-manager -c -d

Let it run over night (Bad idea, as it paused waiting for my input a couple of times.  Didn't break anything, just annoying :)), rebooted when it was done and everything came back up.

---

### Post by mh114 on 2007-04-19
I'm going to do the upgrade right after writing this, since the update manager has picked up the new release.. (running on Edgy atm).. Hopefully everything will work out.. :)

---

### Post by Kevkill on 2007-04-19
I put a posting up on my blog a while back on how to do this. [www.ubnoobie.wordpress.com](www.ubnoobie.wordpress.com)
Hope this helps.

-Kev

---

### Post by mh114 on 2007-04-19
Yay, the upgrade worked perfectly! :) I have yet to try 3d effects (I had beryl before working after some fighting - I have Radeon 9600 Pro.. :P)

---

### Post by Chiv15 on 2007-04-22
I've tried updating to fiest a couple of times today.  During the first step of the upgrade, I keep getting this message:
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz) Sub-process gzip returned an error code (1)

Any help with this problem?

I've only had ubunto for about a week,  so I have no idea where to begin

---

### Post by moldyclint on 2007-04-22
> **Chiv15 said:**
> I've tried updating to fiest a couple of times today.  During the first step of the upgrade, I keep getting this message:
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz) Sub-process gzip returned an error code (1)

Any help with this problem?

I've only had ubunto for about a week,  so I have no idea where to begin

I've had a not entirely similar error....

Failed to fetch http://mirror.noreply.org/pub/tor/dists/<edgy>/main/binary-i386/Packages.gz 404 Not Found

Though the file seems to be there....although "edgy" doesn't have the <> on the site....  Any work around for this?  Anybody?

Thanks....

---

### Post by ..Ayla.. on 2007-04-23
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

```
http://mirror3.ubuntulinux.nl/dists/edgy/Release.gpg: Connection failed
http://mirror3.ubuntulinux.nl/dists/edgy/freenx/i18n/Translation-en_GB.bz2: Connection failed
http://mirror3.ubuntulinux.nl/dists/edgy/freenx/binary-i386/Packages.gz: Connection failed
```

W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA


Any idea what to do??  	[-o<

:mrgreen:

---

### Post by jkrumm on 2007-04-25
> **moldyclint said:**
> I've had a not entirely similar error....

Failed to fetch http://mirror.noreply.org/pub/tor/dists/<edgy>/main/binary-i386/Packages.gz 404 Not Found

Though the file seems to be there....although "edgy" doesn't have the <> on the site....  Any work around for this?  Anybody?

Thanks....




I had the same failed to fetch error and fixed it by messing with the Software Sources utility under System/Administration. I unchecked the Automatix server (if you have Automatix installed) and I first switched to the U.S. Server, tried it (didn't work) then to Main Server. It did some kind of update then and that fixed everything. After that, the upgrade went smoothly.

---

