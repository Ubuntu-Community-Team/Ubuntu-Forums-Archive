---
title: "Trouble with apt and aptitude"
date: 2005-07-02
forum: Installation &amp; Upgrades
---

### Post by ancoblanco on 2005-07-02
Hi. I've just finished my installation of Ubuntu Linux. I really liked the installation, just minor problem with my wireless card and everything else magically worked. I'm having trouble with apt-get, it seems that about 50% of the packages I'm trying to install is broken. Anyone else having this problem?

I walked through the starter guide, [http://ubuntuguide.org/](http://ubuntuguide.org/) and copied that apt sources.list file but still I'm having trouble with getting those packages in that guide

Is there anything more to configure with apt (like security issues, get dependencies)? The only conf I've done now is that sources.list that is changed, otherwise I use commands as:
# apt-get install xemacs21

Some ideas?

/Andreas

---

### Post by Xian on 2005-07-02
[QUOTE=ancoblanco]I'm having trouble with apt-get, it seems that about 50% of the packages I'm trying to install is broken. Anyone else having this problem?[/QUOTE]
Let's do a couple of commands and if there are errors, please post what they are. Open a terminal and issue the commands listed below. Again, if you get errors just copy/paste the output and post back in this thread.
```
$ sudo apt-get update
$ sudo apt-get -f install
```

---

### Post by ancoblanco on 2005-07-03
Hi. Yes I'm still having problems. For instance with xemacs21 I issued the commands that you posted and then tried:
#apt-get install xemacs21 and got this output (roughly translated from swedish):

```
Following packages has dependencies that can not be satisfied:
  xemacs21: depends: xemacs21-mule (= 21.4.17-1) but it will not be installed
                   xemacs21-mule-canna-wnn (= 21.4.17-1) but it will not be installed
                   xemacs21-nomule (= 21.4.17-1) but it will not be installed
                   xemacs21-gnome-mule (= 21.4.17-1) but it will not be installed
                   xemacs21-gnome-mule-canna-wnn (= 21.4.17-1) but it will not be installed
                   xemacs21-gnome-nomule (= 21.4.17-1) but it will not be installed
E: Broken packages
```

It is the same kind of error messages with other packages. Thankful for your help.

---

### Post by Xian on 2005-07-03
Since you are able to run 'apt-get -f install' and 'apt-get update' without any errors, the problem has to reside in your repo selection if we are both on x86 archs. The only thing I can advise is that you use my sources.list since I do not have this difficulty.

Here is output on my box using your install command:
```
$ sudo apt-get install xemacs21
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  emacsen-common libcompfaceg1 xemacs21-basesupport xemacs21-bin xemacs21-mule
  xemacs21-mulesupport xemacs21-support
Suggested packages:
  xemacs21-supportel
The following NEW packages will be installed:
  emacsen-common libcompfaceg1 xemacs21 xemacs21-basesupport xemacs21-bin
  xemacs21-mule xemacs21-mulesupport xemacs21-support
0 upgraded, 8 newly installed, 0 to remove and 1 not upgraded.
Need to get 31.2MB of archives.
After unpacking 103MB of additional disk space will be used.
Do you want to continue [Y/n]?
```
Here is my /etc/apt/sources.list:
```
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

## Backports 
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by ancoblanco on 2005-07-04
That solved my problem, I was really tempted going back to slackware and dropline gnome again, but now I'll stick around with Ubuntu and will give it a real try. The difference I could notice was in the backports section and then that I had language specifics in the other url:s like [http://se.archive](http://se.archive)..... 

Thanks alot!

---

### Post by Xian on 2005-07-04
A lot of that configuration is by default on the primary mirrors.
You would not have had any reason to look....

I got borked on something similar and dug around.
Heh. That's how you learn.

---

