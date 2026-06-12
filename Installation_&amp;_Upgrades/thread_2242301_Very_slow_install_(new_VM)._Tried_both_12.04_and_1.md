---
title: "Very slow install (new VM). Tried both 12.04 and 14.04"
date: 2014-09-01
forum: Installation &amp; Upgrades
---

### Post by Neil_Clayton on 2014-09-01
Hi,

I'm using virtual box VM's on Mac OSX 10.9.5.
I'm seeing really, really slow performance on apt-get update and subsequent apt-get installs.

It appears primarily related to fetches from security.ubuntu.com.
I get to "[FONT=Menlo]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en" and things essentially stop.[/FONT]
[FONT=Menlo]It completes (sometimes) perhaps 20-30m later.[/FONT]

[FONT=Menlo]Disk read/write speeds are fine (800mb/s).[/FONT]
[FONT=Menlo]System is fine otherwise. It's a brand new untouched VM install.  Happens with both 12.04 and 14.04 (Different base images) so I don't think it's VM related.[/FONT]

[FONT=Menlo]Top shows a load average of 0.05.[/FONT]
[FONT=Menlo]The host machine is essentially idle. I've tried two different machines.[/FONT]
[FONT=Menlo]Outgoing network is 100mbit down, and I have no problem hitting that.[/FONT]

[FONT=Menlo]I've attached sources.lst in cast its related.[/FONT]
[FONT=Menlo]Tried using local mirrors, but get the same thing (security URL's don't appear to differ when using a local source).[/FONT]

[FONT=Menlo]---[/FONT]
[FONT=Menlo]While writing this, I go this far in the update:
[/FONT][FONT=Menlo]----

Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en[/FONT][FONT=Menlo]Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [246 kB]                                                                                                                          [/FONT]
[FONT=Menlo]Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [15.3 kB][/FONT]
[FONT=Menlo]Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [861 kB][/FONT]
[FONT=Menlo]67% [5 Packages 484 kB/861 kB 56%]                                                                                                                                                                           [/FONT]


Before the speed disappeared completely, it said it was managing a whopping 1,566B/s.



[FONT=Menlo]Any ideas?[/FONT]


[FONT=Menlo]---- [/FONT]
[FONT=Menlo]Sources.lst[/FONT]
[FONT=Menlo]----[/FONT]

[FONT=Menlo]# [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/main/binary-i386/[/FONT]
[FONT=Menlo]# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/restricted/binary-i386/[/FONT]
[FONT=Menlo]# deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ precise main restricted[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]#deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/main/binary-i386/[/FONT]
[FONT=Menlo]#deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ dists/precise/restricted/binary-i386/[/FONT]
[FONT=Menlo]#deb cdrom:[Ubuntu-Server 12.04 LTS _Precise Pangolin_ - Release amd64 (20120424.1)]/ precise main restricted[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to[/FONT]
[FONT=Menlo]# newer versions of the distribution.[/FONT]
[FONT=Menlo]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted[/FONT]
[FONT=Menlo]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]## Major bug fix updates produced after the final release of the[/FONT]
[FONT=Menlo]## distribution.[/FONT]
[FONT=Menlo]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted[/FONT]
[FONT=Menlo]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu[/FONT]
[FONT=Menlo]## team. Also, please note that software in universe WILL NOT receive any[/FONT]
[FONT=Menlo]## review or updates from the Ubuntu security team.[/FONT]
[FONT=Menlo]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe[/FONT]
[FONT=Menlo]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe[/FONT]
[FONT=Menlo]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe[/FONT]
[FONT=Menlo]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu [/FONT]
[FONT=Menlo]## team, and may not be under a free licence. Please satisfy yourself as to [/FONT]
[FONT=Menlo]## your rights to use the software. Also, please note that software in [/FONT]
[FONT=Menlo]## multiverse WILL NOT receive any review or updates from the Ubuntu[/FONT]
[FONT=Menlo]## security team.[/FONT]
[FONT=Menlo]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse[/FONT]
[FONT=Menlo]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse[/FONT]
[FONT=Menlo]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse[/FONT]
[FONT=Menlo]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]## N.B. software from this repository may not have been tested as[/FONT]
[FONT=Menlo]## extensively as that contained in the main release, although it includes[/FONT]
[FONT=Menlo]## newer versions of some applications which may provide useful features.[/FONT]
[FONT=Menlo]## Also, please note that software in backports WILL NOT receive any review[/FONT]
[FONT=Menlo]## or updates from the Ubuntu security team.[/FONT]
[FONT=Menlo]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse[/FONT]
[FONT=Menlo]deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted[/FONT]
[FONT=Menlo]deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted[/FONT]
[FONT=Menlo]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe[/FONT]
[FONT=Menlo]deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe[/FONT]
[FONT=Menlo]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse[/FONT]
[FONT=Menlo]deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]## Uncomment the following two lines to add software from Canonical's[/FONT]
[FONT=Menlo]## 'partner' repository.[/FONT]
[FONT=Menlo]## This software is not part of Ubuntu, but is offered by Canonical and the[/FONT]
[FONT=Menlo]## respective vendors as a service to Ubuntu users.[/FONT]
[FONT=Menlo]# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner[/FONT]
[FONT=Menlo]# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]## Uncomment the following two lines to add software from Ubuntu's[/FONT]
[FONT=Menlo]## 'extras' repository.[/FONT]
[FONT=Menlo]## This software is not part of Ubuntu, but is offered by third-party[/FONT]
[FONT=Menlo]## developers who want to ship their latest software.[/FONT]
[FONT=Menlo]# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main[/FONT]
[FONT=Menlo]# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main[/FONT]

---

### Post by TheFu on 2014-09-01
Does a web browser locate  [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) ?
Is it fast or slow or non-existent.

Could the DNS be down?

All shots in the dark.

---

### Post by diepnguyen on 2014-09-01
Try to switch your DNS servers to: 8.8.8.8 and 8.8.4.4 (from Google)

---

