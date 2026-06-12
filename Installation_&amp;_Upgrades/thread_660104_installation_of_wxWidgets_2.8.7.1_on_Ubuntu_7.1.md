---
title: "installation of wxWidgets 2.8.7.1 on Ubuntu 7.1"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by darck on 2008-01-06
I've found info how to add wxWidgets to repository:

build against wxWidgets 2.8.7.1 from:
deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) etch-wx main

key-import to apt's trusted keys:
wget -q [http://apt.wxwidgets.org/key.asc](http://apt.wxwidgets.org/key.asc) -O-  | sudo apt-key add -

But problem is, that, when i tray to install wxWidgets, it says that i have too old libpango. There isn't any newer in repository. There is newer for Ubuntu Hardy. I downloaded it, tried to install and the same - it says me i have too old libc6 and libdatrie, i tried install newer libdatrie and the same. ENDLESS CIRCLE !!!

How to simply install wxWidgets 2.8.7.1 without all this complications.
It's needed for the newest Code::Blocks c++ programming enviroment.

-----------------
i got information in another forum. Solution is using feisty debs.
instead deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) gutsy-wx main
deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) feisty-wx main

and all is ok

---

