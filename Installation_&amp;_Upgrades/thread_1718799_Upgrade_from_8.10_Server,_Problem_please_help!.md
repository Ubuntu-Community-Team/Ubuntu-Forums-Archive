---
title: "Upgrade from 8.10 Server, Problem please help!"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by ubila on 2011-03-31
Hello,
So ive decided to upgrade to Ubuntu server 9.04 since the 8.10 repositories are not supported anymore.

Im running Ubuntu 8.10 Server 64 bit. With a working internet connection. 

When Im upgrading I do this:
sudo apt-get install update-manager-core
sudo do-release-upgrade

But it returns this error: (sorry for long paste output)

> richard@spiders:~$ sudo do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'jaunty.tar.gz'
authenticate 'jaunty.tar.gz' against 'jaunty.tar.gz.gpg'

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid Release.gpg
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid Release.gpg
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates Release.gpg
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates Release.gpg
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid Release
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid Release
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates Release
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates Release
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main Packages
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main Packages
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/restricted Packages
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/restricted Packages
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main Sources
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main Sources
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/restricted Sources
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/restricted Sources
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/universe Packages
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/universe Packages
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/universe Sources
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/universe Sources
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/multiverse Packages
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/multiverse Packages
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/multiverse Sources
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/multiverse Sources
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/main Packages
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/main Packages
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/restricted Packages
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/restricted Packages
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/main Sources
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/main Sources
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/restricted Sources
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/restricted Sources
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/universe Packages
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/universe Packages
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/universe Sources
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/universe Sources
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/multiverse Packages
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/multiverse Packages
Ignored [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/multiverse Sources
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/multiverse Sources
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main Packages
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/restricted Packages
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/main Sources
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/restricted Sources
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/universe Packages
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/universe Sources
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/multiverse Packages
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid/multiverse Sources
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/main Packages
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/restricted Packages
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/main Sources
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/restricted Sources
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/universe Packages
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/universe Sources
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/multiverse Packages
Failed [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) intrepid-updates/multiverse Sources
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Ignored [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/mainverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/mainverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Failed [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/mainverse Packages
Done downloading
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Updating repository information
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty Release.gpg
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release.gpg
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty Release
Done [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty Release
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release
Done [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Done downloading
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty Release.gpg
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release.gpg
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty Release
Done [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty Release
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release
Done [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Done downloading
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty Release.gpg
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release.gpg
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty Release
Done [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty Release
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release
Done [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Done downloading

Error during update

A problem occurred during the update. This is usually some sort of
network problem, please check your network connection and retry.

W:Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release)
Unable to find expected entry mainverse/binary-amd64/Packages in
Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or
old ones used instead.


Restoring original system state

Aborting
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Could it be that my /etc/apt/sources has the old Interpid repositories in it? Do i need to change them to the Jaunty ones for this upgrade to work?

Any help would be greatly appreciated.
Cheers!

---

### Post by tommcd on 2011-03-31
> **ubila said:**
> 
So ive decided to upgrade to Ubuntu server 9.04 since the 8.10 repositories are not supported anymore.

Ubuntu 9.04 is no longer supported either: [http://www.ubuntugeek.com/ubuntu-version-names-and-end-of-life-details.html](http://www.ubuntugeek.com/ubuntu-version-names-and-end-of-life-details.html)
Your best bet would be to do a clean install of Ubuntu 10.04. Since 10.04 is a LTS version it will be supported until April 2015 for the server version.

---

