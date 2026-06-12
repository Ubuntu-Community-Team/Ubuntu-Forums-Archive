---
title: "&quot;W: gpg error&quot; when trying to update ; also libreadline.so.6 is gone"
date: 2012-12-12
forum: Installation &amp; Upgrades
---

### Post by petitionhamilton on 2012-12-12
Hi folks,

I'm running Ubuntu version 10.04 LTS.

I had been trying to fix a problem with the update manager for a while. When I open it, I would get:

*E:Error,pkgProblemResolver::Resolve generated breaks, this may be casued by held packages*

I would receive a similar error error when running *apt-get update* from the terminal. I also could not upgrade to the new version of Ubuntu, 12.04

In my desperation while trying to fix this persistent problem, I came across a solution that talked about deleting the /usr/lib/libreadline files. I ended up deleting my /lib/libreadline.so.6 by mistake. Now I get an additional error message when trying to run *do-release-upgrade* from terminal:

*gpg: error while loading shared libraries: libreadline.so.6: cannot open shared object file: No such file or directory*

Now I also get this huge error message when trying to run apt-get update:

[I]W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: Unknown error executing gpgv
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: Unknown error executing gpgv
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release: Unknown error executing gpgv
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release: Unknown error executing gpgv
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: Unknown error executing gpgv
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-backports Release: Unknown error executing gpgv
W: GPG error: [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release: Unknown error executing gpgv
[/I]
Is there anything I can do to repair these problems and get the new release? If I have messed up irreversibly, I will hang my head in shame and reformat my harddrive and do a re-install.

Thanks so much for any help.

---

### Post by zvacet on 2012-12-13
In **synaptic>refesh>mark all updates**.Maybe that will help.

---

### Post by ibjsb4 on 2012-12-13
Got some hits here that may help.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Unknown+error+executing+gpgv&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Unknown+error+executing+gpgv&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by petitionhamilton on 2012-12-17
Hi, thanks for the suggestions.

zvacet, Synaptic gave me these messages:

[I]E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 Could not upgrade the system! Fix broken packages first.[/I]

ibjsb4, I have been grappling with this problem for some time and have already tried the solutions on many of those pages, though there are definitely one or two I will look at again. One of them was the one that lead me to accidentally delete my **libreadline.so.6 **which caused more problems. If any of those threads stand out to you as being worth another look though, let me know and I'll try the solutions offered there.

Any futher help on this issue would be greatly appreciated.

---

