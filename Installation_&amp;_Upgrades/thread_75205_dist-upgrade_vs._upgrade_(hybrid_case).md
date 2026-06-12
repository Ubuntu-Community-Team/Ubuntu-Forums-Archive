---
title: "dist-upgrade vs. upgrade (hybrid case)"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by skoal on 2005-10-13
Howdy,

What about my case? I'm a hybrid...

1. I installed 'kubuntu-desktop' from a Hoary 5.04 Ubuntu (not Kubuntu) CD
2. I used server install (and don't have Gnome installed at all)
3. I upgraded to KDE 3.4.2 via [here](http://ubuntuforums.org/showthread.php?t=52499&highlight=kde)
4. I'm only using a custom built 2.6.12 kernel, compiled with gcc-3.3 (stock hoary). 

Yeah, I know I know what you're saying too.  But that's just how I roll...

*You may have done just 1 of those 4 (but not all) like me, so I seek your upgrading wisdom here...*

I. **dist-upgrade**

*Need to get 627MB of archives*. 
*After unpacking 293MB of additional disk space will be used*.
...and get a bunch of stuff installed which I don't want, and don't have installed already.

-> errors? yes.

If I follow the very first step from the sticky, when I 'sudo apt-get install kubuntu-desktop', I get:
```
skoal@morpheus://~ $ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: adept but it is not going to be installed
                   Depends: bluez-pcmcia-support but it is not going to be installed
                   Depends: bluez-utils but it is not going to be installed
                   Depends: dbus but it is not going to be installed
                   Depends: ivman but it is not going to be installed
                   Depends: kaffeine-gstreamer but it is not going to be installed
                   Depends: katapult but it is not going to be installed
                   Depends: kde-guidance but it is not going to be installed
                   Depends: kde-systemsettings but it is not going to be installed
                   Depends: kdebluetooth but it is not going to be installed
                   Depends: kio-apt but it is not going to be installed
                   Depends: kio-locate but it is not going to be installed
                   Depends: krita but it is not going to be installed
                   Depends: ksystemlog but it is not going to be installed
                   Depends: kubuntu-konqueror-shortcuts but it is not going to be installed
                   Depends: libgl1-mesa but it is not going to be installed
                   Depends: openoffice.org2-kde but it is not going to be installed
                   Depends: qca-tls but it is not going to be installed
                   Depends: speedcrunch but it is not going to be installed
E: Broken packages
```
II. **upgrade**

*Need to get 216MB of archives*.
*After unpacking 20.9MB of additional disk space will be used*.

-> errors? no.

...but I don't know what I'll be left with afterwards, _and_ it looks like it's upgrading my gcc-3.3 base too.

**QUESTIONS**:

What version of KDE does breezy have? 

Could that error above be from me commenting out the 'kde.org' repos (from 3. above) and only using 'archive.ubuntu.com' instead?

Anybody upgrade to breezy this way, piece mealwise like (changing repos from hoary to breezy and using update only)?

Similiar experiences? Suggestions? I don't want to fubar my system.

\\//_

---

### Post by Storm Rider on 2005-10-13
Breezy has KDE 3.4.2  

KDE 3.4.3 was just released today.:KS

Hey, just noticed Kubuntu has KDE3.4.3

---

### Post by Storm Rider on 2005-10-13
Can't offer much help on the updates.

I have run apt-get upgrade and had a few errors.  I think the suggested fix was to run dist-upgrade.  Ever since, I've been running sudo apt-get dist-upgrade.  Everything seems fine to me.

---

### Post by skoal on 2005-10-13
Thanks, storm rider.

If breezy has 3.4.3 KDE, then I definitely want to comment out the 'kde.org' in my 'sources.list'.  I can't get past that error above though with 'dist-upgrade'.

I think I'll snatch some kubuntu ISO lovin' off of bittorent in the meantime and piecemeal it back together that way.  If that don't work, I guess I have to go through the whole install process all over again, which doesn't bid well for someone like me who customizes everything in between releases.  I wish there were a way to do this with just 'upgrade' instead.  I just don't know how reliably...

\\//_

---

