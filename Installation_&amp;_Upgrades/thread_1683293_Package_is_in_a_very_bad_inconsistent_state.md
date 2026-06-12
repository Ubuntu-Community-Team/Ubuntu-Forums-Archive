---
title: "Package is in a very bad inconsistent state"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by isecore on 2011-02-07
So yesterday I noticed there were new updates. In this case from the Wine PPA. Started installing them and on the package named ttf-symbol-replacement-wine1.3 everything just... stopped.

I prefer applying updates in the terminal (using aptitude) and on this package dpkg just completely broke. I thought it just took a while, but after an hour nothing had happened. I had to kill aptitude with a SIGKILL and do the same to dpkg, and then I had to run dpkg --configure -a to get it working again (after I removed all the lock-files).

Something seems very off with this package, and it's now been broken. When I try to purge it (or remove it) I get the following error:

```
dpkg: error processing ttf-symbol-replacement-wine1.3 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ttf-symbol-replacement-wine1.3
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

If I try to reinstall it the same thing happens as before i.e. DPKG grinds to a halt and then nothing. 

I can't apply any updates because DPKG wants to install this package first, and I can't remove it or purge it due to the above error. My APT has been locked in a complete Catch-22.

What gives?

---

### Post by tommcd on 2011-02-07
> **isecore said:**
> So yesterday I noticed there were new updates. In this case from the Wine PPA. Started installing them and on the package named ttf-symbol-replacement-wine1.3 everything just... stopped.
This is why I *never* use any 3rd party repos. This includes those all too problematic PPA repos, which are completely unsupported by Ubuntu.
First, you need to understand that this is a problem that you have caused yourself. Ubuntu did not fail you here!

To try to fix this mess you can run in the terminal the standard commands to fix problems with broken packages:
First, open a terminal and run: ```
sudo dpkg --configure -a

```
If that returns errors, try:
```
sudo dpkg --clear-avail && sudo apt-get update
```
See this thread:
[http://ubuntuforums.org/showthread.php?t=1022727](http://ubuntuforums.org/showthread.php?t=1022727)
If that does not work, try:
```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
Sudo apt-get upgrade
```

And if nothing else works, then run this to remove broken packages:
```
sudo dpkg --purge --force-all package-name
```
Where *package-name* is the rogue package that you decided to install.
You could also try commenting out (put a # in front of) your rogue wine repo in your /etc/apt/sources.list file, or in your /etc/apt/sources.list.d/ directory. Then run:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
> **isecore said:**
> 
Something seems very off with this package, and it's now been broken. 
What gives?
What gives is that you decided to install an unsupported package that is apparently broken,and completely unsupported. You should use these PPA repos with caution, if at all.

---

