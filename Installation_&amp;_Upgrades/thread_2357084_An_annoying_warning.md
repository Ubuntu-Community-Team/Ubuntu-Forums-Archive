---
title: "An annoying warning"
date: 2017-03-29
forum: Installation &amp; Upgrades
---

### Post by uwe-bungto on 2017-03-29
I did a clean upgrade of Ubuntu Studio 16.04.2. There is an annoying warning every time I use apt-get or synaptic

> E: Failed to fetch file:/var/cache/apt-build/repository/dists/apt-build/main/binary-i386/Packages  File not found - /var/cache/apt-build/repository/dists/apt-build/main/binary-i386/Packages (2: No such file or directory)
E: Some index files failed to download. They have been ignored, or old ones used instead.

How do I get rid of it. 
The dir /var/cache/apt-build/repository/dists/apt-build/main/binary-i386 does not exist

Thanks 

Paul

---

### Post by #&amp;thj^% on 2017-03-29
What shows from:
```
leafpad /etc/apt/sources.list.d/apt-build.list

```
Paste back here please.

---

### Post by uwe-bungto on 2017-03-30
deb [trusted=yes] file:/var/cache/apt-build/repository apt-build main

---

### Post by vasa1 on 2017-03-30
Please post the output of```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/* | nl
```as well.

---

### Post by uwe-bungto on 2017-03-30
```
jpb@maple:~$ grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/* | nl
     1    /etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial main restricted
     2    /etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
     3    /etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial universe
     4    /etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-updates universe
     5    /etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial multiverse
     6    /etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
     7    /etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
     8    /etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
     9    /etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
    10    /etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
    11    /etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
    12    /etc/apt/sources.list:deb [http://download.ebz.epson.net/dsc/op/stable/debian/](http://download.ebz.epson.net/dsc/op/stable/debian/) lsb3.2 main
    13    /etc/apt/sources.list.d/apt-build.list:deb [trusted=yes] file:/var/cache/apt-build/repository apt-build main
    14    /etc/apt/sources.list.d/apt-build.list.save:deb [trusted=yes] file:/var/cache/apt-build/repository apt-build main
    15    /etc/apt/sources.list.d/audio-recorder-ubuntu-ppa-xenial.list:deb [http://ppa.launchpad.net/audio-recorder/ppa/ubuntu](http://ppa.launchpad.net/audio-recorder/ppa/ubuntu) xenial main
    16    /etc/apt/sources.list.d/audio-recorder-ubuntu-ppa-xenial.list.save:deb [http://ppa.launchpad.net/audio-recorder/ppa/ubuntu](http://ppa.launchpad.net/audio-recorder/ppa/ubuntu) xenial main
    17    /etc/apt/sources.list.d/deluge-team-ubuntu-ppa-xenial.list:deb [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) xenial main
    18    /etc/apt/sources.list.d/deluge-team-ubuntu-ppa-xenial.list.save:deb [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) xenial main
    19    /etc/apt/sources.list.d/djcj-ubuntu-mediainfo-xenial.list:deb [http://ppa.launchpad.net/djcj/mediainfo/ubuntu](http://ppa.launchpad.net/djcj/mediainfo/ubuntu) xenial main
    20    /etc/apt/sources.list.d/djcj-ubuntu-mediainfo-xenial.list.save:deb [http://ppa.launchpad.net/djcj/mediainfo/ubuntu](http://ppa.launchpad.net/djcj/mediainfo/ubuntu) xenial main
    21    /etc/apt/sources.list.d/getdeb.list:deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) xenial-getdeb apps
    22    /etc/apt/sources.list.d/getdeb.list.save:deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) xenial-getdeb apps
    23    /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-xenial.list:deb [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) xenial main
    24    /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-xenial.list.save:deb [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) xenial main
    25    /etc/apt/sources.list.d/maarten-baert-ubuntu-simplescreenrecorder-xenial.list:deb [http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu](http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu) xenial main
    26    /etc/apt/sources.list.d/maarten-baert-ubuntu-simplescreenrecorder-xenial.list.save:deb [http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu](http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu) xenial main
    27    /etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list:deb [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) xenial main
    28    /etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list.save:deb [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) xenial main
    29    /etc/apt/sources.list.d/pmjdebruijn-ubuntu-darktable-release-xenial.list:deb [http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu](http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu) xenial main
    30    /etc/apt/sources.list.d/pmjdebruijn-ubuntu-darktable-release-xenial.list.save:deb [http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu](http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu) xenial main
    31    /etc/apt/sources.list.d/skype-stable.list:deb [arch=amd64] [https://repo.skype.com/deb](https://repo.skype.com/deb) stable main
    32    /etc/apt/sources.list.d/skype-stable.list.save:deb [arch=amd64] [https://repo.skype.com/deb](https://repo.skype.com/deb) stable main
    33    /etc/apt/sources.list.d/teejee2008-ubuntu-ppa-xenial.list:deb [http://ppa.launchpad.net/teejee2008/ppa/ubuntu](http://ppa.launchpad.net/teejee2008/ppa/ubuntu) xenial main
    34    /etc/apt/sources.list.d/teejee2008-ubuntu-ppa-xenial.list.save:deb [http://ppa.launchpad.net/teejee2008/ppa/ubuntu](http://ppa.launchpad.net/teejee2008/ppa/ubuntu) xenial main
    35    /etc/apt/sources.list.d/thomas-schiex-ubuntu-blender-xenial.list:deb [http://ppa.launchpad.net/thomas-schiex/blender/ubuntu](http://ppa.launchpad.net/thomas-schiex/blender/ubuntu) xenial main
    36    /etc/apt/sources.list.d/thomas-schiex-ubuntu-blender-xenial.list.save:deb [http://ppa.launchpad.net/thomas-schiex/blender/ubuntu](http://ppa.launchpad.net/thomas-schiex/blender/ubuntu) xenial main
    37    /etc/apt/sources.list.d/ubuntuhandbook1-ubuntu-dvdstyler-xenial.list:deb [http://ppa.launchpad.net/ubuntuhandbook1/dvdstyler/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/dvdstyler/ubuntu) xenial main
    38    /etc/apt/sources.list.d/ubuntuhandbook1-ubuntu-dvdstyler-xenial.list.save:deb [http://ppa.launchpad.net/ubuntuhandbook1/dvdstyler/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/dvdstyler/ubuntu) xenial main
    39    /etc/apt/sources.list.d/virtualbox.org.list:deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial contrib
    40    /etc/apt/sources.list.d/virtualbox.org.list.save:deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial non-free contrib
    41    /etc/apt/sources.list.d/vivaldi.list:deb [http://repo.vivaldi.com/stable/deb/](http://repo.vivaldi.com/stable/deb/) stable main
jpb@maple:~$
```

---

### Post by #&amp;thj^% on 2017-03-30
> **uwe-bungto said:**
> deb [trusted=yes] file:/var/cache/apt-build/repository apt-build main

I think you find it works a bit better when adding:
```
[arch=amd64]
```
Like:
```
deb [arch=amd64 trusted=yes]  file:/var/cache/apt-build/repository apt-build main

```
This is a old bug that was reported here: [https://bugs.launchpad.net/ubuntu/+source/apt-build/+bug/1268120](https://bugs.launchpad.net/ubuntu/+source/apt-build/+bug/1268120)

---

### Post by uwe-bungto on 2017-03-30
Thank you.
the warning is gone
Paul

---

### Post by #&amp;thj^% on 2017-03-30
Your Welcome.;)
Glad everything is now ship shape.

---

