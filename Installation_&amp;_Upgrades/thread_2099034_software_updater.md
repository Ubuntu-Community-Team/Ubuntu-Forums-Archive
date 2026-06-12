---
title: "software updater"
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by cees.knysna on 2012-12-28
Every time I update I receive the error message as below.
Besides I used Dropbox but  a couple of weeks ago Dropbox disappeared and I can not re-install it anymore.
I have not a clue what to do. Please help.

W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch [http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-amd64/Packages](http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by darkod on 2012-12-28
Double check your sources in Software Centre, Software Sources.

For the cdrom message, you might have the cd set as a source, so everytime you try to install or remove something it's looking for the cd to be inside the drive. Remove/disable any cd-rom from the sources, you would usually download what you need from the internet.

For the linux.dropbox.com error, it seems you have a source/repository set up. And it no longer exists at that address. So it is getting the 404 Not Found error. Remove this source also.

After that it should be fine. Be careful when adding repositories, make sure they work and they will keep working (not changing the URL every month).

---

### Post by Bucky Ball on 2012-12-28
Yes, the CD is set as a source. Disable that in Software Sources, as suggested, by unticking the box next to it. That might fix the dropbox repo issue as well ...

If not, you might want to disable that repo, too, as maybe the server is down.

---

