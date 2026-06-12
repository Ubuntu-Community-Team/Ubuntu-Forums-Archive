---
title: "Problems with Updates &amp; Software, add-apt-repository and &quot;Can't find a source ...&quot;"
date: 2015-04-30
forum: Installation &amp; Upgrades
---

### Post by braneludio on 2015-04-30
Hi guys,

   Well as one guy said "I know I shouldn't have done it, but I did it anyway ..." I installed different DE-s on my 14.04.2 Ubuntu including: gnome-shell, kde, xubuntu, mate, cinammon, awesome, i3wm and pantheon. This messed up my unity (mainly kde and pantheon which required gnome3 ppas), so I wanted to get back to unity and had to downgrade a lot of installed stuff using aptitude build-dep ...

   So far I've managed to get back almost to square 1 (after 2 months of fun : ) but there are a couple of things left to fix:

1. I can't start Software and Updates
   I tried reinstalling but I get:

```
$ sudo aptitude reinstall update-manager
The following packages will be REINSTALLED:
  update-manager 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 9 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
E: Can't find a source to download version '1:0.196.13' of 'update-manager:amd64'
E: Can't find a source to download version '1:0.196.13' of 'update-manager:amd64'
E: Internal error: couldn't generate list of packages to download
```

   I also tried reinstalling python3-apt but I get:

```
$ sudo aptitude reinstall python3-apt
The following packages will be REINSTALLED:
  python3-apt 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 9 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
E: Can't find a source to download version '0.9.3.5+elementary4~ubuntu0.3.1' of 'python3-apt:amd64'
E: Can't find a source to download version '0.9.3.5+elementary4~ubuntu0.3.1' of 'python3-apt:amd64'
E: Internal error: couldn't generate list of packages to download
```


2. I can't add repositories using add-apt-repository 
    I get this:

```
$ sudo add-apt-repository ppa:conky-companions/ppa 
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 91, in <module>
    sp = SoftwareProperties(options=options)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 109, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 599, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 89, in get_sources
    (self.id, self.codename))
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template for Ubuntu/n/a
```


3. my power indicator doesn't refresh
    I tried reinstalling but also get 

```
$ sudo aptitude reinstall gnome-power-manager 
The following packages will be REINSTALLED:
  gnome-power-manager 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 9 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
E: Can't find a source to download version '3.8.2-1ubuntu3~trusty1.1' of 'gnome-power-manager:amd64'
E: Can't find a source to download version '3.8.2-1ubuntu3~trusty1.1' of 'gnome-power-manager:amd64'
E: Internal error: couldn't generate list of packages to download
```

I dunno if it's all connected - but I sure don't want to do a clean install because of all the stuff I need to redo ... help?

Branko

---

### Post by v3.xx on 2015-04-30
> E: Can't find a source
Whats in your sources list?
```
cat /etc/apt/sources.list
```

---

### Post by braneludio on 2015-05-01
Yeah I tried resetting my source.list after purging some of the packages  didn't finish nice and tidy. The thing is I wanted to purge all this  new ppas that i added but some of them wanted to remove ubuntu-desktop  and I thought "well that doesn't sound good" (now I know I'm wrong : )  so I stopped the purging midway. 

Anyway to get a nice and fresh source.list I used [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) to get the list bellow. I also emptied /etc/apt/sources.list.d completely. I don't know where elementaryos still stands a source for some of the bins .. 

```
# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

# deb-src [http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu](http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu) trusty main

# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
deb [http://liveusb.info/multisystem/depot](http://liveusb.info/multisystem/depot) all main
# deb-src [http://liveusb.info/multisystem/depot](http://liveusb.info/multisystem/depot) all main

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main 
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main 

deb [http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu](http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu) trusty main 
deb-src [http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu](http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu) trusty main 

# Conky
deb [http://ppa.launchpad.net/teejee2008/ppa/ubuntu](http://ppa.launchpad.net/teejee2008/ppa/ubuntu) trusty main
```

---

### Post by v3.xx on 2015-05-02
Why do you have your ppa's in your sources.list and not in sources.list.d?

Please run a update in terminal and look for errors.  If the ppas come up in error, comment out (#) the offending ppa in the sources list for now.  Did you install these ppa using apt-add-repository at some point?  

Is all this conflict being cause by an version upgrade to 14o4?  

You run a lot of environments.  The only one that would concern me would be gnome-shell.  I do not run it myself, but have read reports of it (at times), not playing nice with other desktops.

---

### Post by braneludio on 2015-05-02
I added all of these directly in the sources.list, actually all of them except the last 3: deb [xorg-edgers]("http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu"), [systray-trusty]("http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu") and Conky were generated by [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/). Adding stuff using add-apt-repository doesn't work any more. I cleared sources.list.d/ because I couldn't figure out why ubuntu can't find the sources to reinstall the stuff that's not working. Otherwise, apt-get update doesn't give any errors except a GPG error because I didn't add the keys for the last repo-s.

I think the biggest trouble came when I was trying to install Pantheon DE. This necessitated adding gnome-3 ppa's, so maybe you're right with the gnome-shell thing. 

Cheers,
Branko

---

### Post by QIII on 2015-05-02
@braneludio:

When you are posting blocks of text copied from the terminal, please use code tags:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

This helps others distinguish what is from the terminal from the rest of your text.

---

### Post by v3.xx on 2015-05-02
Ok, what if you try a dist-upgrade and do some cleaning.
```
sudo apt-get clean && sudo apt-get autoremove && cd /varlib/apt && sudo mv list list.old && sudo mkdir -p list/partial && sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get -f install
```
The last command attempts to fix broken packages and may give a useful error message.

Seen this?
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Internal+error%3A+couldn%27t+generate+list+of+packages+to+download&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Internal+error%3A+couldn%27t+generate+list+of+packages+to+download&sa=Search&cof=FORID:9)

---

### Post by braneludio on 2015-05-05
Ok thanks! Sorry about that - I was wondering how to do it : )

---

### Post by braneludio on 2015-05-05
I've tried clean and autoremove to no avail. I'll try upgrading the distro, but first I have to back things up : )

---

### Post by v3.xx on 2015-05-05
A dist-upgrade is not a version-upgrade.

[http://manpages.ubuntu.com/manpages/utopic/en/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/utopic/en/man8/apt-get.8.html)

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by Bashing-om on 2015-05-05
v3.xx; braneludio; Hey guys;

I am invited to join this thread, see what we can do.

v3.xx has my thoughts and we follow his lead  as he is the 1st responder.

[INDENT]upfront, maybe
[INDENT][INDENT][INDENT]look'n for that needle in the haystack
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by v3.xx on 2015-05-05
Here's Bashing-om reply to my PM.

> So many DE's installed, and we have a conflict of interest when the OP  tried to remove, No telling what will now have to be replaced, just  trial and error with ' apt-get upgrade ' .
Make sure all the PPAs are supported in trusty; temporarily disable all of them until the package manager is stable;
results -> apt-get -f install ?
results -> sudo dpkg -C -> ?

Focus on getting the system stable using the default DE ,unity, up and running as the display manager .
  Run sudo dpkg-reconfigure lightdm to set the default display manager 

Then we see where we stand.

---

