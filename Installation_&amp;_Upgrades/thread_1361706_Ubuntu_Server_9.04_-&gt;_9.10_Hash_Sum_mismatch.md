---
title: "Ubuntu Server 9.04 -&gt; 9.10: Hash Sum mismatch"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by Dimas on 2009-12-22
I'm upgrading a Ubuntu Server 8.10 to the last release.

First I updated it to 9.04 without problem, doing this:

```
sudo apt-get update
sudo apt-get install update-manager-core
sudo do-release-upgrade
```

Now I have 9.04 working, but can't upgrade to 9.10. I do:

```
sudo aptitude upgrade
sudo aptitude dist-upgrade
sudo aptitude install update-manager-core
sudo do-release-upgrade
```

The last action give this error every time:

```
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting 'karmic.tar.gz'
authenticate 'karmic.tar.gz' against 'karmic.tar.gz.gpg'

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Done downloading
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
No candidate ver:  libisc44
No candidate ver:  belocs-locales-bin
No candidate ver:  libxcb-xlib0
No candidate ver:  libparted1.8-9
No candidate ver:  linux-image-2.6.27-9-server
No candidate ver:  libmagick10
No candidate ver:  linux-image-2.6.27-7-server
No candidate ver:  libntfs-3g28
No candidate ver:  libdns44

Updating repository information
Done downloading
Done downloading
Done downloading

Error during update

A problem occurred during the update. This is usually some sort of
network problem, please check your network connection and retry.

[B]W:Failed to fetch
http://es.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.bz2
Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or
old ones used instead.[/B]


Restoring original system state

Aborting
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
```

---

### Post by rodmacpherson on 2009-12-22
Looks like the file on that server is corrupt.

open /etc/apt/sources.list in your favorite text editor 

comment out the lines that end in universe

Find other servers that host those packages (try another continent's servers) and put their lines in. 

re-run your upgrade.

---

### Post by Dimas on 2009-12-22
Solved. In my case was a proxy problem, since I'm behind a corporate firewall and needed to configure apt-get to use the proxy server.

More info about setting up de proxy: [http://cubicledenizen.blogspot.com/2008/03/ubuntu-proxy-for-aptitude-update.html](http://cubicledenizen.blogspot.com/2008/03/ubuntu-proxy-for-aptitude-update.html)

---

