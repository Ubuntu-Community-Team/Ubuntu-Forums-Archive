---
title: "install cups 1.4.2 from source on 8.04"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by headhunter_unit23 on 2010-03-11
Hi,

I need (have to) to upgrade the cups 1.3.7 running on one of our ubuntu 8.04 32bit kernel servers to the latest 1.4.2. As there's no package available through apt-get I downloaded the source from cups.org.

1. Stop cupsys
2. Stop cups
3. apt-get remove cupsys

So at that point I thought the web interface pages would be removed along the rest of the package. So I didn’t even bother checking if they were still there.

4. tar xvpf cups-1.4.2-source.tar.gz
5. sudo ./configure
6. sudo make
7. sudo make check
8. sudo make install
9. /usr/sbin/cupsd –C /home/path/to/cups1.3.7BACKUP/cupsd.conf
10. [http://xxx.xxx.xxx.xxx:631](http://xxx.xxx.xxx.xxx:631)
11. And here WTF? :shock:I see the index.html from version 1.3.7, ‘right, go to /usr/share/doc/cups/ and not only do I have html pages from 1.3.7 but also the index.html from 1.3.9. If I browse a bit the admin interface I have some of the 1.4.2 pages displayed.:twisted: So I stopped here, as it seems there’s a mess in there, at least 3 cups versions mixed together, better ask than sorry.[-(

So my question is:

How do I perform a clean uninstall of cupsys and cups on my 8.04, including all the stuff stored in /usr/share/doc/cups/ so that I can recompile 1.4.2 and install it the default path.

Hopefully I copied the configuration files from the 1.3.7 so there’s always a quick way back to a running cups.:-\"

Thanks for you help,

Cheers

---

### Post by tom4everitt on 2010-03-11
Generally you need to run:

sudo apt-get remove --purge cupsys

to also remove all configuration files. (Notice the --purge option.)

---

### Post by headhunter_unit23 on 2010-03-11
thanks for the quick reply mate,

the --purge option was what I was looking for indeed.

Yet, as I've installed the 1.4.2 atop of 1.3.7 directory I'm getting error messages, when --purge the cupsys package.

Sounds like I need to manually remove the files and either attempt a reinstall of the cupsys 1.3.7 then remove with the --purge option or install 1.4.2 in the now empty directories.

I'll post the clean way to do this once I found it.

cheers

---

### Post by headhunter_unit23 on 2010-03-11
'right,

I manually removed:

rm -Rf /usr/share/cups/

then

rm -Rf /usr/share/doc/cups

and now it seems my cups 1.4.2 is running without displaying pages from previous versions.:guitar:

Now it's the time to test the server itself.

---

### Post by tom4everitt on 2010-03-11
Great, be sure to mark the thread as solved (under thread tools) if it works!

---

