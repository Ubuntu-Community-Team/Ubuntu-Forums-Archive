---
title: "Evolution client missing following upgrade to 20.10"
date: 2020-10-24
forum: Installation &amp; Upgrades
---

### Post by neilohnez on 2020-10-24
Following an upgrade from 20.04 to 20.10 the Evolution client was no longer installed and I have not found a way to reinstall it. The evolution-data-server package is installed. Initially I checked in the "Ubuntu Software" but could not find Evolution listed. When I run "apt update" followed by "apt install evolution" I get the following:
```
$ sudo apt install evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package evolution is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  evolution-data-server

E: Package 'evolution' has no installation candidate

```
I can see a package listed for the amd64 architecture at [https://packages.ubuntu.com/groovy/evolution](https://packages.ubuntu.com/groovy/evolution) but if I try to download and install it then "Ubuntu Software" says "Failed to install file: not supported". I did not see anything in the release notes for 20.10 suggesting that Evolution was no longer supported.

---

### Post by neilohnez on 2020-11-28
By accident I have discovered the solution, which was that the Evolution client is in the universe repository rather than the main repository and in the Software Updater settings the universe repository was not ticked. I can only guess that at some point I unintentionally selected an option to disable that repository.

---

