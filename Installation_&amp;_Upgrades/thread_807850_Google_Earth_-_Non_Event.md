---
title: "Google Earth - Non Event"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by hundred1906 on 2008-05-26
Installed GoogleEarth via Synaptic but where is it?

Appears to install correctly and there are various files installed. But how do I start it up. I was expecting a new entry on the Applications bar - say under accessories but can find nothing.

Hardy Heron.

---

### Post by hal8000 on 2008-05-26
> **hundred1906 said:**
> Installed GoogleEarth via Synaptic but where is it?

Appears to install correctly and there are various files installed. But how do I start it up. I was expecting a new entry on the Applications bar - say under accessories but can find nothing.

Hardy Heron.


No, my friend, if you look at Synaptics description:
"
This utility makes it possible to build your own personal Debian package of Google Earth. The packaging itself is Free Software, but the Google Earth program is governed by the copyright holder (Google), so you may be limited as to what you can do with the resulting package (i.e. no redistribution, etc). This package will simply help you create the package--it is your responsibility to use the resulting package responsibly."

The package allows you to build a debian package, thats all.

I'm using Hardy Heron myself so decided to install. Point your browser at
the following link:
[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

Download the file to your desktop. Open a terminal and type

cd Desktop
chmod a+x GoogleEarthLinux.bin

this allows you to install it so type
./GoogleEarthLinux.bin

(assuming your terminal is still at ~/Desktop)
The packge will install and you have a launcher on the desktop, you can add it your menu just by creating a new launcher.

Hope that helps.

---

### Post by hundred1906 on 2008-05-26
Stupid me. Thanks, your suggestion worked. I will have to look more carefully next time but still would not have worked out the command sequence needed.

---

### Post by raymondvillain on 2008-06-05
> **hal8000 said:**
> No, my friend, if you look at Synaptics description:
"
This utility makes it possible to build your own personal Debian package of Google Earth. The packaging itself is Free Software, but the Google Earth program is governed by the copyright holder (Google), so you may be limited as to what you can do with the resulting package (i.e. no redistribution, etc). This package will simply help you create the package--it is your responsibility to use the resulting package responsibly."

The package allows you to build a debian package, thats all.

I'm using Hardy Heron myself so decided to install. Point your browser at
the following link:
[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

Download the file to your desktop. Open a terminal and type

cd Desktop
chmod a+x GoogleEarthLinux.bin

this allows you to install it so type
./GoogleEarthLinux.bin

(assuming your terminal is still at ~/Desktop)
The packge will install and you have a launcher on the desktop, you can add it your menu just by creating a new launcher.

Hope that helps.


I did the same thing as hundred1906.  If I follow your instructions, will I be using the package I installed from the synaptics menu, or will I be installing Google Earth from the Google website?

---

