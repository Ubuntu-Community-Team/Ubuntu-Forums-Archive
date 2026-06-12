---
title: "Apt-get upgrade holds back kernel packages while apt doesn't on a fresh 16.04 install"
date: 2016-08-16
forum: Installation &amp; Upgrades
---

### Post by jant90 on 2016-08-16
I just installed a fresh Ubuntu Server 16.04 on my VPS and ran apt-get upgrade but I saw some package held back. After some Googling I found out about apt (vs. apt-get), which I'm not familiar with (as I always used apt-get on previous installs).

What command can I best use to keep my Ubuntu installation up-to-date (and working/stable!)? As I see it my options are: apt-get upgrade, apt upgrade, apt-get dist-upgrade and apt full-upgrade. Below is the output of the various commands.

**apt-get -s upgrade**
```
$ sudo apt-get -s upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-headers-generic linux-signed-generic linux-signed-image-generic ubuntu-core-launcher
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```

**apt -s upgrade**
```
$ sudo apt -s upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic linux-image-4.4.0-34-generic linux-image-extra-4.4.0-34-generic linux-signed-image-4.4.0-34-generic snap-confine
The following packages will be upgraded:
  linux-headers-generic linux-signed-generic linux-signed-image-generic ubuntu-core-launcher
4 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Inst ubuntu-core-launcher [1.0.27.1] (1.0.38-0ubuntu0.16.04.4 Ubuntu:16.04/xenial-updates [amd64]) []
Inst snap-confine (1.0.38-0ubuntu0.16.04.4 Ubuntu:16.04/xenial-updates [amd64])
Inst linux-headers-4.4.0-34 (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [all])
Inst linux-headers-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Inst linux-image-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Inst linux-signed-image-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Inst linux-image-extra-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Inst linux-signed-generic [4.4.0.31.33] (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64]) []
Inst linux-signed-image-generic [4.4.0.31.33] (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64]) []
Inst linux-headers-generic [4.4.0.31.33] (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf snap-confine (1.0.38-0ubuntu0.16.04.4 Ubuntu:16.04/xenial-updates [amd64])
Conf ubuntu-core-launcher (1.0.38-0ubuntu0.16.04.4 Ubuntu:16.04/xenial-updates [amd64])
Conf linux-headers-4.4.0-34 (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [all])
Conf linux-headers-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-image-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-signed-image-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-image-extra-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-signed-image-generic (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-headers-generic (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-signed-generic (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
```

**apt-get -s dist-upgrade**
```
$ sudo apt-get -s dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic linux-image-4.4.0-34-generic linux-image-extra-4.4.0-34-generic linux-signed-image-4.4.0-34-generic snap-confine
The following packages will be upgraded:
  linux-headers-generic linux-signed-generic linux-signed-image-generic ubuntu-core-launcher
4 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Inst ubuntu-core-launcher [1.0.27.1] (1.0.38-0ubuntu0.16.04.4 Ubuntu:16.04/xenial-updates [amd64]) []
Inst snap-confine (1.0.38-0ubuntu0.16.04.4 Ubuntu:16.04/xenial-updates [amd64])
Inst linux-headers-4.4.0-34 (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [all])
Inst linux-headers-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Inst linux-image-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Inst linux-signed-image-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Inst linux-image-extra-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Inst linux-signed-generic [4.4.0.31.33] (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64]) []
Inst linux-signed-image-generic [4.4.0.31.33] (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64]) []
Inst linux-headers-generic [4.4.0.31.33] (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf snap-confine (1.0.38-0ubuntu0.16.04.4 Ubuntu:16.04/xenial-updates [amd64])
Conf ubuntu-core-launcher (1.0.38-0ubuntu0.16.04.4 Ubuntu:16.04/xenial-updates [amd64])
Conf linux-headers-4.4.0-34 (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [all])
Conf linux-headers-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-image-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-signed-image-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-image-extra-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-signed-image-generic (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-headers-generic (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-signed-generic (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
```

**apt-get full-upgrade**
```
$ sudo apt -s full-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic linux-image-4.4.0-34-generic linux-image-extra-4.4.0-34-generic linux-signed-image-4.4.0-34-generic snap-confine
The following packages will be upgraded:
  linux-headers-generic linux-signed-generic linux-signed-image-generic ubuntu-core-launcher
4 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Inst ubuntu-core-launcher [1.0.27.1] (1.0.38-0ubuntu0.16.04.4 Ubuntu:16.04/xenial-updates [amd64]) []
Inst snap-confine (1.0.38-0ubuntu0.16.04.4 Ubuntu:16.04/xenial-updates [amd64])
Inst linux-headers-4.4.0-34 (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [all])
Inst linux-headers-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Inst linux-image-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Inst linux-signed-image-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Inst linux-image-extra-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Inst linux-signed-generic [4.4.0.31.33] (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64]) []
Inst linux-signed-image-generic [4.4.0.31.33] (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64]) []
Inst linux-headers-generic [4.4.0.31.33] (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf snap-confine (1.0.38-0ubuntu0.16.04.4 Ubuntu:16.04/xenial-updates [amd64])
Conf ubuntu-core-launcher (1.0.38-0ubuntu0.16.04.4 Ubuntu:16.04/xenial-updates [amd64])
Conf linux-headers-4.4.0-34 (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [all])
Conf linux-headers-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-image-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-signed-image-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-image-extra-4.4.0-34-generic (4.4.0-34.53 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-signed-image-generic (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-headers-generic (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
Conf linux-signed-generic (4.4.0.34.36 Ubuntu:16.04/xenial-updates, Ubuntu:16.04/xenial-security [amd64])
```


