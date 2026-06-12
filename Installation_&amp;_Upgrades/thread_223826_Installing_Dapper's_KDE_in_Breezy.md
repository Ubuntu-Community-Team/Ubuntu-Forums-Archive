---
title: "Installing Dapper's KDE in Breezy"
date: 2006-07-27
forum: Installation &amp; Upgrades
---

### Post by Roque on 2006-07-27
Hello all, 

I am new to the forum but been using Ubuntu since Hoary. Last week I tried Dapper but it doesn't work with my old modem and video card, so I went back to Breezy. I want to install Dapper's KDE version in Breezy to solve some bugs of the old version. 
So I changed my sources.lst to point to Dapper's repositories and did:

```

sudo apt-get install kubuntu-desktop

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
                   Depends: kaffeine-xine but it is not going to be installed
                   Depends: kdnssd but it is not going to be installed
                   Depends: keep but it is not going to be installed
                   Depends: kmail but it is not going to be installed
                   Depends: kmailcvt but it is not going to be installed
                   Depends: kmplayer-konq-plugins but it is not going to be installed
                   Depends: ksplash-engine-moodin but it is not going to be installed
                   Depends: ktorrent but it is not going to be installed
                   Depends: language-selector-qt but it is not going to be installed
                   Depends: libarts1-akode but it is not going to be installed
                   Depends: openoffice.org-kde but it is not going to be installed
                   Depends: skim but it is not going to be installed
                   Depends: wlassistant but it is not going to be installed
E: Broken packages

```

Then I tried to manually remove these broken dependencies:
```

sudo apt-get remove adept
(etc)

```
But when attempting to install kubuntu-dektop the same message I posted above reappears.

Does anybody know how to fix this? In any case, would this method work?

Many thanks in advance.

---

### Post by aysiu on 2006-07-27
Mixing Dapper and Breezy repositories is a quick way to break your system... as you're seeing now.

The way to "fix" it is to change your repositories to all Breezy repositories and then do ```
sudo apt-get -f install
```

---

### Post by Roque on 2006-07-27
Thanks. But I don't want to fix it, but to upgrade my KDE version without upgrading the rest of the installation (which would break my network and video). Does anyone know how could I do it?

---

### Post by aysiu on 2006-07-27
> **Roque said:**
> Thanks. But I don't want to fix it, but to upgrade my KDE version without upgrading the rest of the installation (which would break my network and video). Does anyone know how could I do it?
Try this:
[http://www.kubuntu.org/announcements/kde-35.php](http://www.kubuntu.org/announcements/kde-35.php)

---

### Post by Roque on 2006-07-27
Ok. I added the key and copied the mirror line to my sources.lst and commented out the rest of the entries. 

Sorry for the dumb question, but what should I do next? :(

---

### Post by aysiu on 2006-07-27
Do not comment out all the other entries but **do** delete all the Dapper entries. Then... ```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by Roque on 2006-07-27
It worked perfectly. Many thanks for your help! :D

Just a question: this upgrade was possible because KDE-3.5 is included (post-release) in Breezy's repositories, but what will happen when Breezy is discontinued? In other words, how could I move to (let's say) KDE-3.8 without having to upgrade the rest of the installation?

---

### Post by aysiu on 2006-07-27
> **Roque said:**
> It worked perfectly. Many thanks for your help! :D

Just a question: this upgrade was possible because KDE-3.5 is included (post-release) in Breezy's repositories, but what will happen when Breezy is discontinued? In other words, how could I move to (let's say) KDE-3.8 without having to upgrade the rest of the installation?
You would probably have to upgrade to Dapper or Edgy.

---

### Post by Roque on 2006-07-28
It's bad news, but thanks anyway.

---

