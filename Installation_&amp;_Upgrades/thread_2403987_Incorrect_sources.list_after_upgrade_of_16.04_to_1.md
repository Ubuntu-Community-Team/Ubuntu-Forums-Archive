---
title: "Incorrect sources.list after upgrade of 16.04 to 18.04"
date: 2018-10-18
forum: Installation &amp; Upgrades
---

### Post by evansj2 on 2018-10-18
[FONT=arial]I have two servers at home which were running Ubuntu 16.04. I upgraded both of them to 18.04 a few months ago using [COLOR=#333333][FONT=courier new]sudo do-release-upgrade[/FONT] as described in the official docs. The servers themselves are very different, one is a fairly feeble mini-ITX machine and the other is a 16 core AMD64.

The mini-ITX upgraded fine, the other one had all sorts of problems which I eventually resolved, and I'm kicking myself now that I didn't make any notes about what the problem was. It runs OK now, mainly services inside a handful of docker containers. However I'm now in the following situation:

[/COLOR][/FONT]
[LIST]
[*][FONT=arial][COLOR=#333333]Both servers are running kernel [/COLOR][/FONT]4.15.0-36-generic
[*]Both servers think that they are running 18.04 LTS:
[/LIST]

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic
```


[LIST]
[*]One of the servers has xenial in its /etc/apt/sources.list and the other has bionic.
[/LIST]

The server which is OK:

```
$ grep -v -E '^#|^$' /etc/apt/sources.list
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic-updates universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
```

The server which still has xenial:

```
$ grep -v -E '^#|^$' /etc/apt/sources.list
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
deb [https://apt.dockerproject.org/repo/](https://apt.dockerproject.org/repo/) ubuntu-xenial main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-proposed restricted main multiverse universe
deb [arch=amd64] [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) bionic stable
```


The "broken" server thinks that it's up to date:

```
$ sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found.
```

I only noticed when I thought it was weird that [FONT=courier new]sudo apt update[/FONT] on that server hasn't found anything to update in the last few weeks and normally there's at least one updated package every day or so.

Can I fix this by just updating [FONT=courier new]/etc/apt/sources.list[/FONT] or is there more to it than that?

---

### Post by evansj2 on 2018-10-22
OK, I manually updated [FONT=&quot]/etc/apt/sources.list[/FONT] and changed all of the [FONT=&quot]xenial[/FONT] references to [FONT=&quot]bionic[/FONT]. [FONT=&quot]apt[/FONT] subsequently installed ~200 updates and after a reboot everything seems to be working OK.

---