**So what command should I keep using?**

Thanks.

---

### Post by Bashing-om on 2016-08-16
jant90; Hello;

Why sometimes packeages are held back - phased updates:
[http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04)
[http://lwn.net/Articles/563966/](http://lwn.net/Articles/563966/)

Why apt over apt-get:
[https://www.reddit.com/r/linux/comments/26q2sm/apt_vs_aptget/](https://www.reddit.com/r/linux/comments/26q2sm/apt_vs_aptget/)
[http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/](http://www.howtogeek.com/234583/simplify-command-line-package-management-with-apt-instead-of-apt-get/)
[https://mvogt.wordpress.com/2014/04/04/apt-1-0/](https://mvogt.wordpress.com/2014/04/04/apt-1-0/)

One may over ride the phased updates - in your best judgement:
```

sudo apt update
sudo apt full-upgrade

```

[INDENT][INDENT]system administration
[INDENT][INDENT][INDENT]an art in and of it's self
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-08-16
It seems that from 16.04 onwards apt is to be preferred over apt-get. Ubuntu developers in tutorials have started to use apt instead of apt-get.

I think that you will find that apt upgrade will also sometimes have packages being held back. The commands apt-get dist-upgrade and apt full-upgrade do much the same thing. They will download and install held back packages even if it means removing existing packages to avoid a conflict.

The command: man apt says.

> full-upgrade (apt-get(8))
           full-upgrade performs the function of upgrade but will remove
           currently installed packages if this is needed to upgrade the
           system as a whole.


The wiki on apt-get says, 
> apt-get dist-upgrade The same as the above [apt-get upgrade], except add the  "smart upgrade" checkbox. It tells APT to use "smart" conflict  resolution system, and it will attempt to upgrade the most important  packages at the expense of less important ones if necessary.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

For safety

```
sudo apt update
sudo apt upgrade
```

If impatient to get held back packages

```
sudo apt full-upgrade
```

Regards

---

### Post by ian-weisser on 2016-08-16
> **jant90 said:**
> What command can I best use to keep my Ubuntu installation up-to-date (and working/stable!)? As I see it my options are: apt-get upgrade, apt upgrade, apt-get dist-upgrade and apt full-upgrade.

 grahammechanical's insight is correct and very well said.
In 16.04 and newer, use apt.

I use unattended-updates (in the Ubuntu repos) to stay up to date instead of mucking about manually on that treadmill. Once a month or so, I do an ordinary 'apt upgrade' to catch any upgrades from my other repos.

When the time comes to do a release upgrade (every six months), I uninstall the non-Ubuntu software, disable the non-Ubuntu repos, run a 'do-release-upgrade', restore the non-Ubuntu repos, and finally reinstall the non-Ubuntu software, Were I sticking with LTS, I would run 'apt full-upgrade' before upgrading to the next LTS point release.

It won't hurt to run 'apt full-upgrade' every day. It won't help much either, but that's irrelevant if it makes you feel better.

---

### Post by jant90 on 2016-08-16
Thanks for the input :).

If apt seems to be preferred now (in Ubuntu 16.04) I will simply use that and assume that apt knows (better) what to upgrade and hold back. I just found it weird that apt and apt-get would behave differently on a completely clean Ubuntu 16.04 install and it worried me one might make better choices than the other, in particular in the long run.

Btw, in this case it makes no difference if I use apt update or apt full-update.

---

### Post by grahammechanical on 2016-08-17
I have just loaded an install of 16.10 development version that I had  not updated for a few days. I ran apt update and I see this.

> The following packages have been kept back:
click  compiz compiz-core compiz-gnome compiz-plugins-default    gir1.2-click-0.4 gir1.2-totem-1.0 libclick-0.4-0 libcompizconfig0   libdecoration0 libreoffice-help-en-us libtotem0 metacity-common  packagekit   python3-click-package totem totem-common totem-plugins


So, apt like apt-get also has held back packages. The command: man apt-get says

> apt-get  is the command-line tool for handling packages, and may be considered  the user's "back-end" to other tools using the APT library. Several  "front-end" interfaces exist, such as aptitude(8), synaptic(8)

I have tried to find information about this change as to why it is better but I have so far been unsuccessful.

Regards.

---

