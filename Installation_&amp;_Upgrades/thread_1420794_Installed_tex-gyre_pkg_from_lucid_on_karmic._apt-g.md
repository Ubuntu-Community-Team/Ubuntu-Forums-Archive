---
title: "Installed tex-gyre pkg from lucid on karmic. apt-get stopped"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by irate.turtle on 2010-03-03
```
$uname -a
Linux ______ 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

```

I downloaded tex-gyre package from [lucid repository]("http://packages.ubuntu.com/lucid/tex-gyre") and installed it. I recall the installation giving error msg saying something to the effect that "tex-common (>= 2.00) required while you have installed 1.20". Still it somehow did install and now I get the following error when I try to uninstall it or try to install anything else.
```
$ sudo apt-get autoremove tex-gyre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  tex-gyre
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 34.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 296780 files and directories currently installed.)
Removing tex-gyre ...
unknown option: map
dpkg: error processing tex-gyre (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 tex-gyre
E: Sub-process /usr/bin/dpkg returned an error code (1)
$
$
$
$
$
$ sudo apt-get install djview4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  djvulibre-desktop
Suggested packages:
  djvulibre-bin djvulibre-plugin
The following packages will be REMOVED:
  tex-gyre
The following NEW packages will be installed:
  djview4 djvulibre-desktop
0 upgraded, 2 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B/679kB of archives.
After this operation, 32.2MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 296780 files and directories currently installed.)
Removing tex-gyre ...
unknown option: map
dpkg: error processing tex-gyre (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 tex-gyre
E: Sub-process /usr/bin/dpkg returned an error code (1)
$ 

```
Any help would be appreciated. I tried uninstalling it using Synaptic and obviously it throws the same error.

---

### Post by irate.turtle on 2010-03-07
Appled info from these two links: [_link1_]("http://odzangba.wordpress.com/2009/10/14/how-to-fix-“subprocess-pre-removal-script-returned-error-exit-status-2&#8243;-error/") and [_link2_]("http://ubuntuforums.org/archive/index.php/t-545055.html"). Seems to work for now. Hopefully no surprises will popup in future.

---

