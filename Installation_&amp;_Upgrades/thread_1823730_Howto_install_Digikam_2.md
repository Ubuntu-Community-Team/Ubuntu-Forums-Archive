---
title: "Howto install Digikam 2"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by scott36 on 2011-08-12
Hi there,

A lot of people have been waiting for Digikam 2 since quite some time.

The final release was made on 31/07, but now I am wondering how to install this on Ubuntu?

I searched for it but could only find one thread:
[http://www.muktware.com/blogs/2087](http://www.muktware.com/blogs/2087)
This does not work for me, it only installs Digikam 1.9

Any ideas?

Thank you,
Scott

---

### Post by raja.genupula on 2011-08-12
some problem solution based approach but its gonna help you for installing it 


[http://www.digikam.org/drupal/node/600](http://www.digikam.org/drupal/node/600)

---

### Post by scott36 on 2011-08-13
Thanks for your reply,

Thats exactly the steps I followed, but it still comes up with "package not found" after typing [I]sudo apt-get install digikam2 kipi-plugins2.

Does it matter that I am using x64?


[/I]

---

### Post by realzippy on 2011-08-13
Here it works:
(you run apt-get update ??)

```
sudo add-apt-repository ppa:philip5/extra
sudo apt-get update
sudo apt-get install digikam2
```

---

### Post by scott36 on 2011-08-13
[FONT=monospace]*sudo add-apt-repository ppa:philip5/extra* and
*sudo apt-get update*
Don't give any errors

*sudo apt-get install digikam2*
Comes up with: "Pakage digikam 2 could not be found"

Whats wrong there?
[/FONT]

---

### Post by realzippy on 2011-08-13
Real sorry,have to apologise.You are right,it does not work on 64 bit.
I didn't realise that I was on my 32 bit ubuntu,which I normally only use for testing purpose.Back on my normal _64 bit it does not work.
But will try to workaround or force...

---

### Post by scott36 on 2011-08-17
Anybody else any ideas how to install Digikam2 on an 64 bit Ubuntu?

---

### Post by steve11911 on 2011-08-19
A few resources out there:

[https://scribblesandsnaps.wordpress.com/2011/03/09/install-the-latest-beta-of-digikam-on-ubuntu-10-10/](https://scribblesandsnaps.wordpress.com/2011/03/09/install-the-latest-beta-of-digikam-on-ubuntu-10-10/)

This page addresses the 64bit issue and indicates a fix with success:

[http://ubuntuku.org/22/how-to-install-compile-digikam-2-0-0-beta-from-source/](http://ubuntuku.org/22/how-to-install-compile-digikam-2-0-0-beta-from-source/)

also here:

[http://osdir.com/ml/digikam-users/2011-08/msg00088.html](http://osdir.com/ml/digikam-users/2011-08/msg00088.html)

---

### Post by mp3droid on 2011-10-08
> **realzippy said:**
> Here it works:
(you run apt-get update ??)

```
sudo add-apt-repository ppa:philip5/extra
sudo apt-get update
sudo apt-get install digikam2
```

MY FAULT for not reading the whole page of posts, BUT that command above doesn't include the kipi-plugins2 (a fact I now know all too well) The package didn't install correctly, and when running a "sudo apt-get install -f" to fix things, I get the following error. I am lost how to fix it. I'm new to linux, completely said goodbye to win7, and this week I'm wishing I hadn't. Ubuntu is soo much easier to screw up. Thanks for any help anyone can give me!!

```
kevin@wilon:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  digikam2-data
The following NEW packages will be installed:
  digikam2-data
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/6,691 kB of archives.
After this operation, 31.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 179949 files and directories currently installed.)
Unpacking digikam2-data (from .../digikam2-data_2%3a2.1.1-natty~ppa1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/digikam2-data_2%3a2.1.1-natty~ppa1_all.deb (--unpack):
 trying to overwrite '/usr/share/locale/ro/LC_MESSAGES/libkgeomap.mo', which is also in package libkgeomap-data 2.2.0-natty~ppa3
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/digikam2-data_2%3a2.1.1-natty~ppa1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by mp3droid on 2011-10-08
And after restart I got this:

```
The following packages have unmet dependencies:

digikam2: Depends: libkabc4 (>= 4:4.3.4) but 4:4.6.5-0ubuntu1 is installed
          Depends: libkcmutils4 (>= 4:4.4.95) but 4:4.6.5-0ubuntu1 is installed
          Depends: libkde3support4 (>= 4:4.4.4) but 4:4.6.5-0ubuntu1 is installed
          Depends: libkdecore5 (>= 4:4.4.95) but 4:4.6.5-0ubuntu1 is installed
          Depends: libkdeui5 (>= 4:4.5.80) but 4:4.6.5-0ubuntu1 is installed
          Depends: libkemoticons4 (>= 4:4.4.95) but 4:4.6.5-0ubuntu1 is installed
          Depends: libkfile4 (>= 4:4.4.4) but 4:4.6.5-0ubuntu1 is installed
          Depends: libkhtml5 (>= 4:4.4.4) but 4:4.6.5-0ubuntu1 is installed
          Depends: libkidletime4 (>= 4:4.4.95) but 4:4.6.5-0ubuntu1 is installed
          Depends: libkio5 (>= 4:4.4.4) but 4:4.6.5-0ubuntu1 is installed
          Depends: libkipi8 (>= 4:4.6.2) but 4:4.6.5-0ubuntu1 is installed
          Depends: libkjsapi4 (>= 4:4.4.4) but 4:4.6.5-0ubuntu1 is installed
          Depends: libknotifyconfig4 (>= 4:4.4.4) but 4:4.6.5-0ubuntu1 is installed
          Depends: libkparts4 (>= 4:4.5.80) but 4:4.6.5-0ubuntu1 is installed
          Depends: libkprintutils4 (>= 4:4.4.95) but 4:4.6.5-0ubuntu1 is installed
          Depends: libkresources4 (>= 4:4.3.4) but 4:4.6.5-0ubuntu1 is installed
          Depends: libkutils4 (>= 4:4.6.2) but 4:4.6.5-0ubuntu1 is installed
          Depends: libnepomuk4 (>= 4:4.4.4) but 4:4.6.5-0ubuntu1 is installed
          Depends: libnepomukutils4 (>= 4:4.5.80) but 4:4.6.5-0ubuntu1 is installed
          Depends: libphonon4 (>= 4:4.7.0really4.4.4) but 4:4.7.0really4.5.0-0ubuntu3 is installed
          Depends: libqt4-dbus (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.3 is installed
          Depends: libqt4-network (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.3 is installed
          Depends: libqt4-qt3support (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.3 is installed
          Depends: libqt4-sql (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.3 is installed
          Depends: libqt4-svg (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.3 is installed
          Depends: libqt4-xml (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.3 is installed
          Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.7.2-0ubuntu6.3 is installed
          Depends: libqtgui4 (>= 4:4.6.1) but 4:4.7.2-0ubuntu6.3 is installed
          Depends: libsolid4 (>= 4:4.4.4) but 4:4.6.5-0ubuntu1 is installed
          Depends: digikam2-data (= 2:2.1.1-natty~ppa1) but it is not installed

```

---

### Post by jack24 on 2011-10-11
I'm having the same problem.  Get the error message:
>  E: /var/cache/apt/archives/digikam2-data_2%3a2.1.1-natty~ppa1_all.deb: trying to overwrite '/usr/share/locale/ro/LC_MESSAGES/libkgeomap.mo', which is also in package libkgeomap-data 2.2.0-natty~ppa3

I think the problem is that the deb calls for libkgeomap-data as a dependency, but the same file is in the new digikam-data 2.2.0.

If that's the case, I either have to get the new install package to stop asking for the dependency or take it out of dgikam2-data 2.2.0.

If I figure it out, I'll let you know.

---

