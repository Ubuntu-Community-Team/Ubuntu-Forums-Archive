---
title: "problem updating"
date: 2014-05-04
forum: Installation &amp; Upgrades
---

### Post by 4dr14n on 2014-05-04
Hi everyone,

It's several months that I use Lubuntu and, I am quite happy with it... step by step I'm improving my "skills", and feeling more and more comfortable, even using the console.
But there is a little thing I'd ask, because I don't know how to solve it, even if I think it's not important and never gave me problems.
Once, I installed *R!* and *Damnvid* following some instructions I found on the net, this was at the very first weeks of my ubuntu's experience, so I just followed (and tried to understand, but I remark trying) the points that the tutorial had.

Now, when I do update, this is what appears:

```
W: Imposible obtener http://cran.es.r-project.org/bin/linux/ubuntu/raring/Sources  404  Not Found

W: Imposible obtener http://cran.es.r-project.org/bin/linux/ubuntu/raring/Packages  404  Not Found


W: Imposible obtener http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found


W: Imposible obtener http://ppa.launchpad.net/damnvid/ppa/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found



```

I think I have some unnecessary packages in my laptop and all that I want is to know ho to remove them (and any new one that comes in the future), or a better answer.


Thank you so much in advance.

---

### Post by bapoumba on 2014-05-04
None of these repos have raring as far as I can tell :
[http://cran.es.r-project.org/](http://cran.es.r-project.org/)
[http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/dists/](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu/dists/)

Are you on raring 13.04 ? Its reached end of life last January, which explains the repos are not up anymore.

Best to do is uninstall the packages you got from the repos (for ppas, you can use ppa-purge : [https://launchpad.net/ubuntu/+source/ppa-purge](https://launchpad.net/ubuntu/+source/ppa-purge)), remove them from your software sources and upgrade to a supported release. Being on 13.04, you should go first to 13.10 and then 14.04 LTS.

Please post the outputs to :
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
```

---

### Post by 4dr14n on 2014-05-04
Yes I am still on 13.04, I am a bit worried about lose something and I need the pc everyday... I thought on delete the OS and install the new one, but I have a lot of things in the laptop that I want to mantain (Do you reccommend me to update the version?)

And there it goes:
> adrian@adrian-Latitude-D531:~$ cat /etc/apt/sources.list# deb cdrom:[Lubuntu 13.04 _Raring Ringtail_ - Release i386 (20130423.1)]/ raring main multiverse restricted universe


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring restricted multiverse main universe #Added by software-properties


## Major bug fix updates produced after the final release of the
## distribution.


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) raring multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.




## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb [http://archive.canonical.com/](http://archive.canonical.com/) raring partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) raring partner
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
adrian@adrian-Latitude-D531:~$ ls /etc/apt/sources.list.d
clipgrab-team-ppa-raring.list       dropbox.list.save
clipgrab-team-ppa-raring.list.save  jd-team-jdownloader-raring.list
cran.list                           jd-team-jdownloader-raring.list.save
cran.list.save                      mendeleydesktop.list
damnvid-ppa-raring.list             mendeleydesktop.list.save
damnvid-ppa-raring.list.save        nilarimogard-webupd8-raring.list
dropbox.list                        nilarimogard-webupd8-raring.list.save
adrian@adrian-Latitude-D531:~$ 




---

### Post by ian-weisser on 2014-05-04
> **4dr14n said:**
> but I have a lot of things in the laptop that I want to mantain (Do you reccommend me to update the version?)

I recommend you to backup your data before you do anything else.
Laptops can be dropped or stolen, too. Without backup, you will surely lose all your data someday.

After you have backed up, I recommend updating to a supported version of Ubuntu.
Your unsupported version is not receiving security updates, and is vulnerable to published exploits.
If your system is compromised, you may lose your data.

---

### Post by bapoumba on 2014-05-04
+1 to ian-weisser.

---

