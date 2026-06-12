---
title: "impossible to upgrade to 13.10"
date: 2013-12-25
forum: Installation &amp; Upgrades
---

### Post by papilonaa on 2013-12-25
helo i have now a huge problem; i try to upgrade my ubuntu 13.04 to 13.10 and get always throught synaptic a error message, how and what do i manage the soruce in the synaptic? 
[ATTACH=CONFIG]248890[/ATTACH][ATTACH=CONFIG]248891[/ATTACH][ATTACH=CONFIG]248892[/ATTACH]
then i install by mistake waha-system-adjustments all.deb which U can download from forge, this did take over my source in synaptic and i cant get rid of it and can update and upgrade nothing more, what shall i do, thanks
```
dom@dom:~$ cat /proc/version
Linux version 3.8.0-35-generic (buildd@allspice) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #50-Ubuntu SMP Tue Dec 3 01:25:33 UTC 2013
dom@dom:~$ cat  /etc/lsb-release
DISTRIB_ID=WahaLinux
DISTRIB_RELEASE=7.2
DISTRIB_CODENAME=sarab
DISTRIB_DESCRIPTION="Waha Linux 7.2 Sarab"
dom@dom:~$ sudo apt-get update
[sudo] password for dom: 
Get:1 [http://sf.net](http://sf.net) sarab Release.gpg [490 B]
Hit [http://sf.net](http://sf.net) sarab Release
Ign [http://sf.net](http://sf.net) sarab Release
Ign [http://sf.net](http://sf.net) sarab/main i386 Packages/DiffIndex
Err [http://sf.net](http://sf.net) sarab/main i386 Packages                                                                                                                                         
  
Err [http://sf.net](http://sf.net) sarab/main i386 Packages                                                                                                                                         
  
Err [http://sf.net](http://sf.net) sarab/main i386 Packages                                                                                                                                         
  
Ign [http://sf.net](http://sf.net) sarab/main Translation-en_US                                                                                                                                     
Ign [http://sf.net](http://sf.net) sarab/main Translation-en
Hit [http://sf.net](http://sf.net) sarab/main i386 Packages
Fetched 490 B in 15s (31 B/s)
Reading package lists... Done
N: Ignoring file 'kxstudio-debian.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'flexiondotorg-java-quantal.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'openshot_developers-ppa-raring.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'a-v-shkop-chromium-quantal.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'danielrichter2007-grub-customizer-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'kxstudio-team-latest-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'vovoid-vsxu-release-quantal.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'hughescih-ppa-quantal.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'upubuntu-com-mobile-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'upubuntu-com-graphics-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'chrysn-openscad-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'shutter-ppa-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'webupd8team-java-quantal.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'pinta-maintainers-pinta-daily-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'medibuntu.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'freyja-dev-unity-tweak-tool-daily-raring.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ffdiaporamateam-daily-raring.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'nightingaleteam-nightingale-release-quantal.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'kxstudio-team-ppa-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'dns-sound-quantal.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'otto-kesselgulasch-gimp-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'sunab-kdenlive-release-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'opera.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'norsetto-ppa-quantal.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'kxstudio-team-plugins-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'skype.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'gwendal-lebihan-dev-cinnamon-stable-raring.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'gwendal-lebihan-dev-cinnamon-stable-quantal.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'fkrull-deadsnakes-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'medibuntu-1210.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'kxstudio-non-free.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'yannubuntu-boot-repair-quantal.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'kxstudio-team-kxstudio-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-earth.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'kxstudio-team-kernel-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'kxstudio-team-music-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'jon-severinsson-ffmpeg-raring.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'apt-fast-stable-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ferramroberto-sopcast-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'opera-beta.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'kxstudio-team-games-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'dlynch3-ppa-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'tualatrix-ppa-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'peterlevi-ppa-quantal.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'trebelnik-stefina-sweethome3d-quantal.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-chrome.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'upubuntu-com-multimedia-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'giuseppe-iuculano-ppa-quantal.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'cinelerra-ppa-ppa-precise.list.distUpgrade' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
```

---

### Post by monkeybrain20122 on 2013-12-25
Forget about upgrading. Just save your data and do a fresh isntall. It is much faster (20 mins plus the time to reinstall software, the total is an  hr max,--usually much shorter but to be on the safe side,-- vs several hours) and save you a lot of potential problems later on.

---

### Post by deadflowr on 2013-12-25
What distro is that?

---

### Post by craig10x on 2013-12-25
@ deadflowr: Doing a quick search, it appears to be a debian based linux called waha linux...so apparently not ubuntu at all...can't figure how he thinks he could upgrade that to Ubuntu 13.10 :confused:

---

### Post by Bucky Ball on 2013-12-25
> **craig10x said:**
> ... a debian based linux called waha linux...so apparently not ubuntu at all...can't figure how he thinks he could upgrade that to Ubuntu 13.10 :confused:

> **papilonaa said:**
> 
... then i install by mistake waha-system-adjustments all.deb 

OP, who may be a he, but equally maybe a she, clearly states they installed waha by mistake. This does make it confusing. The original intention, also clearly stated, was to upgrade 13.04 to 13.10, then things went pear-shaped (extremely!). 

I know nothing about waha, never even heard of it, but I would imagine getting rid of that is the first step on getting things back on track.

As previously stated, backing up your personal data and doing a clean install of 13.10 may the cleanest, easiest path of least resistance at this point. Unless you fancy a xmas learning curve trying to get this back to what it was.

Can you simply log out, click the Sessions popup and choose Ubuntu instead of Waha, log back in again?

PS: @papilonaa: Your pics are too small to be of much use. Please make them larger and attach them to your post rather than inserting them in the body of the post (click 'Go Advanced' and use the paperclip icon to attach larger pics). Thanks.

---

### Post by deadflowr on 2013-12-25
Yeah, big +1, or +1000 to backing up and reinstalling a clean system.

It's possible you might be able to salvage something by simply deleting and removing all of those ppa's in the sources.list.d folder.
But I have a feeling that it would be far far easier to simply backup and re-apply, so to say.

---

### Post by braiampe on 2013-12-25
For those wondering exactly what the package does, I posted an answer in Ask Ubuntu [http://askubuntu.com/q/395717/169736](http://askubuntu.com/q/395717/169736)

---

### Post by Bucky Ball on 2013-12-25
> **braiampe said:**
> For those wondering exactly what the package does, I posted an answer in Ask Ubuntu [http://askubuntu.com/q/395717/169736](http://askubuntu.com/q/395717/169736)

... and the main thrust and the relevant bit for this support thread from that link is basically:
> 
... all the files in /usr/share/waha/adjustments/ are copied to the root of the filesystem without checking before hand and no way to remove them securely. The best option is just to backup everything and reinstall the system.

---

