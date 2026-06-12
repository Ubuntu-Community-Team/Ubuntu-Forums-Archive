---
title: "Upgrading from local repository?"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Githlar on 2011-04-29
Hello, everyone!

I've got another odd question. Is it possible to upgrade Ubuntu from a local repository? I've had a mirror of Natty since it was created, so all of the files should be up-to-date. I have a friend with Ubuntu as well, but due to restrictions on his internet he is unable to install the update through the Update Manager.

I know how to install things from the repository on the hard drive, however I've never tried an upgrade from a repository?

What steps are involved during the installation process? I know one of the first things that's done is that the repositories are changed to Natty. I also know that it downloads some kind of upgrade package that tells it what all it needs to do, but other than that I'm lost.

Does anybody have any recommendations for me?

---

### Post by Githlar on 2011-05-01
Also, what does the update manager have to download in order for it to know that there is a new version. By that, I mean it can't just go off the number of folders in archive.ubuntu.org/ubuntu/dists because the natty repository has existed for a long time.

---

### Post by Githlar on 2011-05-01
I had a look at the update-manager source (OK, it was some of the README's) and it says that you can get debug output from update-manager by setting the environment variable DEBUG_UPDATE_MANAGER. I tried it and update-manager dumps some useful information to the console:

```
MetaRelease.__init__() useDevel=False useProposed=False
/etc/update-manager/meta-release: http://changelogs.ubuntu.com/meta-release 
/etc/update-manager/meta-release: http://changelogs.ubuntu.com/meta-release-lts 
/etc/update-manager/meta-release: -development 
/etc/update-manager/meta-release: -proposed 
metarelease-uri: http://changelogs.ubuntu.com/meta-release
MetaRelease.download()
have self.metarelease_information
MetaRelease.parse()
current dist name: 'natty'
found distro name: 'warty'
found distro name: 'hoary'
found distro name: 'breezy'
found distro name: 'dapper'
found distro name: 'edgy'
found distro name: 'feisty'
found distro name: 'gutsy'
found distro name: 'hardy'
found distro name: 'intrepid'
found distro name: 'jaunty'
found distro name: 'karmic'
found distro name: 'lucid'
found distro name: 'maverick'
found distro name: 'natty'
```

So, it appears that it pulls the release information from [http://changelogs.ubuntu.com/meta-release](http://changelogs.ubuntu.com/meta-release)

So, here's what I propose to do prior to moving to the machine needing upgrading:
1. Mirror archive.ubuntu.com/ubuntu/dists/natty/dist-upgrader-all/current and add it on my repository file tree.
2. Mirror changelogs.ubuntu.com's root directory into /some/path/UpdateServer
3. Change the Natty URL's in meta-release from http:// to file:// URI's referencing the harddrive repository.
And here's what I'm going to do from the machine needing upgrading:
1. Install Apache from the harddrive repository
2. Setup Apache with a VirtualHost of changelogs.ubuntu.com
3. Make an entry in /etc/hosts rerouting traffic from changelogs.ubuntu.com to 
'localhost' (which in turn will activate the VirtualHost)

If the URI's can't be changed to file:// URI's, then I'll just set up another VirtualHost for archive.ubuntu.com pointing to the repository harddrive. This might cause some issues with ownership, but I can force apache to run as the current user (he's not on the internet, so there's really no risk)

---

### Post by silvavlis on 2011-07-12
Did you get it running Githlar?

I'm trying to do something similar, but mirroring all the required files in a server and modifying the required ones both in the server and the client.

I already mirrored the required *dist-upgrader-all* files and changelogs so that *update-manager* reports that a new release exists.

The problem is that it downloads a new *update-manager* for the upgrade (for Lucid, for example, the file *lucid.tar.gz* from [http://de.archive.ubuntu.com/ubuntu/dists/lucid/main/dist-upgrader-all/current/](http://de.archive.ubuntu.com/ubuntu/dists/lucid/main/dist-upgrader-all/current/)). And this new version ignores every change I might have done in the server.

I'm wondering if there is no easier way than unpacking *lucid.tar.gz*, changing all the URLs so that they point to my mirror and packing the archive again. It sounds kind of too complicated...

---

