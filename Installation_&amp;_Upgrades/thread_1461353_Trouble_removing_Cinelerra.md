---
title: "Trouble removing Cinelerra"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by neanderslob on 2010-04-24
Hi All,

Recently I'd been getting error messages when doing a sudo apt-get upgrade, saying that I my libcinelerra package wasn't upgrading.  So I tried purging my computer of the program and reinstalling and now I can't get Cinelerra to work, install or uninstall.  Each time I try to remove it this happens:

:~$ sudo apt-get -f remove --purge cinelerra*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cinelerra-4.1-ubu_9.04

when I try to do a package upgrade I get this:

Removing cinelerra-xt ...
Description:	Ubuntu 9.04
en_US.iso885915
locale "ru_RU.KOI8-R" not in archive
rm: cannot remove `/usr/bin/Cinelerra': No such file or directory
dpkg: error processing cinelerra-xt (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 cinelerra-xt
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas?  :guitar:

---

### Post by neanderslob on 2010-04-24
Oh and I should add that any suggestions are much appreciated.  ...unless they're intentionally horse-**** but I've never seen that happen ....yet :P

---

### Post by _0R10N on 2010-04-25
Tipically, removing installed apps from the commandline is much more faster, but when it fails, then you should try performing that action from Synaptic. Search for the package and then select it for complete uninstall. See what packages are selected for removal, you might find a conflict...

I prefer, and recommend, the usage of aptitude against apt-get. So you can also try
```
sudo aptitude -f
```
to fix broken packages.
After removing the package, update the content of your repositories, running
```
sudo aptitude update
```

Hope this help! Let us know how it goes!

Kind regards!

_0R10N >>

---

### Post by neanderslob on 2010-04-25
Hey man, thanks very much for your suggestion; I had not tried using aptitude.  Unfortunately aptitude kicked out exactly the same response as apt-get once all was said and done.  (I really like the interface of aptitude though, I think I might switch over to using it on a regular basis.)  Here's the output in case there are any subtle differences that I didn't pick up on.

~$ sudo aptitude -f
[sudo] password for 
(Reading database ... 181904 files and directories currently installed.)
Removing cinelerra-xt ...
Description:	Ubuntu 9.04
en_US.iso885915
locale "ru_RU.KOI8-R" not in archive
rm: cannot remove `/usr/bin/Cinelerra': No such file or directory
dpkg: error processing cinelerra-xt (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 cinelerra-xt
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.

---

