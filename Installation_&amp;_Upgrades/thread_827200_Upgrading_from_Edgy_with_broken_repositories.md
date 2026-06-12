---
title: "Upgrading from Edgy with broken repositories"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by The Dragon Master on 2008-06-12
Now Edgy is no longer supported ([http://en.wikipedia.org/wiki/Ubuntu#Ubuntu_6.10_.28Edgy_Eft.29](http://en.wikipedia.org/wiki/Ubuntu#Ubuntu_6.10_.28Edgy_Eft.29)) I would like to update to Hardy Heron. But none of the repositories in my sources.list function any more.

For sake of demonstration I'll keep the example simple and remove everything from source.list except the lines ....

# My Sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

Now I'll run apt-get update

$ sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Errhttp://archive.ubuntu.com edgy/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


The problem seems to be that edgy is no longer at [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)

and I cannot find any trust worthy repositories for edgy now. Is my only option for an update to backup all my data, burn Hardy Heron to CD and install from disk erasing edy eft as I go?

:confused:

---

### Post by avtolle on 2008-06-12
Another option, should you want to try it: [https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)

---

### Post by kdcoetzee on 2008-06-12
You can try...

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories")

And if you need Hardy repos. just go to [http://ubuntuguide.org/]("http://ubuntuguide.org/")
very helpful site.

---

### Post by The Dragon Master on 2008-06-12
Thanks Avtolle

What I didn't know was that I could replace all "edgy"s with "feisty"s in sources list.


So I followed this suggestion from Pumalite at this thread ([http://ubuntuforums.org/showthread.php?t=817409&highlight=edgy](http://ubuntuforums.org/showthread.php?t=817409&highlight=edgy))

sudo sed -i 's/edgy/feisty/' /etc/apt/sources.list

sudo apt-get update

sudo apt-get dist-upgrade

But I hit a key problem, so I also had to follow this suggestion from Did at this thread ([http://forum.ubuntu-fr.org/viewtopic.php?pid=722968](http://forum.ubuntu-fr.org/viewtopic.php?pid=722968))

gpg --keyserver subkeys.pgp.net --recv 40976EAF437D05B5 && gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -

This has been enough to finally let me start a dist-upgrade.

:guitar:

---

### Post by avtolle on 2008-06-12
Glad to see you're up and going. Good luck with the upgrade.

---

