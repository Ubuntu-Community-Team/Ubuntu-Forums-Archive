---
title: "Problem downloading upgrade to 8.04"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by trikkievic on 2008-05-09
Hello, upon trying to upgrade to 8.04 from 7.10 using the update manager, the ugrade process stops with the message that certain files could not be downloaded.

During the "Setting new software channels" phase, it first gives an information box saying that "Third party sources disabled", with the message that I can re-enable them after the upgrade with the properties tool of my package manager.

Upon closing this message box, it then resumes to fetch different files. Before it can enter the "getting new packages" phase, I get a warning box with the following text:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Release) Unable to find expected entry  main/debian-installer/source/Sources in Meta-index file (malformed Release file?)

So, I went to my Synaptic update manager, and under settings-repositories made sure all were "on" and set the preferred server to "server for north america" (that's my location). Then tried to reload the available upgrades and got the same error message when trying to download file 99 of 100 or so:

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release:) Unable to find expected entry  main/debian-installer/source/Sources in Meta-index file (malformed Release file?)

So, apparently, the above repository is not correct, but I do not know how to bypass this. I am unable to upgrade to 8.04 due to this bad file/address. The upgrade simply stops and any changes are undone.

Anyone knows how I can get a different address for the above file, and where and how I can input that repository in the Synpatic update manager?

Thanks!

Vic

p.s. I know I could probably download the DVD/CD-ROM and burn it, that's how I upgraded to 7.10 from 7.04, but I'd rather do it with the update manager.

---

### Post by Pumalite on 2008-05-09
First of all remove all third parties from your /etc/apt/sources.list. Then try again.

---

