---
title: "Problem with upgrade to hoary"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by ivan.virtuale on 2005-04-08
Sorry, I get a big problem when I try to upgrade from ubuntu 4.10 to hoary.
I change the source.list in this way:

eb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

I download the list of the new packets and when i try to do 'apt-get dist-upgrade
' i receive this message :

The following packages have been kept back:
firestarter gnome-cpufreq-applet gstreamer0.8-swfdec gtk2-engines-crux
gtk2-engines-lighthouseblue gtkhtml3.2 libgal2.2-common libgcrypt7
libgnutls10 libgtkhtml3.2-11 lufs-cryptofs mc python-hip python2.3-examples
python2.3-gdbm python2.3-librdf python2.3-mpz python2.3-osd python2.3-pycurl
python2.3-pymacs python2.3-pyorbit python2.3-reportlab python2.3-sqlite
xfree86-common xserver-xfree86

Why?
How can I force to upgrade from xfree86 to xorg?
Ivan

---

### Post by kuleali on 2005-04-08
try using synaptic.

---

### Post by p!=f on 2005-04-08
Looks like you're missing main repository.
> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary **main** universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary **main** universe


Then you should update and dist-upgrade safely. Feel free to post here if you get any problems.

---

### Post by ivan.virtuale on 2005-04-08
[QUOTE=kuleali]try using synaptic.[/QUOTE]
 Thank you, but I used synaptic ...

I think that my 'apt-get update' didn't download all the packets...
I changed my sources.list in this whay and NOW i'm downloading 400MB...
But i still have 1 packet that I sure will give me problem:
The following packages have been kept back:
  x-window-system-core


My  sources.list:
--------------------------------------------------------------------------------------------
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security univers
-------------------------------------------------------------------------------------------------------

I just saw that the final release of Kubuntu is out... and our distro?

---

### Post by Leif on 2005-04-08
go ahead with the upgrade, and then fire up synaptic, look for xserver-xorg and install it. (apt-get install -f xserver-xorg if you're a cli person, i think). this will sort out that final package

---

### Post by arrizaba on 2005-04-08
Hey! I also got that package uninstalled. This is not a common feature of upgrading to Hoary, isn't it?

---

### Post by Leif on 2005-04-08
It happened to me too, and when I looked for it, someone else had already had the problem, so I guess it's kinda common.

---

### Post by jobezone on 2005-04-08
[QUOTE=ivan.virtuale]Sorry, I get a big problem when I try to upgrade from ubuntu 4.10 to hoary.
I change the source.list in this way:

eb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

I download the list of the new packets and when i try to do 'apt-get dist-upgrade
' i receive this message :

The following packages have been kept back:
firestarter gnome-cpufreq-applet gstreamer0.8-swfdec gtk2-engines-crux
gtk2-engines-lighthouseblue gtkhtml3.2 libgal2.2-common libgcrypt7
libgnutls10 libgtkhtml3.2-11 lufs-cryptofs mc python-hip python2.3-examples
python2.3-gdbm python2.3-librdf python2.3-mpz python2.3-osd python2.3-pycurl
python2.3-pymacs python2.3-pyorbit python2.3-reportlab python2.3-sqlite
xfree86-common xserver-xfree86

Why?
How can I force to upgrade from xfree86 to xorg?
Ivan[/QUOTE]
 You shouldn't **dist-upgrade**having a repository line pointing to **Universe**, since it may cause some Universe less tested packages overwrite ubuntu oficial packages.


You can get yourself out of sources.list crazyness by launching Synaptic, configure repositories, and make sure you have Hoary, Hoary-update and Hoary-security repositories, and for each only the sections main and restricted (no Universe or Multivers). After the dist-upgrade(smart upgrade in synaptic), you can add the universe and/or multiverse sections.

Here's how sources.list would look like:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted

---

### Post by p!=f on 2005-04-08
[QUOTE=jobezone]You shouldn't **dist-upgrade**having a repository line pointing to **Universe**, since it may cause some Universe less tested packages overwrite ubuntu oficial packages.
[/QUOTE]
Ubuntu officially supported packages are only in the section main. Your statement basically says there're plenty of doubled packages, ones in main, others in universe but with various versions... which is not true. :)
Having universe (multiverse, ...) "activated" during dist-upgrade should have no effect on the upgrade process itself unless you have repositories offering same packages with different versions.

---

### Post by jobezone on 2005-04-08
[QUOTE=p!=f]Ubuntu officially supported packages are only in the section main. Your statement basically says there're plenty of doubled packages, ones in main, others in universe but with various versions... which is not true. :)
Having universe (multiverse, ...) "activated" during dist-upgrade should have no effect on the upgrade process itself unless you have repositories offering same packages with different versions.[/QUOTE]
 hmm..you're absolutely right, never thought about that too well. mea culpa.
So, there's no problem with having universe on? What if some packages in universe depend on others of universe, which we might not want to have, but may make the system react differently, especially if they are libraries? is this a reasonable risk, or not quite, since universe is basically a snapshot of debian unstable, which actually acts in a very stable way?(I used it for years before ubuntu)

---

### Post by p!=f on 2005-04-08
[QUOTE=jobezone]
So, there's no problem with having universe on? 
[/quote]
I can't say "no problem" but you should be safe. :)
[QUOTE=jobezone]
What if some packages in universe depend on others of universe, which we might not want to have, but may make the system react differently, especially if they are libraries? is this a reasonable risk, or not quite, since universe is basically a snapshot of debian unstable, which actually acts in a very stable way?(I used it for years before ubuntu)[/QUOTE]
For more detailed technical answer ask your nearest engineer :) but here's my opinion.
I don't think it's risky. If you install some application which depends on a library, this library should not affect whole system stability but just applications which were compiled against it or just part of an application functionality. Core libraries are in the main (supported) section.
Universe is Debian Unstable snapshot (maybe with some other packages not found in Sid) but recompiled from sources for Ubuntu as shown in the example below.
```

[~] > wajig policy anjuta blender
anjuta:
  Installed: 1.2.2-6ubuntu1
  Candidate: 1.2.2-6ubuntu1
  Version table:
 *** 1.2.2-6ubuntu1 0
        500 http://archive.ubuntu.com hoary/universe Packages
        100 /var/lib/dpkg/status
blender:
  Installed: 2.36-1ubuntu1
  Candidate: 2.36-1ubuntu1
  Version table:
 *** 2.36-1ubuntu1 0
        500 http://archive.ubuntu.com hoary/universe Packages
        100 /var/lib/dpkg/status

```

---

