---
title: "APR Location for Tomcat Native"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by carljokl on 2008-09-11
I am trying to install the tomcat native connector to intergrate Tomcat into Apache. Both Apache and Tomcat are installed and run fine. The problem is that I have to supply a locaton to the APR directory or apr-config. I cannot find a valid setting for this. I am using the server version of Ubuntu 8.04. After trawling through the internet any references to the location have been thrown back as invalid when runing ./configure on the tomcat-navite folder decompressed from the tomcat-native archive bundled in the bin directory of Tomcat. I wonder if I might need to download some package first perhaps. It is suggested that Apache web server 2.2+ should be bundled with APR as standard and the Apache web server version I have is 2.2.8

Can anyone help me

---

### Post by lechal on 2008-11-06
Hi,

There is a package that contains tomcat native library that can be installed via apt-get: libtcnative-1. Maybe that's ok for you.

I had to download and compile it because I wanted to disable ipv6 as there was an error when enabling it on tomcat and I didn't want to disable it completely in the machine.

If you want to build it yourself you will need to download apr source too. You can use apt-get to install libapr1.0-dev or get it from the web. I got it from [http://apache.sunsite.ualberta.ca/apr/#apr](http://apache.sunsite.ualberta.ca/apr/#apr)).

You might have to point the --with-apr configure parameter to the apr source folder, I'm not sure if it is found by default when using apt-get.

Hope it helps.
Jorge

---

