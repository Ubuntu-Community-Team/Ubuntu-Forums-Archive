---
title: "[SOLVED] Software Source not displayed in Jaunty"
date: 2008-11-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2008-11-02
I've just followed Mazza558's [COLOR="Red"][post]("http://ubuntuforums.org/showthread.php?t=966306")[/COLOR] on upgrading to Jaunty. When I now go to Software Sources, it asks for my password and then nothing happens (apart from the password box closing). I've checked my sources.list file and it's modified as per the original post.
If I go to Synaptic and select Settings-Repositories, I just get a message box 'Repositories Changed', select Reload. This is repeatable when ever Settings-Repositories selected.

---

### Post by Gina on 2008-11-02
Oh the joys of testing pre-ready-for-testing software :lolflag:

---

### Post by plun on 2008-11-02
Broken....

```
plun@plun:~/$ **sudo software-properties-gtk**
[sudo] password for plun: 
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 78, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 516, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.5/site-packages/aptsources/distro.py", line 85, in get_sources
    "[B]Error: could not find a distribution template")
aptsources.distro.NoDistroTemplateException[/B]

```


With **sudo alacarte** you can see all commands for GUIs > right click > properties.

You can only survive this time from the terminal and the probability for a total break is high....:)

---

### Post by smartboyathome on 2008-11-02
> **plun said:**
> Broken....

```
plun@plun:~/$ **sudo software-properties-gtk**
[sudo] password for plun: 
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 78, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 516, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.5/site-packages/aptsources/distro.py", line 85, in get_sources
    "[B]Error: could not find a distribution template")
aptsources.distro.NoDistroTemplateException[/B]

```


With **sudo alacarte** you can see all commands for GUIs > right click > properties.

You can only survive this time from the terminal and the probability for a total break is high....:)

Hooray for breakage! :D

---

### Post by plun on 2008-11-02
> **smartboyathome said:**
> Hooray for breakage! :D

Yup... you can learn a lot out of breakages  :)

Survive without GUIs is a challenge...  


Debians apt-manual is recommended.
[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)

Also how Ubuntus package system works.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by smartboyathome on 2008-11-02
I just recommend installing irssi and links for when Ubuntu's GUI breaks. That way, you can get on an IRC channel or the forums when it breaks. Though then again, I'm experienced with command line stuff since I have had a few bad Arch installs. :p

---

### Post by Eclipse. on 2008-11-02
> **Kevbert said:**
> I've just followed Mazza558's [COLOR=Red][post]("http://ubuntuforums.org/showthread.php?t=966306")[/COLOR] on upgrading to Jaunty. When I now go to Software Sources, it asks for my password and then nothing happens (apart from the password box closing). I've checked my sources.list file and it's modified as per the original post.
If I go to Synaptic and select Settings-Repositories, I just get a message box 'Repositories Changed', select Reload. This is repeatable when ever Settings-Repositories selected.

GUI's break all the time during development.You will get used to it.:)

Jockey-gtk is the worse for it.lol

---

### Post by Kevbert on 2008-11-03
> **plun said:**
> Broken....

```
plun@plun:~/$ **sudo software-properties-gtk**
[sudo] password for plun: 
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 78, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 516, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.5/site-packages/aptsources/distro.py", line 85, in get_sources
    "[B]Error: could not find a distribution template")
aptsources.distro.NoDistroTemplateException[/B]

```


With **sudo alacarte** you can see all commands for GUIs > right click > properties.

You can only survive this time from the terminal and the probability for a total break is high....:)

Thanks Plun. I'll raise this as a bug. I'll also look into that new command you've introduced me to. Thanks again.

---

### Post by plun on 2008-11-03
> **Kevbert said:**
> Thanks Plun. I'll raise this as a bug. I'll also look into that new command you've introduced me to. Thanks again.

We cannot define this as a bug, more like a  "As is".....

The repos are not officially open and everything before Alpha 1 is a "adventure".

I hope you have backups and also /home on a separate partition. 

Just take it as a challenge...:)

---

### Post by Kevbert on 2008-11-03
Someone has already beaten me reporting this on [[COLOR="Red"]launchpad.[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/292691"). I've just added a comment.
There seems to be quite a few bug reports on Jaunty already.
Regarding 'as is' problems. Is there anywhere I can see known problems other than in launchpad ? Release notes ?

---

### Post by plun on 2008-11-03
> **Kevbert said:**
> Someone has already beaten me reporting this on [[COLOR="Red"]launchpad.[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/292691"). I've just added a comment.
There seems to be quite a few bug reports on Jaunty already.
Regarding 'as is' problems. Is there anywhere I can see known problems other than in launchpad ? Release notes ?

Well.. there are no "releases"....:) 

You can follow Ubuntu mailing lists

Development announces
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/](https://lists.ubuntu.com/archives/ubuntu-devel-announce/)

Development discuss
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/)

EDIT  Jaunty changes
[https://lists.ubuntu.com/archives/jaunty-changes/](https://lists.ubuntu.com/archives/jaunty-changes/)

Jaunty schedule
[https://wiki.ubuntu.com/JauntyReleaseSchedule](https://wiki.ubuntu.com/JauntyReleaseSchedule)

Jaunty wiki
[https://wiki.ubuntu.com/JauntyJackalope](https://wiki.ubuntu.com/JauntyJackalope)

I also saw a Community Cafe posting and its more like "anarchy"...

This one is important about /home on a separate partition
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)


"Read and read and read"....   and don´t fill Launchpad with "junk"...IMHO  :)

---

### Post by Kevbert on 2008-11-03
Thanks again plun. Yes, I don't want to report bugs that are already known about or expected to occur as a result of the build status. The problem is knowing when a problem really is a bug and we should not load the developers with useless dross.
I've just subscribed to the Jaunty changes and already subscribe to the development changes.

---

### Post by ronacc on 2008-11-03
darn I missed this one , I always just load /etc/apt/sources.list into gedit and search/replace oldname/newname  :)

---

### Post by DougieFresh4U on 2008-11-03
I am not surprised about the "Software Sources" drama, as in a few of the previous releases  (Edgy, Feisty) access to "Software Sources" was 'broken' in early stages as well.

---

### Post by Kevbert on 2008-11-03
> **DougieFresh4U said:**
> I am not surprised about the "Software Sources" drama, as in a few of the previous releases  (Edgy, Feisty) access to "Software Sources" was 'broken' in early stages as well.

Thanks DougieFresh4U. So its deja vu. Can you remember any other typical problems that we need to look out for ?

---

### Post by autocrosser on 2008-11-03
YES!!!! Bring on the BREAKAGE!!!!!!

> **smartboyathome said:**
> Hooray for breakage! :D

---

### Post by Kevbert on 2008-11-03
> **autocrosser said:**
> YES!!!! Bring on the BREAKAGE!!!!!!

The software is only as good as it's weakest link (goodbye)...no seriously the more we can break, the greater the fun. Is there any specific packages we can target ? Newly downloaded today was a rhythmbox and totem package, but the versions seem to be the same as Intrepid.

---

