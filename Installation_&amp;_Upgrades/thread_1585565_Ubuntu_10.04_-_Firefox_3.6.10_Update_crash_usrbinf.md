---
title: "Ubuntu 10.04 - Firefox 3.6.10 Update crash /usr/bin/firefox doesn't exist"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by rfv-370 on 2010-09-30
Hello,

I had a crash when updating via the update manager from Firefox 3.5.x to 3.6.10..; And I can't get Firefox to work at all.

I get an error 1 or error 2 return(depends on the presence or not of the symlink) mentionning that /usr/bin/firefox doesn't exist. It is weird as /usr/bin/firefox is existing on my system....!

I searched around but re-establishing the symlink does not work for me...

I tried to purge the package with apt-get then re-install but nothing would work...

Any ideas?

Thanks

Robert

```

rfv@rfv-ubt:/$ ls -al /usr/bin/firefox
lrwxrwxrwx 1 root root 31 2010-09-30 23:36 /usr/bin/firefox -> /usr/lib/firefox-3.6.10/firefox
rfv@rfv-ubt:/$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox
rfv@rfv-ubt:/$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firefox (3.6.10+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)
rfv@rfv-ubt:/$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox
rfv@rfv-ubt:/$ sudo apt-get install -f firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firefox (3.6.10+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)
rfv@rfv-ubt:/$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox
rfv@rfv-ubt:/$ cd /usr/lib
rfv@rfv-ubt:/usr/lib$ ls fire*
firefox-3.6.10:
application.ini           crashreporter-override.ini  libnss3.so      libsmime3.so    modules
blocklist.xml             distribution                libnssckbi.so   libsoftokn3.so  platform.ini
browserconfig.properties  icons                       libnssdbm3.so   libsqlite3.so   run-mozilla.sh
chrome                    libfreebl3.so               libnssutil3.so  libssl3.so
components                libmozjs.so                 libplc4.so      libxpcom.so
crashreporter.ini         libnspr4.so                 libplds4.so     libxul.so

firefox-addons:
extensions  plugins  searchplugins
rfv@rfv-ubt:/usr/lib$ cd firefox-3.6.10
rfv@rfv-ubt:/usr/lib/firefox-3.6.10$ ls
application.ini           crashreporter-override.ini  libnss3.so      libsmime3.so    modules
blocklist.xml             distribution                libnssckbi.so   libsoftokn3.so  platform.ini
browserconfig.properties  icons                       libnssdbm3.so   libsqlite3.so   run-mozilla.sh
chrome                    libfreebl3.so               libnssutil3.so  libssl3.so
components                libmozjs.so                 libplc4.so      libxpcom.so
crashreporter.ini         libnspr4.so                 libplds4.so     libxul.so
rfv@rfv-ubt:/usr/lib/firefox-3.6.10$ ls -l
total 19516
-rw-r--r-- 1 root root     2042 2010-09-15 21:21 application.ini
-rw-r--r-- 1 root root     4137 2010-09-15 21:21 blocklist.xml
-rw-r--r-- 1 root root       49 2010-09-15 21:21 browserconfig.properties
drwxr-xr-x 3 root root     4096 2010-09-30 23:30 chrome
drwxr-xr-x 2 root root     4096 2010-09-30 23:30 components
-rw-r--r-- 1 root root     3803 2010-09-15 21:21 crashreporter.ini
-rw-r--r-- 1 root root      583 2010-09-15 21:21 crashreporter-override.ini
drwxr-xr-x 2 root root     4096 2010-09-30 23:30 distribution
drwxr-xr-x 2 root root     4096 2010-09-30 23:29 icons
-rw-r--r-- 1 root root   300372 2010-09-15 21:28 libfreebl3.so
-rw-r--r-- 1 root root  1392648 2010-09-15 21:28 libmozjs.so
-rw-r--r-- 1 root root   207576 2010-09-15 21:28 libnspr4.so
-rw-r--r-- 1 root root   875916 2010-09-15 21:28 libnss3.so
-rw-r--r-- 1 root root   351464 2010-09-15 21:28 libnssckbi.so
-rw-r--r-- 1 root root   124220 2010-09-15 21:28 libnssdbm3.so
-rw-r--r-- 1 root root    83252 2010-09-15 21:28 libnssutil3.so
-rw-r--r-- 1 root root    13644 2010-09-15 21:28 libplc4.so
-rw-r--r-- 1 root root     9496 2010-09-15 21:28 libplds4.so
-rw-r--r-- 1 root root   124684 2010-09-15 21:28 libsmime3.so
-rw-r--r-- 1 root root   186188 2010-09-15 21:28 libsoftokn3.so
-rw-r--r-- 1 root root   511908 2010-09-15 21:28 libsqlite3.so
-rw-r--r-- 1 root root   169984 2010-09-15 21:28 libssl3.so
-rw-r--r-- 1 root root    13512 2010-09-15 21:28 libxpcom.so
-rw-r--r-- 1 root root 15460196 2010-09-15 21:28 libxul.so
drwxr-xr-x 2 root root     4096 2010-09-30 23:30 modules
-rw-r--r-- 1 root root       50 2010-09-15 21:21 platform.ini
-rwxr-xr-x 1 root root    10469 2010-09-15 21:21 run-mozilla.sh
rfv@rfv-ubt:/usr/lib/firefox-3.6.10$ 


```

