---
title: "qt-dev: Broken Packages."
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by SteveTheRed on 2011-06-07
I know that there have been a lot of posts for broken packages but I haven't found the right solution and I'm getting frustrated. Any hints or links to solutions would be appreciated.

I'm trying to install qt-dev but I get a broken package error. I'm using Xubuntu amd64 11.04 Natty with the default version of KDE.

Here's the output when I try to install qt-dev:

```

steve@bender3:~$ sudo apt-get install qt-sdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 qt-sdk : Depends: libqt4-dev but it is not going to be installed
          Depends: libqt4-opengl-dev but it is not going to be installed
          Depends: libphonon-dev but it is not going to be installed
          Depends: qt4-designer but it is not going to be installed
          Depends: qt4-dev-tools but it is not going to be installed
          Depends: libqtwebkit-dev but it is not going to be installed
E: Broken packages

```

When I try to install the first listed package individually (libqt4-dev), I get this output:

```

steve@bender3:~$ sudo apt-get install libqt4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqt4-dev : Depends: libqt4-dbus (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-qt3support (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-xml (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqtcore4 (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqtgui4 (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-network (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-svg (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-sql (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-script (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-scripttools (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-xmlpatterns (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-designer (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-help (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-test (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Depends: libqt4-declarative (= 4:4.7.2-0ubuntu6) but 4:4.7.2-0ubuntu6.1 is to be installed
              Recommends: libqt4-opengl-dev (= 4:4.7.2-0ubuntu6) but it is not going to be installed
E: Broken packages

```

I've tried various recommended incantations of:

```

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install -f qt-dev

```

and some others, but I'm afraid I'm going to really screw things up if I keep blindly entering commands. There's a good reason that you have to act as the superuser to mess with packages.

I can see that apt is not happy that newer versions of the libraries are to be installed, but I don't know what to do about it.

TIA for any help you may care to share.

---

