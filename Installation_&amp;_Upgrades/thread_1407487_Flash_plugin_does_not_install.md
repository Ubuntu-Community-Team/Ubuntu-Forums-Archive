---
title: "Flash plugin does not install"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by Konrad Ansehelm on 2010-02-15
I'm having problems with the Flash plugin since yesterday. It is caused by a file which is not available in the repo:
```
$ sudo apt-get install flashplugin-installer
[...]
Downloading...
--2010-02-15 15:59:39--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.42.34.orig.tar.gz
Resolving archive.canonical.com... 91.189.90.142
Connecting to archive.canonical.com|91.189.90.142|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-02-15 15:59:39 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

```In that [archive]("http://archive.canonical.com/pool/partner/a/adobe-flashplugin/") the file adobe-flashplugin_10.0.42.34.orig.tar.gz is missing, but there is a file for 10.0.45.2. I couldn't figure out how I can install this version (does not even show up when I select all software sources including backports).

For the moment I reverted to 10.0.32.18.

---

### Post by darkod on 2010-02-15
Remove the flash plugins that you're trying to install yourself. I spent days trying to get this working on firefox on 64bit karmic.
The solutions was very simple. Download the 10.0.45 archive from the link you mentioned. Unpack and it should have a single file there called something like libxxxx.so
That is the actual library. Just copy it in your Home folder in the mozilla plugins folder, /.mozilla/plugins

In Home you need to press Ctrl + H to see the hide folders, including .mozilla and if plugins folder doesn't exist inside, just create it.

Close and reopen firefox if it was open. Best way to test is [www.speedtest.net](www.speedtest.net), it uses flash to test the connection.

---

### Post by darkod on 2010-02-15
I got my library from the link in post #3 from here:
[http://ubuntuforums.org/showthread.php?t=1306113](http://ubuntuforums.org/showthread.php?t=1306113)

Worked perfect as soon as you save it in home/.mozilla/plugins

---