---

### Post by sikander3786 on 2010-09-30
DId you try

```

sudo apt-get install -f

```

Also under Synaptic's Edit Menu, select Fix Broken Packages.

**[COLOR="Magenta"]Edit:[/COLOR]** Does sudo apt-get update give any errors?

---

### Post by rfv-370 on 2010-09-30
Hello,

Indeed, I tried but I get an Error 1 return...

:(

```

sudo apt-get install -f
[sudo] password for rfv: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firefox (3.6.10+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by sikander3786 on 2010-09-30
What about

```

sudo dpkg --configure firefox

```

---

### Post by rfv-370 on 2010-10-01
Hello,

I tried that as well...

but no success....

(I tried complete removal from synaptic package manager and re-install but not working either).

Any further idea of what to do ?

Best,

```

sudo dpkg --configure firefox
[sudo] password for rfv: 
Setting up firefox (3.6.10+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox


```

---

### Post by sikander3786 on 2010-10-01
```

sudo apt-get clean

```

and again

```

sudo apt-get install -f

```

Otherwise you'll have to manually clean up your apt-get cache. See post # 5 in this thread.

[http://ubuntuforums.org/showthread.php?p=9880309](http://ubuntuforums.org/showthread.php?p=9880309)

---

### Post by rfv-370 on 2010-10-01
Sikander,

I tried but no getting better...

It is really strange...

Any ideas?

Best,

```

rfv@rfv-ubt:~$ sudo apt-get clean
[sudo] password for rfv: 
rfv@rfv-ubt:~$ sudo apt-get clean
rfv@rfv-ubt:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firefox (3.6.10+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by sikander3786 on 2010-10-01
Did some research.

[http://ubuntuforums.org/showthread.php?t=1446039](http://ubuntuforums.org/showthread.php?t=1446039)

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/512937](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/512937)

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/524947](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/524947)

---

### Post by rfv-370 on 2010-10-01
Hi Sikander,

Before posting I tried search and found that. I checked the symlink but it is existing as well as the directory...

I have never used other packages referred to in the bug reports (ie ubuntuzilla, etc..)

Really weird...


```

ls -al /usr/bin/firefox
lrwxrwxrwx 1 root root 31 2010-09-30 23:36 /usr/bin/firefox -> /usr/lib/firefox-3.6.10/firefox
rfv@rfv-ubt:~$ ls -al firefox.ubuntu
ls: cannot access firefox.ubuntu: No such file or directory
rfv@rfv-ubt:~$ 

```

---

### Post by lovinglinux on 2010-10-01
Try this:


```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by rfv-370 on 2010-10-02
Thanks.
It advanced one step.
Firefox installed and I got a start-up but once the Firefox window appears it freezes...
Where is the log/trace of Firefox?
best
Robert

---

### Post by rfv-370 on 2010-10-02
Finally got it to start...
Thanks you all.

best
:guitar:

---

