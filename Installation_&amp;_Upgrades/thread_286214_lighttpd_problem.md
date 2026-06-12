---
title: "lighttpd problem"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by djmccormick on 2006-10-27
I have recently installed ubuntu 6.06 LTS and have updated using:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

I have also added the universal repository to my list of sources, though I've yet to use any non-standard packages.

Here is what I've done...
```
djmccormick@mercury:~$ sudo apt-get install lighttpd
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  openssl rrdtool apache2-utils
Recommended packages:
  php4-cgi php5-cgi
The following NEW packages will be installed:
  lighttpd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/280kB of archives.
After unpacking 848kB of additional disk space will be used.
Selecting previously deselected package lighttpd.
(Reading database ... 22959 files and directories currently installed.)
Unpacking lighttpd (from .../lighttpd_1.4.11-3ubuntu3_i386.deb) ...
Setting up lighttpd (1.4.11-3ubuntu3) ...
<!-- s:853e9a42efca88ae0dd1a83aeb215047 -->
 * Starting web server lighttpd                                                                                       [ ok ]


```

From here it seems like all is well, but nothing is being served over port 80. Also, I can't stop or restart the service:
```
djmccormick@mercury:~$ sudo /etc/init.d/lighttpd stop
 * Stopping web server lighttpd                                                                                       [fail]
djmccormick@mercury:~$ sudo /etc/init.d/lighttpd start
 * Starting web server lighttpd                                                                                       [ ok ]
djmccormick@mercury:~$ sudo /etc/init.d/lighttpd restart
 * Stopping web server lighttpd                                                                                       [fail]
djmccormick@mercury:~$ sudo /etc/init.d/lighttpd force-reload
 * Stopping web server lighttpd                                                                                       [fail]

```

So it won't stop or uninstall:
```
djmccormick@mercury:~$ sudo apt-get remove lighttpd
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  lighttpd
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 848kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 23008 files and directories currently installed.)
Removing lighttpd ...
 * Stopping web server lighttpd                                                                                       [fail]
invoke-rc.d: initscript lighttpd, action "stop" failed.
dpkg: error processing lighttpd (--remove):
 subprocess pre-removal script returned error exit status 1
 * Starting web server lighttpd                                                                                       [ ok ]
Errors were encountered while processing:
 lighttpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now I eventually removed it with the suggestions found [here]("http://ubuntuforums.org/showthread.php?t=240580"), but I'm wondering what's wrong with this package? Am I not going to be able to use lighttpd properly?

---

### Post by djmccormick on 2006-10-28
*bump*

---

### Post by dermotti on 2006-10-28
I updated from dapper to edgy and had issue starting my server.

It turned out that i needed to reinstall EAccelerator and everything worked perfect.

I assume if i didnt install Eaccelerator in the first place, the upgrade woul dhave been flawless.

---

