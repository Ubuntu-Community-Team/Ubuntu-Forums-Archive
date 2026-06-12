---
title: "help please: dpkg: unrecoverable fatal error"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by dsjansen on 2010-07-04
An installation of Gnokii went wrong and blocked Ubuntu 10.04 upgrades.
I tried this (upon a suggestion of someone):
- apt-get -f install to force an install
- apt-get upgrade again
- deleted reference to Gnokki in Statoverride file
- also in /var/lib/dpkg/info
- also in /var/cache/apt/archives

Still get this message:[INDENT]76 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/78,0MB of archives.
After this operation, 6611kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: unrecoverable fatal error, aborting:
 statoverride file contains empty line
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/INDENT]Please advise and help me!

---

### Post by phillw on 2010-07-04
Hiyas, the below is from my library of fixing an errant package to get synaptics happy again.
> 
In cases where installing a package is abruptly stopped (such as a power failure, or your battery dying) it can leave you in a position where you cannot launch Synaptics Package Manager. To reset things you need to:
[list]
1) cd /var/lib/dpkg
2) sudo cp available available.bad
3) sudo cp status status.bad
4a) open available with a text editor. (e.g. gksudo gedit available)
4b) remove all references to offending package. Save/close.
5a) open status with a text editor.
5b) remove all references to offending package. Save/close.
6) cd info
7) delete all files relating to package. (Don't worry if there are no files there, it depends on how far the install went).[/list]


Regards,
Phill.

---

### Post by dsjansen on 2010-07-05
Excellent, thanks for your help, this helped.
In the statoverride file I also deleted an empty line.

---

