---
title: "Broken mythtv-backend package and dependencies"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by wammin on 2007-02-27
This is usually my "experimental" machine but I'm using it for work now while my laptop's LCD screen is being repaired.

The other day I got the update manager notification, and often I'll just click install and not even look at what packages are being updated. Well, I did this and since then my 'mythtv-backend' package is seriously broken. Its preventing me from installing any other pacakges. I don't even use Mythtv on this machine anymore, and just want to remove it and get my package manager back in shape but some broken dependency is not letting me.

I tried 'sudo apt-get -f install' and I get:
```
After unpacking 2351kB disk space will be freed.
Do you want to continue [Y/n]? 
dpkg: error processing mythtv-backend (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted (core dumped)
nate@centersage:/var/cache/apt/archives$ Errors were encountered while processing:
 mythtv-backend

```

So then I try to reinstall it by: 'sudo apt-get install -f mythtv-backend':
```
Reading package lists... Donev-backend 
Building dependency tree       
Reading state information... Done
mythtv-backend is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mythtv-backend: Depends: mythtv-common (= 0.20-0.2ubuntu2) but 0.20-0.2ubuntu2.1~proposed1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

It seems like I can't get out of this loop. The package still shows up as broken in Synaptic. Any ideas?

---

### Post by Titus A Duxass on 2007-02-27
> Try 'apt-get -f install' with no packages  - Does this do anything?

What about running an aptitude install?

---

### Post by wammin on 2007-02-27
@Titus - 'apt-get -f install' is the first thing I tried. It still results in this scary error:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  mythtv-frontend pwgen mythtv-common libmyth-0.20 libqt3-mt-mysql
  mythtv-database libjack0.100.0-0 mythtv-backend
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mythtv-backend
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2351kB disk space will be freed.
Do you want to continue [Y/n]? 
dpkg: error processing mythtv-backend (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted (core dumped)
nate@centersage:/var/cache/apt/archives$ Errors were encountered while processing:
 mythtv-backend

```

'aptitude install' gives me the same thing.

See what I mean about being stuck in a loop now?

---

### Post by wammin on 2007-02-28
* bump * 

HELP please? I've spent way too much time on this and getting nowhere. The big problem is that I cant install anything now using apt-get or Synaptic. I always get the prompt saying:

You might want to run `apt-get -f install' to correct these

But when I do so, it fails on this broken mythtv-backend package with the error message already posted above. Is there a way to manually remove this package?

---

### Post by wammin on 2007-03-21
Ok ... I'm still having this problem with the broken package, and I can't use apt-get to install anything until it's fixed. I have exhausted all my knowledge and resources. I am very frustrated and I *really* don't want to reinstall ubuntu.

**I am offering $30 USD to anyone that can help me fix this!** I'll provide you with SSH root access to my machine (once i verify that you're not a bad guy). Payment via PayPal.

Reply or PM if you are interested and think you can help.

Thanks!

---

### Post by oliveri on 2007-08-28
Have a look at this:

[http://ubuntuforums.org/showthread.php?t=462135/](http://ubuntuforums.org/showthread.php?t=462135/)

If it works for you, please donate the $30 to Pathways to Housing in NYC.

Cheers!

---

