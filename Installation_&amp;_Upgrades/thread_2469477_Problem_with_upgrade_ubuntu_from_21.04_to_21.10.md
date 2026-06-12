---
title: "Problem with upgrade ubuntu from 21.04 to 21.10?"
date: 2021-11-30
forum: Installation &amp; Upgrades
---

### Post by gale85 on 2021-11-30
As the title says, I can't upgrade ubuntu from 21.04 to 21.10. 
I messed something with the programs from Kali and now instead of being connected to the ubuntu server I am connected to the Kali linux server. 
Here’s a [picture]("https://postimg.cc/YvvsY7N0") to make it clearer to you what I’m talking about. 
After that I downloaded the ubuntu 21.10 iso image file but I don't know how to run it. 
Specifically, I open the image file but I don't know how to start the installation.

---

### Post by gale85 on 2021-11-30
I want to run the installation without a boot. 
I don't want to save it to a flash drive and then start the installation, but if I can do it directly through the iso file.
I already said I know how to open an iso file but I don't know how to run the installation (same as autorun in Windows)

---

### Post by T6&amp;sfpER35% on 2021-11-30
are you still on 20.04 ?
then open **software&updates** , go to **update tab** , find** Notify me of a new Ubuntu version** , change &#8220;**For long-term support versions**&#8221; to &#8220;**For any new version**&#8221; , and close.
run **software&updates** again , it should now tell you 20.10 is available blah blah blah , simply click **upgrade**.
not sure what you mean you can't run the ISO image? an ISO image is meant to be burned to a media and then booted from that media.
that will do a clean install , meaning wiping everything you had on. so backup 1st if that's the route you want to go.
personally i'd stick with 20.04, which is a LTS

*edit* ignore the last piece, only see post#2 now after i typed

---

### Post by ActionParsnip on 2021-11-30
What is the output of
```

lsb_release -a; uname -a

```
I suggest you disable the Kali repositories, update then re-enable

---

### Post by gale85 on 2021-11-30
@3nd As I already wrote in the title I use version 21.04 and I have long ago set "For any new version"

---

### Post by gale85 on 2021-11-30
lsb_release -a; uname -a
> 
No LSB modules are available.Distributor ID:	Kali
Description:	Kali GNU/Linux Rolling Gale
Release:	2021.2
Codename:	kali-rolling
Linux gale85-EP35-DS3R 5.11.0-22-generic #23-Ubuntu SMP Thu Jun 17 00:34:23 UTC 2021 x86_64 GNU/Linux

How do I exclude Kali from the repository and am I struggling with that?

---

### Post by T6&amp;sfpER35% on 2021-11-30
oh i made a typo ,meant 21.04
ok cool ,sorry can't help.
PS. doesn't look like your on ubuntu 21.04

---

### Post by gale85 on 2021-11-30
This is 100% ubuntu. I have never used Kali Linux. I have been using Ubuntu since 2008 and I have not used any other Linux except Ubuntu and I have already said how this error occurred. The worst part is that I can't get Kali out of the repository now, and I've reviewed the /etc/apt/sources.list file and the Software & Updates -> Other Software site, and there's nothing included about Kali Linux other than the image in the first message.

---

### Post by tea for one on 2021-11-30
Have you reviewed [COLOR="#0000FF"]/etc/apt/sources.list.d[/COLOR]?

Anything there?

---

### Post by gale85 on 2021-11-30
/etc/apt/sources.list.d$ ls
anydesk-stable.list                                              nilarimogard-ubuntu-webupd8-eoan.list
anydesk-stable.list.save                                         nilarimogard-ubuntu-webupd8-eoan.list.distUpgrade
appgrid-stable.list                                              nilarimogard-ubuntu-webupd8-eoan.list.save
appgrid-stable.list.distUpgrade                                  nodesource.list
appgrid-stable.list.save                                         nodesource.list.save
appgrid-ubuntu-stable-focal.list.save                            openshot_developers-ubuntu-ppa-focal.list
danielrichter2007-ubuntu-grub-customizer-focal.list              openshot_developers-ubuntu-ppa-focal.list.distUpgrade
danielrichter2007-ubuntu-grub-customizer-focal.list.distUpgrade  openshot_developers-ubuntu-ppa-focal.list.save
danielrichter2007-ubuntu-grub-customizer-focal.list.save         steam.list
flexiondotorg-ubuntu-minecraft-eoan.list                         steam.list.distUpgrade
flexiondotorg-ubuntu-minecraft-eoan.list.distUpgrade             steam.list.save
flexiondotorg-ubuntu-minecraft-eoan.list.save                    teamviewer.list
google-chrome.list                                               teamviewer.list.distUpgrade
google-chrome.list.distUpgrade                                   teamviewer.list.save
google-chrome.list.save                                          vscode.list
jonathonf-ubuntu-ffmpeg-4-kali-rolling.list                      vscode.list.save
jonathonf-ubuntu-ffmpeg-4-kali-rolling.list.save                 webupd8team-ubuntu-java-focal.list
lutris-team-ubuntu-lutris-kali-rolling.list                      webupd8team-ubuntu-java-focal.list.distUpgrade
lutris-team-ubuntu-lutris-kali-rolling.list.save                 webupd8team-ubuntu-java-focal.list.save

