---
title: "[SOLVED] Major apt-get issues (fubar'd), help appreciated!"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by urIkon on 2007-09-13
Background:
A few days ago, started having some awkward HD issues, lead to nasty HD failure, ran some fsck, seemed to fix everything, but lost some files in /var/lib/dpkg/info, *.list files to be exact.

Everything seemed to be in working order, except for the first time I ran apt, when I was hit with a whole bunch of these errors:

```
dpkg: serious warning: files list file for package "man-db" missing, assuming package has no files installed.

dpkg: serious warning: files list file for package "scribus" missing, assuming package has no files installed.


dpkg: serious warning: files list file for package "launchpad-integration" missing, assuming package has no files installed.

```
There were about 15 of them. 

I figured I could just
```
 apt-get install [package] --reinstall
```
each one, and the problem would take care of itself. 

Everything was going sweet, and I started feeling my oats a little bit, and decided to lump the rest of them together, killing 5 birds with one stone (command), and everything went horribly wrong. 

Now whenever I apt-get anything, I'm hit with this:
```
wram@frankm:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
7 not fully installed or removed.
Need to get 0B/16.6kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... 
dpkg: serious warning: files list file for package `ssl-cert' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libungif4g' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `bc' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libogg0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libdbus-qt-1-1c2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libseda-java' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `command-not-found' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `launchpad-integration' missing, assuming package has no files currently installed.
154882 files and directories currently installed.)
Preparing to replace command-not-found 0.2.4 (using .../command-not-found_0.2.4_all.deb) ...
pycentral: pycentral pkgremove: package command-not-found is not installed
pycentral pkgremove: package command-not-found is not installed
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package command-not-found is not installed
pycentral pkgremove: package command-not-found is not installed
dpkg: error processing /var/cache/apt/archives/command-not-found_0.2.4_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package command-not-found is not installed
pycentral pkginstall: package command-not-found is not installed
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace launchpad-integration 0.1.13 (using .../launchpad-integration_0.1.13_all.deb) ...
pycentral: pycentral pkgremove: package launchpad-integration is not installed
pycentral pkgremove: package launchpad-integration is not installed
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package launchpad-integration is not installed
pycentral pkgremove: package launchpad-integration is not installed
dpkg: error processing /var/cache/apt/archives/launchpad-integration_0.1.13_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package launchpad-integration is not installed
pycentral pkginstall: package launchpad-integration is not installed
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/command-not-found_0.2.4_all.deb
 /var/cache/apt/archives/launchpad-integration_0.1.13_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
wram@frankm:~$ 
```

I am totally at a loss. HELP!

---

### Post by Pumalite on 2007-09-13
Have you tried:
Synaptic>Edit>Fix Broken Packages

---

### Post by dabl on 2007-09-13
Try ```
sudo dpkg --configure -a
```  :)

---

### Post by Pumalite on 2007-09-13
You might want to look at this too: [http://ubuntuforums.org/showthread.p...=force+removal](http://ubuntuforums.org/showthread.p...=force+removal)

---

### Post by urIkon on 2007-09-13
First of all, thank you so much for such hasty replies. 

Fix broken packages in synaptic did naught.  I don't think this is a dependency issue, though. And I don't think just removing them all is a wise idea, as some of the packages will uninstall a whole bunch of x packages that look to me to be quite important.

dpkg --configure -a output
```

wram@frankm:~$ sudo dpkg --configure -a
Password:
Setting up man-db (2.4.3-5ubuntu1) ...

Setting up xserver-xorg-video-nsc (2.8.2-0ubuntu1) ...
dpkg: error processing command-not-found (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up fftw3 (3.1.2-1build1) ...

dpkg: error processing launchpad-integration (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up libice6 (1.0.3-1build1) ...

Setting up scribus (1.2.5.dfsg-5ubuntu3) ...

Errors were encountered while processing:
 command-not-found
 launchpad-integration

```

Afterwards, I ran apt-get install -f again, and still in the same boat. 

```
wram@frankm:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
2 not fully installed or removed.
Need to get 0B/16.6kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... 
dpkg: serious warning: files list file for package `ssl-cert' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libungif4g' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `bc' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libogg0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libdbus-qt-1-1c2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libseda-java' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `command-not-found' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `launchpad-integration' missing, assuming package has no files currently installed.
154882 files and directories currently installed.)
Preparing to replace command-not-found 0.2.4 (using .../command-not-found_0.2.4_all.deb) ...
pycentral: pycentral pkgremove: package command-not-found is not installed
pycentral pkgremove: package command-not-found is not installed
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package command-not-found is not installed
pycentral pkgremove: package command-not-found is not installed
dpkg: error processing /var/cache/apt/archives/command-not-found_0.2.4_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package command-not-found is not installed
pycentral pkginstall: package command-not-found is not installed
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace launchpad-integration 0.1.13 (using .../launchpad-integration_0.1.13_all.deb) ...
pycentral: pycentral pkgremove: package launchpad-integration is not installed
pycentral pkgremove: package launchpad-integration is not installed
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package launchpad-integration is not installed
pycentral pkgremove: package launchpad-integration is not installed
dpkg: error processing /var/cache/apt/archives/launchpad-integration_0.1.13_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package launchpad-integration is not installed
pycentral pkginstall: package launchpad-integration is not installed
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/command-not-found_0.2.4_all.deb
 /var/cache/apt/archives/launchpad-integration_0.1.13_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
wram@frankm:~$ 


```

Lastly, that url is borked :(

Thanks again for your help, gents.

---

### Post by dabl on 2007-09-13
That's pretty screwed up, all right ...  :(  It's possible that hdd breakage actually messed you up beyond recovery (may be headed toward re-installation). 

You might want to try this series of commands, one at a time:

```
sudo apt-get clean
```

```
sudo apt-get autoremove
```

```
sudo apt-get update
```

```
sudo apt-get install
```


Then try ```
sudo dpkg --configure -a
``` again.  I know it looks a little mindless, and indeed it is, but I've straightened out the package manager on mine by just cycling through these commands a couple of times.  :)

---

### Post by urIkon on 2007-09-13
HUZZAH!

Alas, the answer was simple.  

I DON'T KNOW IF THIS WAS THE CORRECT WAY OF GOING ABOUT THINGS, SO CONSULT A GURU BEFORE CONSUMING.

command-not-found and launchpad-integration were the two packages that were giving me all the guff. It is my understanding that dpkg uses /var/lib/dpkg/info to keep track of current installs/in progress installs (along with /var/lib/dpkg/status).  

So, in said folder, I ran:
```

sudo rm launchpad-integration*
sudo rm command-not-found*
sudo apt-get install launchpad-integration
sudo apt-get install command-not-found command-not-found-data

```
Then continued to reinstall the other packages with the missing files lists. Everything is peachy!
Thanks again for the help!

---

