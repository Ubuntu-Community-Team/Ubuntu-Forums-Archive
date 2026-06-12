---
title: "electric sheep compile"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-10-30
im going to compile electric sheep from the SVN repo.  as of right now its broken for me....

i talked to the flam 3 dev and he said move from 82 backwards until i get a compile.....  i love source especially when it blows up....

svn co -r 82 [http://electricsheep.googlecode.com/svn/trunk/](http://electricsheep.googlecode.com/svn/trunk/) electricsheep-read-only

moving to libglewmx1.6-dev from 1.5 and removing 1.5 from system, and adding wx-common, glee-dev

this builds producing errors for me that are telling me i need moar new version of WX widgets....

so i nab the latest DEV wx widgets to get this beast compiled...

[http://downloads.sourceforge.net/project/wxwindows/2.9.2/wxWidgets-2.9.2.tar.bz2?r=http%3A%2F%2Fwww.wxwidgets.org%2Fdownloads%2F&ts=1320004198&use_mirror=superb-dca2](http://downloads.sourceforge.net/project/wxwindows/2.9.2/wxWidgets-2.9.2.tar.bz2?r=http%3A%2F%2Fwww.wxwidgets.org%2Fdownloads%2F&ts=1320004198&use_mirror=superb-dca2)

moving to libglewmx1.6-dev from 1.5 and removing 1.5 from system, and adding wx-common

to stop some build errors

sudo ln -s /usr/include/wx-2.9/wx /usr/include/wx
sudo ln -s /usr/lib/wx/include/base-unicode-release-2.8/wx/setup.h /usr/include/wx

ugggg more and more source problems...  hanging threads of mplayer from repo electric sheep

more to come, ill edit this so dont comment my half built thread plz!

---

