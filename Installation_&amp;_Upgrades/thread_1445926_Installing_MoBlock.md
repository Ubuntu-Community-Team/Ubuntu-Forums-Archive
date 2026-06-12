---
title: "Installing MoBlock"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by chome4 on 2010-04-03
I can't seem to find the reference to a deb file via this site: 

[http://moblock-deb.sourceforge.net]("http://moblock-deb.sourceforge.net/")

Can someone point me in the direction to the deb file?

---

### Post by jre on 2010-04-05
Generally you should not download a deb file and then install it manually. You might be used to do that on a Windows based computer, but Linux distributions like Ubuntu and Debian offer a better way:
You simply tell your system where it gets an application. Then you select the applications that you want in your package manager (e.g. synaptic) and the whole rest is done automatically.
This way all dependencies of the software are installed (in Linux systems you don't get one installer with tons of additional libraries, instead the libraries are installed system wide, so that all applications that depend on them can use the same library. Also mobloquer (Grapical User Interface for moblock) depends on the moblock daemon and blockcontrol (command line interface that also does the sytem integration) - so you have three packages here already). Another advantage of this approach is that you get updates for your whole system automatically or with just "one click".

These places on the internet where your system gets software are called repositories. The information about these repositories is stored in the file /etc/apt/sources.list, but you can manage these repositories also with graphical interfaces (I don't use them, so I can't tell you which they are).
Many applications are made available through the official Ubuntu repositories. But for additional software like moblock you have to rely on 3rd party repositories. You can learn how to add this on [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) or on [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock).

Thus having said, if you still want to download the debs manually go to
[http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu/pool/main/m/moblock/](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu/pool/main/m/moblock/)
[http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu/pool/main/b/blockcontrol/](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu/pool/main/b/blockcontrol/)
[http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu/pool/main/m/mobloquer/](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu/pool/main/m/mobloquer/)

---