---

### Post by tea for one on 2021-11-30
From post no. 6
 ```
No LSB modules are available.Distributor ID: Kali
Description: [COLOR="#0000FF"]Kali GNU/Linux Rolling Gale[/COLOR]
Release: 2021.2
Codename: kali-rolling
Linux gale85-EP35-DS3R 5.11.0-22-generic #23-Ubuntu SMP Thu Jun 17 00:34:23 UTC 2021 x86_64 GNU/Linux 
```

You said it was 100% Ubuntu but your info above does not support this?

---

### Post by gale85 on 2021-11-30
Well, it's a problem for me that it says Kali Linux and I know it's Ubuntu and I have no idea how it happened except for what I've already written

---

### Post by deadflowr on 2021-11-30
You have at least two sources marked for kali-rolling
What do those two files show:
```
cd /etc/apt/sources.list.d
cat lutris-team-ubuntu-lutris-kali-rolling.list 
cat jonathonf-ubuntu-ffmpeg-4-kali-rolling.list
```
(Note, while you can run both with a single cat command, I figure it to be better to break them apart for better readability)

---

### Post by tea for one on 2021-11-30
If you look at your screenshot from post no.1, you will see [COLOR="#FF0000"]Kali Software[/COLOR] in the top left tab.

An Ubuntu OS would display [COLOR="#0000FF"]Ubuntu Software[/COLOR] in the same position.

If you do not know how all this happened, then why not bite the bullet:-

Back up your personal data.
Create an install USB using your Ubuntu 21.10 ISO.
Fresh install and restore back up.

It should be quite simple as you have been using Ubuntu since 2008.

---

### Post by gale85 on 2021-11-30
cat lutris-team-ubuntu-lutris-kali-rolling.list 
> 

# deb [http://ppa.launchpad.net/lutris-team/lutris/ubuntu/](http://ppa.launchpad.net/lutris-team/lutris/ubuntu/) kali-rolling main
# deb-src [http://ppa.launchpad.net/lutris-team/lutris/ubuntu/](http://ppa.launchpad.net/lutris-team/lutris/ubuntu/) kali-rolling main

cat jonathonf-ubuntu-ffmpeg-4-kali-rolling.list
> 

# deb [http://ppa.launchpad.net/jonathonf/ffmpeg-4/ubuntu/](http://ppa.launchpad.net/jonathonf/ffmpeg-4/ubuntu/) kali-rolling main
# deb-src [http://ppa.launchpad.net/jonathonf/ffmpeg-4/ubuntu/](http://ppa.launchpad.net/jonathonf/ffmpeg-4/ubuntu/) kali-rolling main


---

### Post by grahammechanical on 2021-11-30
A 100% pure Ubuntu would store the internet addresses of its repositories at /etc/apt/source.list. Lines in that file that have a hash ( # ) prefix are treated as comments and are not acted upon by update manager. It could be that the Kali programs that you have installed have commented out all the internet addresses for the Ubuntu servers. Those programs might have changed the address to Kali servers. This is what a Ubuntu 21.10 sources.list file looks like.

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) impish main
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) inpish main restricted

# Major bug fix updates produced after the final release of the
## distribution.
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) impish-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) impish universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) impish universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) impish-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) impish multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) impish-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) impish-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) impish partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) impish partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) impish-security main restricted universe multiverse


Because I live in London, England I update from the GB Ubuntu server. I also do not have the multiverse repository enabled.

I do agree with the suggestion mentioned above of doing a fresh install of 21.10. You would then need to upgrade to 22.04 LTS in about six months time. Which you will have to do anyway at some time. If you want to get some kind of a benefit from Kali you could always dual boot between Ubuntu and Kali Linux.

P.S. The 21.04 source.list would have "hirsute" instead of "impish." It all depends upon which sources list file a person is attempting to rebuild.

Regards

---

### Post by T6&amp;sfpER35% on 2021-12-01
> If you want to get some kind of a benefit from Kali you could always dual boot
out of curiosity...iv'e read somewhere that all or most kali tools can be installed in a regular distro , like ubuntu.
that true ? or not feasible ?

---

### Post by gale85 on 2021-12-04
@3nd That's right, the programs that I installed in ubuntu are by default in Kali Linux. I found a clip where it was explained how easier it is to access those programs, and supposedly that clip is there, so I think it was close to a million views after that, when I did everything like in the clip, this mistake happened to me.

I made a USB flash the other day, but it won't boot, does anyone have any idea how to solve this problem.

---

### Post by gale85 on 2021-12-11
Folks just to let you know that I inserted the CD-ROM into my computer I installed the latest Ubuntu 21.10 and so now everything works ok. 
Thanks to everyone for their help.

---

