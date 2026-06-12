---
title: "'Error: BrokenCount&gt;0'"
date: 2019-04-02
forum: Installation &amp; Upgrades
---

### Post by rocker996 on 2019-04-02
The following message appeared on my Ubuntu 16.04 LTS:
An error ocurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what's wrong. The error message was: 'Error: BrokenCount>0'

I ran
```
sudo apt-get install -f[/B] and the output was the following:[INDENT][B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  python3-qgis-common
The following NEW packages will be installed:
  python3-qgis-common
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0 B/4296 kB of archives.
After this operation, 14,6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 261736 files and directories currently installed.)
Preparing to unpack .../python3-qgis-common_3.4.6+dfsg-1~xenial1_all.deb ...
Unpacking python3-qgis-common (3.4.6+dfsg-1~xenial1) ...
dpkg: error processing archive /var/cache/apt/archives/python3-qgis-common_3.4.6+dfsg-1~xenial1_all.deb (--unpack):
 trying to overwrite '/usr/share/qgis/python/plugins/processing/script/ScriptAlgorithmProvider.py', which is also in package python-qgis-common 1:2.18.16+24xenial
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python3-qgis-common_3.4.6+dfsg-1~xenial1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Could you guys help me fixing this issue, since I'm a beginner on Linux? Thanks!

---

### Post by Rubi1200 on 2019-04-02
Hi and welcome to the forum :-)

Please try this and post back if there were errors or the problem was resolved:

```
sudo dpkg --configure -a
```

---

### Post by rocker996 on 2019-04-03
Output:
[B]dpkg: dependency problems prevent configuration of python3-qgis:
 python3-qgis depends on python3-qgis-common (= 3.4.6+dfsg-1~xenial1); however:
  Package python3-qgis-common is not installed.

dpkg: error processing package python3-qgis (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3-qgis
[/B]

---

### Post by rocker996 on 2019-04-03
Output:
[B]dpkg: dependency problems prevent configuration of python3-qgis:
 python3-qgis depends on python3-qgis-common (= 3.4.6+dfsg-1~xenial1); however:
  Package python3-qgis-common is not installed.

dpkg: error processing package python3-qgis (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3-qgis
[/B]

---

### Post by Rubi1200 on 2019-04-03
I suggest removing the package:

```
sudo apt-get remove --purge python3-qgis
```

The run this again:

```
udo dpkg --configure -a
```

If there are no more errors then try installing again:

```
sudo apt-get install python3-qgis
```

Obviously, if dpkg does return errors post them here before trying to reinstall so we can try and figure out what is going on.

---

### Post by rocker996 on 2019-04-03
dpkg didn't return any error, but when running **sudo apt-get install python3-qgis **it returned the following:

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  python3-qgis-common
The following NEW packages will be installed:
  python3-qgis python3-qgis-common
0 upgraded, 2 newly installed, 0 to remove and 12 not upgraded.
Need to get 0 B/12,6 MB of archives.
After this operation, 63,5 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 261678 files and directories currently installed.)
Preparing to unpack .../python3-qgis-common_3.4.6+dfsg-1~xenial1_all.deb ...
Unpacking python3-qgis-common (3.4.6+dfsg-1~xenial1) ...
dpkg: error processing archive /var/cache/apt/archives/python3-qgis-common_3.4.6+dfsg-1~xenial1_all.deb (--unpack):
 trying to overwrite '/usr/share/qgis/python/plugins/processing/script/ScriptAlgorithmProvider.py', which is also in package python-qgis-common 1:2.18.16+24xenial
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package python3-qgis.
Preparing to unpack .../python3-qgis_3.4.6+dfsg-1~xenial1_amd64.deb ...
Unpacking python3-qgis (3.4.6+dfsg-1~xenial1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/python3-qgis-common_3.4.6+dfsg-1~xenial1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B]

---

### Post by Rubi1200 on 2019-04-03
Let's see if cleaning things up a bit helps:

```
sudo apt-get clean
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
```

Post back if there are errors please.

---

### Post by rocker996 on 2019-04-03
Returned the same errors as before

---

### Post by Rubi1200 on 2019-04-03
Couple of questions:

Did you recently upgrade, if yes from which version to which new version?

Were you trying to compile from source or adding from the APT directory?

---

### Post by rocker996 on 2019-04-03
I did not.

A few days ago, in order to install a program I added a few lines to sources.list

---

### Post by Rubi1200 on 2019-04-03
That may be why you are having issues. Did you make a copy of the sources.list before adding new lines?

In any event, let's take a look at the PPAs and sources.list:

```
grep -H -v ^# /etc/apt/sources.list.d/*
```

Command is case-sensitive, capital H

Thanks.

---

### Post by rocker996 on 2019-04-08
I did not make a copy of the sources.list.
Here's the output of the command:

[ATTACH=CONFIG]282990[/ATTACH]

---

### Post by Rubi1200 on 2019-04-08
I would try this to figure out which repository might be causing problems:

Go to Settings >> Software & Updates >> Other Software and uncheck third party repositories, either all of them or one at a time until you figure out which is causing the error.

If you do each one separately then try ```
sudo apt-get update install -f
``` each time.

Hopefully you will at least know which one is causing the problem after this.

---

### Post by rocker996 on 2019-04-08
I have no 3rd party repositories option in here...
[ATTACH=CONFIG]282991[/ATTACH]

---

### Post by DuckHook on 2019-04-08
You have a ton of third parties activated. That's what PPAs and all of those other repos are.

Uncheck ***everything*** on the page you've posted (but ***only*** what is on ***that*** page and no others), then run the basic:```
sudo apt update && sudo apt full-upgrade && sudo apt autoremove && sudo apt clean
```…and post output back to this thread.

FWIW, new Linux users (and especially those coming from Windows) often make the error of adding tons of PPAs and third party repos to their install. This is required in the Windows world where every app is jealously guarded by their developers so must be downloaded from their site, but in the Linux-sphere, anything that a new user is likely to use can be found in the official repo. Therefore, it is unwise to attach any further PPAs or outside repos. Doing so is the primary cause of the sort of dependency hell that you are experiencing. Chasing down such problems is also a cold and clammy exercise.

If the above doesn't work, you may have to try *ppa-purge*. This will remove not only the PPA, but also the app that was installed by the PPA. However,

[LIST=1]
[*]it may not work on the non-PPA 3rd party repos you've installed (though you can try), and
[*]even *ppa-purge* may fail if you are already in dependency hell.
[/LIST]
But let's try unchecking everything first, proceeding to next step only if necessary.

---

### Post by rocker996 on 2019-04-13
After unchecking all 3rd party dependencies, I ran **sudo apt-get install -f **and then ran the command line above and it worked out perfectly!
Thank you so much for your patience and advice!

---

### Post by Rubi1200 on 2019-04-13
Glad to hear you got this sorted out :-)

Please mark Solved using the Thread Tools at the top of the page.

Thanks.

---

### Post by DuckHook on 2019-04-13
> **rocker996 said:**
> &#8230;and it worked out perfectly!&#8230;

> **Rubi1200 said:**
> &#8230;Please mark Solved using the Thread Tools at the top of the page&#8230;

@rocker996

I'm afraid you are only half done at this point.

> **DuckHook said:**
> You have a ton of third parties activated. &#8230;new Linux users (and especially those coming from Windows) often make the error of adding tons of PPAs and third party repos to their install. &#8230;Doing so is the primary cause of the sort of dependency hell that you are experiencing.

If you haven't done so, it's time to consider removing some (or all) of those PPAs and outside repos because as soon as you turn them on, one or more of them will go back to making trouble for you. [This link]("http://www.ubuntubuzz.com/2012/02/newbie-guide-how-to-use-ppa-purge.html") gives a good brief description of and instructions for *ppa-purge*, which removes not only the PPA but all the apps and associated dependency conflicts that may have been installed by it and that are the cause of your problem.

---

