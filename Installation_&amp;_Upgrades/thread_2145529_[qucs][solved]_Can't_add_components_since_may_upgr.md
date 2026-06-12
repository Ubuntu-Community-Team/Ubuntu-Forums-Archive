---
title: "[qucs][solved] Can't add components since may upgrade(0.16 to 0.17)"
date: 2013-05-15
forum: Installation &amp; Upgrades
---

### Post by nolan on 2013-05-15
Hello,

I installed qucs 0.16 on ubuntu 12.10 some months ago thanks to Frans Schreuder ppa.

Some days ago I apt-get upgraded and qucs 0.17 was installed (still from the ppa).

Now I can't add components in the main viewport, the mouse cursor is always a 'forbidden' sign. I can add ground and wires through the menu though. On old projects I can copy paste components that are already on the viewport but I can't drag and drop from the left pane.

I didn't find any 0.16 packages on launchpad and compiling from 0.16 source might be tricky due to the qt-3/qt-4 transition.

So my question:
1. Did I miss any new settings in qucs that are locking the viewport somehow ?
2. Where can I find a working 0.16 'backport' ?
3. Would upgrading to RR solve my problem ?
4. Is that within the board guidelines to contact fransfrans(ppa maintainer and qucs admin) so he can have a look at this post ?

Update:
I found a deb package of qucs 0.16 on launchpad [https://launchpad.net/ubuntu/+source/qucs/0.0.16-2/+build/3518542](https://launchpad.net/ubuntu/+source/qucs/0.0.16-2/+build/3518542)
dpkg -i complained about libqt3-mt and apt-get install didn't work so I installed the libqt3-mt I found here [https://launchpad.net/ubuntu/quantal/i386/libqt3-mt/3:3.3.8-b-8ubuntu3](https://launchpad.net/ubuntu/quantal/i386/libqt3-mt/3:3.3.8-b-8ubuntu3)

Now qucs 0.16 starts up and run but I can't open old schematics, it complains about 'wrong version: 0.17!'. None of these schematics were created or modifier with 0.17. Also, the interface is coloured with an unsual palish blue. On the plus side I can drag and drop components on the viewport. But I can't open old projects.

Update:
A little more forum browsing later:
[http://sourceforge.net/p/qucs/discussion/311049/thread/92626069/?limit=25&page=1#ad75](http://sourceforge.net/p/qucs/discussion/311049/thread/92626069/?limit=25&page=1#ad75)
I just found out that drag and drop is now working differently from QT3-Version (no drag and drop, but double-click the component and click into schematic).
Sorry, If I have bothered you. 

...and solved!

---

