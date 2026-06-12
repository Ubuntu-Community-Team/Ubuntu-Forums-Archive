---
title: "Can't open Software Sources GUI"
date: 2009-10-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by paul_in_london on 2009-10-31
I thought I knew the answer to this, but not quite. The problem seems to be related to the fact that my Lucid install is directly descended from Jaunty (Alpha 2 I think it was) &#8211; i.e. I haven't done a clean install on this particular drive since then, I've just been upgrading through the release and dev cycles.

Here's my **/etc/lsb-release** file:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu lucid (development branch)"
```

which looks correct. I thought I'd see what would happen if I ran:

```
sudo update-manager &#8211;dist-upgrade
```

This results in a pop-up message saying &#8220;[COLOR="Red"]An upgrade from 'lucid' to 'karmic' is not supported with this tool[/COLOR]&#8221;.

When I close the dialog, I see this message on the terminal:

```
paul@lucid:~$ sudo update-manager --dist-upgrade

[COLOR="Red"]ERROR:root:Bad upgrade: 'lucid' != 'jaunty'
[/COLOR]
```

So something in one (or more) of my files is still pointing to Jaunty. Can someone suggest which one(s) I need to check?

Cheers.

[COLOR="Red"]Afterthought: actually it's just really saying that the expected upgrade path is from jaunty to karmic, but I still don't know how to fix it! I didn't get any errors the other day when I updated my **/etc/apt/sources.list** to refer to lucid and did aptitude update/upgrade.[/COLOR]

---

### Post by sliketymo on 2009-10-31
> **paul_in_london said:**
> I thought I knew the answer to this, but not quite. The problem seems to be related to the fact that my Lucid install is directly descended from Jaunty (Alpha 2 I think it was) – i.e. I haven't done a clean install on this particular drive since then, I've just been upgrading through the release and dev cycles.

Here's my **/etc/lsb-release** file:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu lucid (development branch)"
```which looks correct. I thought I'd see what would happen if I ran:

```
sudo update-manager –dist-upgrade
```This results in a pop-up message saying “[COLOR=Red]An upgrade from 'lucid' to 'karmic' is not supported with this tool[/COLOR]”.

When I close the dialog, I see this message on the terminal:

```
paul@lucid:~$ sudo update-manager --dist-upgrade

[COLOR=Red]ERROR:root:Bad upgrade: 'lucid' != 'jaunty'
[/COLOR]
```So something in one (or more) of my files is still pointing to Jaunty. Can someone suggest which one(s) I need to check?

Cheers.

:popcorn:It's not out yet.

---

### Post by paul_in_london on 2009-10-31
Yep, I get that!

---

### Post by Amaranth on 2009-10-31
python-apt has not been updated to include a lucid profile which is what Software Sources is complaining about. update-manager -dist-upgrade is only meant to upgrade from one version of a distribution to another so I'm not even sure why you'd try it.

---

### Post by paul_in_london on 2009-10-31
Hi, many thanks for your response.

I edited my post a few minutes ago when I realised I'd jumped to the wrong conclusion.

I only ran the update manager command thinking that it might help shed some light on the problem.

Cheers.

---

### Post by LKjell on 2009-11-01
If you already have Lucid Lynx add this to /usr/share/python-apt/templates/Ubuntu.info before Suit: karmic

```
Suite: lucid
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com|archive.ubuntu.com
BaseURI-lpia: http://ports.ubuntu.com/
MatchURI-lpia: ports.ubuntu.com|archive.ubuntu.com
MirrorsFile-amd64: /usr/share/python-apt/templates/Ubuntu.mirrors
MirrorsFile-i386: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 10.4 'Lucid Lynx'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: lucid
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*10.4
MatchURI: cdrom:\[Ubuntu.*10.4
Description: Cdrom with Ubuntu 10.4 'Lucid Lynx'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: lucid-security
ParentSuite: lucid
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com/ubuntu
BaseURI-lpia: http://ports.ubuntu.com/
MatchURI-lpia: ports.ubuntu.com/ubuntu
Description: Important security updates

Suite: lucid-updates
ParentSuite: lucid
RepositoryType: deb
Description: Recommended updates

Suite: lucid-proposed
ParentSuite: lucid
RepositoryType: deb
Description: Pre-released updates

Suite: lucid-backports
ParentSuite: lucid
RepositoryType: deb
Description: Unsupported updates
```

You can read more at here:
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/364092](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/364092)

---

### Post by paul_in_london on 2009-11-01
Ah, I'd forgotten about this file. All sorted now.

Thanks very much and thanks for the link!

---

### Post by autocrosser on 2009-11-01
Thanks!!1 I'd forgot about that also!!

---

### Post by Regenweald on 2009-11-02
Thank you all so much for this info :)

---

### Post by VMC on 2009-11-04
> **LKjell said:**
> If you already have Lucid Lynx add this to /usr/share/python-apt/templates/Ubuntu.info before Suit: karmic

[CODE]Suite: lucid
...
Thanks. I almost made the mistake of just replacing the contents with your add. Every single release is listed there.

Thanks for the link. I'll read up on it to see what this files is all about. I didn't forget about this file, like the rest of you, I didn't even know about it. Started karmic at alpha 2.

---

