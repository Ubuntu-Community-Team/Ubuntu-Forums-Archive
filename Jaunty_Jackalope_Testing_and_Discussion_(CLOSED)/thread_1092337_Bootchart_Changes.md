---
title: "Bootchart Changes"
date: 2009-03-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ayates on 2009-03-10
The new bootchart package says that charts can be generated with 'pybootchartgui'. I can't seem to find this package.
Does anyone know how to get it ? All it does now is dump the .tgz data into /var/log/bootchart, but doesn't produce the chart like it use to.

---

### Post by pah99 on 2009-03-13
This package has not been added to the repository yet. To install it, go to this: [http://launchpadlibrarian.net/23750286/pybootchartgui_0%2Br102_all.deb](http://launchpadlibrarian.net/23750286/pybootchartgui_0%2Br102_all.deb) Download and install. If that doesn't work, go to [https://launchpad.net/ubuntu/jaunty/+queue](https://launchpad.net/ubuntu/jaunty/+queue) and download from there. After that, type in a terminal the following: pybootchartgui /var/log/bootchart

this will open up the picture of your boot up.

---

### Post by ayates on 2009-03-13
Thanks for the answer. That works fine for now.

---

