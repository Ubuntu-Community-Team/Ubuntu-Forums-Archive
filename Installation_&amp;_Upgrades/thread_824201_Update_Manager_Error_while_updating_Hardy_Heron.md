---
title: "Update Manager: Error while updating Hardy Heron"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by gaijindewanai on 2008-06-09
there were 2 errors occurred when I updated my Hardy Heron through Update Manager.
it said:

An error occurred
The following details are provided:
E: python-awn-trunk: subprocess post-installation script returned error exit status 1
E: awn-manager-trunk: dependency problem - leaving unconfigured

I'm new in Linux and i attached the screenshot of my comp when the errors occurred.

How can I fix this problem?:confused:

Thanx in advance.

---

### Post by Pumalite on 2008-06-09
You failed to remove all third parties from /etc/apt/sources.list prior to the upgrade maybe.
Run:
sudo aptitude autoclean.
Reinstall awn

---

### Post by gaijindewanai on 2008-06-09
Is there any way to fix it without reinstalling awn?
I actually don't even know how to reinstall it.

Sorry, I'm a newbie..

---

### Post by Pumalite on 2008-06-09
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

---

### Post by Pumalite on 2008-06-09
You might want to also run:
sudo aptitude update
sudo aptitude dist-upgrade

---

### Post by gaijindewanai on 2008-06-09
does that mean I don't have to reinstall awn?

---

### Post by Pumalite on 2008-06-09
Post the outputs of the commands I gave you. If dependencies were satisfied and old packages removed; you are OK. to reinstall. Try your old awn; see if it works.( I doubt it, but I might be wrong)

---

### Post by gaijindewanai on 2008-06-09
the problem remains unsolved.

Errors were encountered while processing:
python-awn-trunk
awn-manager-trunk

What should I do? :confused:

---

### Post by Pumalite on 2008-06-09
Try:
sudo apt-get -f install

---

### Post by gaijindewanai on 2008-06-09
I got the same result:

Errors were encountered while processing:
python-awn-trunk
awn-manager-trunk

:(
I'm confused..

---

### Post by Pumalite on 2008-06-09
Copy and paste here the whole output.

---

### Post by gaijindewanai on 2008-06-09
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up python-awn-trunk (0.3.1~bzr264-hardy1-1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-awn-trunk (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of awn-manager-trunk:
 awn-manager-trunk depends on python-awn-trunk; however:
  Package python-awn-trunk is not configured yet.
dpkg: error processing awn-manager-trunk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-awn-trunk
 awn-manager-trunk
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by gaijindewanai on 2008-06-10
Does anyone know how to fix it?

---

### Post by iaculallad on 2008-06-10
> **gaijindewanai said:**
> Does anyone know how to fix it?

Try this:

```
sudo apt-get install awn-core-applets-bzr avant-window-navigator-bzr python-awn-bzr python-feedparser python-libgmail libawn0-bzr
```

---

### Post by gaijindewanai on 2008-06-10
this is the result:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package awn-core-applets-bzr is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  awn-extras-applets-trunk
E: Package awn-core-applets-bzr has no installation candidate

I don't have any idea about this problem.. :(
:confused:

---

### Post by Partyboi2 on 2008-06-10
uninstall/remove these packages
```
awn-manager-trunk awn-extras-applets-trunk
```from a terminal (Applications>Accessories>Terminal) or Synaptic Package Manager. 
Open up Software Sources (System>Admin>Software Sources) on the 3rd party tab untick or remove
```
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
```then add
```
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
```then close software sources.
Then install these packages with synaptic package manger
```
avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
```or  a terminal (Applications>Accessories>Terminal)
```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
```

---

### Post by iaculallad on 2008-06-10
It seems like your current AWN was already messed up so I'll lead you to a site where you could follow the instructions to re/install your AWN apps in Hardy.

[http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)

---

### Post by gaijindewanai on 2008-06-10
Hmm.. I did everything that you've just told me..

but I don't exactly know what I have just done?:confused:(would you mind to tell me?)
Is that gonna fix my problem? (I hope it is:lolflag:)
I thought it was only updating the version..

Thank you, anyway..

---

### Post by gaijindewanai on 2008-06-10
I meant: whatz the different between the TRUNK one and the BZR one?
can anyone explain?:confused:

---

### Post by iaculallad on 2008-06-10
> **gaijindewanai said:**
> I meant: whatz the different between the TRUNK one and the BZR one?
can anyone explain?:confused:

For those who knows the difference, correct me if I'm wrong:

From what I understand: TRUNK is the equivalent of TESTING (test package) while BZR is the equivalent of STABLE. AWN developers naming convention maybe.

---

### Post by gaijindewanai on 2008-06-10
hmm... I got it.
but hey, my stack trash applet is still not working (does it work in your awn?)

---

### Post by ArchCorsair on 2008-06-10
quick question to gaijindewanai:

what screenlet/desklet is that on your desktop to the right displaying all statistics?

---

### Post by gaijindewanai on 2008-06-10
quick answer:
it's not desklet/screenlet. It's CONKY.

---

### Post by ArchCorsair on 2008-06-10
thank you very much! :)

---

