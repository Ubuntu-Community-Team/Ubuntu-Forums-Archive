---
title: "Unable to install Adobe Flash on fresh beta install"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bsmith1051 on 2009-10-06
I've just completed a fresh install of the Karmic 9.10 Beta on an IBM Thinkpad T23 with an S3 videocard.  When I try to install Flash through the repositories it says 'unsupported' and when I try to install from the .DEB (downloaded from Adobe.com) it reports a conflict with "libns-dev" something or other.

Is there a hardware dependency here, something that my old S3 videocard is causing?  Is the official Adobe DEB incompatible with the Karmic Beta?

P.S. No, I have not tried either of the open-source Flash alternatives.

---

### Post by gexi on 2009-10-06
have you tried installing the package ubuntu-restricted-extras? flash should be included, maybe you were trying to install the wrong package(s)?

---

### Post by bsmith1051 on 2009-10-06
I forgot to mention: the first thing I tried was to let Firefox look for add-in's but it failed.

re packages, I confirmed that all the repositories were enabled (e.g. universe and multiverse) then did a quick search for 'flash' but didn't see the regular flash package.

What's the 'ubuntu-restricted-extras' package?  That sounds suspiciously like a 'codec pak' which I've learned to avoid.  All I want to install is the official Flash.

P.S. I have gotten some of these details wrong, I'm at work right now and don't have the laptop here to double-check.  I'll try again tonight, hopefully.

---

### Post by slakkie on 2009-10-06
See if you can install these packages:

```

http://archive.canonical.com karmic/partner              adobe-flashplugin                   10.0.22.87-2jaunty1
http://nl.archive.ubuntu.com karmic/multiverse           flashplugin-installer               10.0.32.18ubuntu1
http://nl.archive.ubuntu.com karmic/multiverse           flashplugin-nonfree                 10.0.32.18ubuntu1

```

Included the repo's from which they come.

---

### Post by bsmith1051 on 2009-10-07
bah!  All the fancier options didn't work well but, in fact, the 'first choice' Software Store worked fine.  I just was thrown by the fact that the official Flash is still labeled "Macromedia Flash" rather than "Adobe Flash" (so I didn't find it before).

It's now working fine.

---

### Post by emarkay on 2009-10-07
I had a bugger of a time last night with this - it was something about he "iceape" and after much angst I found that by deleting (in root) all the files that say "flashplugin" (oh my, or was it "Flashinstaller) and the relevant directories, as well as disabling any flash related (FlashBlock, NoScript) plugins in Firefox, and then reinstalling from the Repos, all was well.

The package was so "broken" I couldn't install or uninstall it in anyway known!  

I am sure it's related to Beta test, but I DID install it from the Adobe site, for that is the newest release (I even am told that "there is an older version available in teh repositories...") and I think that was a factor, too.

Just a tale of woe for those interested.  :)

---

### Post by beow on 2009-10-07
I had to run 

```
$ sudo aptitude reinstall flashplugin-installer
```

to get it to work. Probably was some problem with downloading the files from adobe.

---

### Post by lagamemnon on 2009-10-17
I'm having this problem right now, nothing I'm doing seems to work, posted some of the output below.

How do I remove everything with "flashplugin" in the title? rm something?

$ sudo aptitude reinstall flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
flashplugin-installer is not currently installed, so it will not be reinstalled.
flashplugin-installer is not currently installed, so it will not be reinstalled.
The following partially installed packages will be configured:
  adobe-flashplugin 
0 packages upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

And also
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

---

### Post by bsmith1051 on 2009-10-18
> **lagamemnon said:**
> I'm having this problem right now
How did you originally install it, from the new Ubuntu Store (automatic) or from the Adobe web-site (manually) ?

---

