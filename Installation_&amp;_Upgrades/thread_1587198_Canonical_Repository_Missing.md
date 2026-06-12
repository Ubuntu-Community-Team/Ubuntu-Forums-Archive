---
title: "Canonical Repository Missing"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by joey00 on 2010-10-03
This is strange. I must be missing something obvious, but I have tried everything I can think of.

After moving to Lucid, I have no flashplayer.

Eventually, I tracked the problem to a missing Cannonical repository.

I inserted the line in the sources list:
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

Now Synaptic reports:
E: Type 'http://archive.canonical.com/ubuntu' is not known on line 45 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I have re-checked everything I can think of, and remain baffled!
I wondered if the canonical url had changed, but that does not seem to be the case...

:confused:

---

### Post by sikander3786 on 2010-10-03
Post the output of

```
cat /etc/apt/sources.list
```

---

### Post by dino99 on 2010-10-03
you should have:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

---

### Post by joey00 on 2010-10-03
> **dino99 said:**
> you should have:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

That does the trick for the sources list - thanks! :-)

But, unfortunately, I still dont see Flashplayer listed in synaptic. Only flashplugin-nonfree-extrasound (installed). So maybe my assumption was wrong. :(

I tried to install from Adobe but their install reports already installed. 
Similarly the command line: sudo apt-get install adobe-flashplugin.

Firefox 3.6.10 in case somebody asks.

---

### Post by joey00 on 2010-10-03
> **sikander3786 said:**
> Post the output of

```
cat /etc/apt/sources.list
```

This is the amended version (canonical added):

# 
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main restricted

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ftp.uni-erlangen.de/mirrors/ubuntu/](http://ftp.uni-erlangen.de/mirrors/ubuntu/) lucid restricted universe main
deb-src [http://ftp.uni-erlangen.de/mirrors/ubuntu/](http://ftp.uni-erlangen.de/mirrors/ubuntu/) lucid restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.uni-erlangen.de/mirrors/ubuntu/](http://ftp.uni-erlangen.de/mirrors/ubuntu/) lucid-updates restricted universe main
deb-src [http://ftp.uni-erlangen.de/mirrors/ubuntu/](http://ftp.uni-erlangen.de/mirrors/ubuntu/) lucid-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.uni-erlangen.de/mirrors/ubuntu/](http://ftp.uni-erlangen.de/mirrors/ubuntu/) lucid multiverse
deb-src [http://ftp.uni-erlangen.de/mirrors/ubuntu/](http://ftp.uni-erlangen.de/mirrors/ubuntu/) lucid multiverse
deb [http://ftp.uni-erlangen.de/mirrors/ubuntu/](http://ftp.uni-erlangen.de/mirrors/ubuntu/) lucid-updates multiverse
deb-src [http://ftp.uni-erlangen.de/mirrors/ubuntu/](http://ftp.uni-erlangen.de/mirrors/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ftp.uni-erlangen.de/mirrors/ubuntu/](http://ftp.uni-erlangen.de/mirrors/ubuntu/) lucid-backports restricted multiverse universe main

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://ftp.uni-erlangen.de/mirrors/ubuntu/](http://ftp.uni-erlangen.de/mirrors/ubuntu/) lucid-security restricted universe main
deb-src [http://ftp.uni-erlangen.de/mirrors/ubuntu/](http://ftp.uni-erlangen.de/mirrors/ubuntu/) lucid-security restricted
deb [http://ftp.uni-erlangen.de/mirrors/ubuntu/](http://ftp.uni-erlangen.de/mirrors/ubuntu/) lucid-security multiverse
deb-src [http://ftp.uni-erlangen.de/mirrors/ubuntu/](http://ftp.uni-erlangen.de/mirrors/ubuntu/) lucid-security multiverse

---

### Post by sikander3786 on 2010-10-04
Did you mean flashplugin-installer?

```
sudo apt-get install flashplugin-installer
```

It is in the multiverse repository.

Your sources.list seems OK to me.

---

### Post by joey00 on 2010-10-04
> **sikander3786 said:**
> Did you mean flashplugin-installer?

```
sudo apt-get install flashplugin-installer
```It is in the multiverse repository.

Your sources.list seems OK to me.

This is getting tangled. Let me run over the facts again.

Firefox 3.6.10.    Lucid.

I have no flashplayer working in Firefox. It works in Opera I discovered.

Synaptic only shows flashplugin-nonfree-extrasound when searching for flashplayer. It is currently not installed.

flashplugin-installer shows in the list of residual configs. It was uninstalled when I tried to install flashplayer direct from Adobe.

There is no other flashplayer showing in Synaptic, yet it works in Opera. :confused:

I have followed a myriad of install Flashplayer howtos, I still get no response, a claim that flashplayer is not installed or Upgrade to Flash Player 10 for improved playback performance. [Upgrade Now]("http://www.adobe.com/go/getflashplayer/") or [More Info]("http://help.youtube.com/support/youtube/bin/answer.py?answer=95402"). 

I have also run a series of cleans and purges to remove old flashplayers - I dont think I found any, but I ran out of ideas.

Most of these direct to Adobe.

Am I the only one who hates Flashplayer?  ](*,)

---

### Post by sikander3786 on 2010-10-04
You can see this page for some related problems with flash.

[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

You can also try the flash-aid Firefox extension. It solves the issues most of the times.

Flash has been a issue somtimes but to be honest, I never had it, not even on 64-bit. ubuntu-restricted-extras work like a charm for me.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by joey00 on 2010-10-09
> **sikander3786 said:**
> You can see this page for some related problems with flash.

[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

You can also try the flash-aid Firefox extension. It solves the issues most of the times.

Flash has been a issue somtimes but to be honest, I never had it, not even on 64-bit. ubuntu-restricted-extras work like a charm for me.

```
sudo apt-get install ubuntu-restricted-extras
```

Been there, done that. Did the first option: **Flash doesn't work or I get an error on some web pages asking to install flash, but I have already installed the latest version.**

No change. No flashplayer in Firefox. ok in Opera.

The restricted extras line just reports 'already installed'

Flash-aid: Tried for that too. Gives 'not available for your platform'.

I never had a problem either, until installing Lucid...

---

### Post by sikander3786 on 2010-10-10
Type 

```
about:plugins
```

in Firefox address bar. Do you see any Flash plugin listed there? Which one?


[COLOR="Red"]**EDIT:**[/COLOR] Also it will be a good idea to start a new thread regarding Flash.

---

### Post by joey00 on 2010-10-10
> **sikander3786 said:**
> Type 

```
about:plugins
```in Firefox address bar. Do you see any Flash plugin listed there? Which one?


[COLOR=Red]**EDIT:**[/COLOR] Also it will be a good idea to start a new thread regarding Flash.

**No plugins are installed**

hmmm, that doesn't look right...:(

---

### Post by joey00 on 2010-10-17
New thread started:

Flashplayer in Firefox

---

