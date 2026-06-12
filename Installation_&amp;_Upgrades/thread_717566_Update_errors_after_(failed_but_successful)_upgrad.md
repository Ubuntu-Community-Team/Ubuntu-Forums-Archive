---
title: "Update errors after (failed but successful) upgrade to gutsy"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by zaffod on 2008-03-07
ok. I decided to upgrade to Gutsy because i read somewhere that it has improved support for compiz. 

Anyway, the Upgrade failed near the end of the process, after reporting that it could not install libofa0, libtunepimp5.... npviewer.bin closed unexpectedly .... some other messages.... 
It said it was going into recovery mode but when the upgrade application exited, i appeared to be in a successfully upgraded system. 

I rebooted and all looks ok.[U] Except when I do an update:
[/U]
```
E: /var/cache/apt/archives/libofa0_0.9.3-2_amd64.deb: unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums'
E: /var/cache/apt/archives/libtunepimp5_0.5.3-4ubuntu2_amd64.deb: unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/shlibs'

```
[B]
Can anyone help me determine if my system is now stable, or has the upgrade made a monkey of my Feisty system? How can I fix the issue I have when doing updates?[/B]

 dpkg --configure -a returns:
```
dpkg: dependency problems prevent configuration of amarok:
 amarok depends on libtunepimp5; however:
  Package libtunepimp5 is not installed.
dpkg: error processing amarok (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of amarok-xine:
 amarok-xine depends on amarok (= 2:1.4.8-0ubuntu1~gutsy1); however:
  Package amarok is not configured yet.
 amarok-xine depends on amarok; however:
  Package amarok is not configured yet.
dpkg: error processing amarok-xine (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amarok
 amarok-xine
```

If i do an "apt-get install -f"
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-elementtree libktnef1 python-setuptools libmono-system-data1.0-cil
/// cut for brevity ///
  python-feedparser koffice-data libgnorba27 python-wxversion
  libgdk-pixbuf2-ruby
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libofa0 libtunepimp5
The following packages will be upgraded:
  libofa0 libtunepimp5
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/422kB of archives.
After unpacking 36.9kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 154806 files and directories currently installed.)
Preparing to replace libofa0 0.9.3-1 (using .../libofa0_0.9.3-2_amd64.deb) ...
Unpacking replacement libofa0 ...
dpkg: error processing /var/cache/apt/archives/libofa0_0.9.3-2_amd64.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums': Is a directory
Preparing to replace libtunepimp5 0.5.2-1ubuntu3 (using .../libtunepimp5_0.5.3-4ubuntu2_amd64.deb) ...
Unpacking replacement libtunepimp5 ...
dpkg (subprocess): unable to execute old post-removal script: Exec format error
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
dpkg: error processing /var/cache/apt/archives/libtunepimp5_0.5.3-4ubuntu2_amd64.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/shlibs': Is a directory
Errors were encountered while processing:
 /var/cache/apt/archives/libofa0_0.9.3-2_amd64.deb
 /var/cache/apt/archives/libtunepimp5_0.5.3-4ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks for the support thus far.

---

### Post by ssj3strife on 2008-03-08
It looks like only those 2 amarok dependancies are causing trouble. Can you install/update other packages without issue?

---

### Post by zaffod on 2008-03-08
No. I cannot install / remove packages using synaptic or "add/remove". It tries but then errs on those two packages. 

Which is a pity because otherwise, the system looks stable. I'm think I may have to back up and reinstall the OS. =(

Should've stayed with Feisty.

---

### Post by ssj3strife on 2008-03-08
Try checking your repository settings - is your system still trying to use the old Feisty repos instead of the Gutsy ones?

---

### Post by zaffod on 2008-03-08
yeh I did check that. They were updated to Gutsy as part of the upgrade. 
I'm just moving all my data to a new partition, and I'm gonna clean install Gutsy if I can't figure this issue out soon. 

Do you think what i experienced should be reported as a bug at launchpad? I've never done that.

---

### Post by ssj3strife on 2008-03-10
Hmm, I don't know - do you think the problem is reproducable? If so, go for it - if not, I don't know if it would do any good.

Have you tried clearing out your cache (/var/cache/apt), and then trying to update again? That'd be the last thing I could suggest. (I actually don't know if it's safe to do that, but if you're going to reinstall anyway, it's worth a shot.)

---

### Post by zaffod on 2008-03-10
Hi, Thanks for the suggestion but I've installed Gusty fresh from a CD. Looks good. Still have some issues when using compiz, but some improved stability. Sleep / hibernate still broken. Otherwise all ok. 

Lesson Learnt: Don't upgrade a working system with the hope that it'll fix some minor issues.

---

