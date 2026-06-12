---
title: "Google Earth ver 5 (beta)"
date: 2009-02-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by plun on 2009-02-03
is out but not working for me....

Howto install:
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)


But totally broken....

```
plun@plun:~/Desktop$ sudo ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux **_5.0.11337.1968._**.............................................................
loki_setup: Suspect size value for option option

/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
loki_setup: Suspect size value for option option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...
Warning: Unable to create prefs directory '/root/.googleearth'. File exists.
**./googleearth-bin: relocation error: /usr/lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference**

```


If someone else can verify it a bug must be filed to Google directly...

---

### Post by philinux on 2009-02-03
I would install it without sudo.

---

### Post by plun on 2009-02-03
> **philinux said:**
> I would install it without sudo.

Well, I tried that also but the same error for me.

---

### Post by philinux on 2009-02-03
[http://ubuntuforums.org/showthread.php?p=6664407](http://ubuntuforums.org/showthread.php?p=6664407)

---

### Post by gjoellee on 2009-02-03
try this:
```

 cd /path/to/installation/folder
 mv libcrypto.so.0.9.8 bkp_libcrypto.so.0.9.8

```in my case the installation folder was in /home/$USER/google-earth (I did not install with sudo)

---

### Post by ato on 2009-02-03
What about 
```
sudo apt-get install googleearth-package
/usr/bin/make-googleearth-package --force
```
and install the .deb package ;)

---

### Post by gjoellee on 2009-02-03
> **ato said:**
> What about 
```
sudo apt-get install googleearth-package
/usr/bin/make-googleearth-package --force
```and install the .deb package ;)

Is that google-earth version 5.0?

---

### Post by ato on 2009-02-03
Yes
but it needs a little hack found here
[http://ubuntuforums.org/showthread.php?t=195382&page=27]("http://ubuntuforums.org/showthread.php?t=195382&page=27")

```
cd /usr/lib/googleearth
sudo mv libcrypto.so.0.9.8 bkp_libcrypto.so.0.9.8
```

---

### Post by ronacc on 2009-02-03
as a mater of intrest here is a link to the online version of google mars 
it works fine in Opera , I haven't tried FF yet.
[http://www.google.com/mars/](http://www.google.com/mars/)

---

### Post by tghe-retford on 2009-02-03
I managed to get Google Earth running fine after I changed the name of libcrypto.so.0.9.8. However, the font looks weird as shown below:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=102038&stc=1&d=1233696590[/IMG]

~/.config/Google/GoogleEarthPlus.conf doesn't change the font as it used to.

---

### Post by plun on 2009-02-03
> **ato said:**
> Yes
but it needs a little hack found here
[http://ubuntuforums.org/showthread.php?t=195382&page=27]("http://ubuntuforums.org/showthread.php?t=195382&page=27")

```
cd /usr/lib/googleearth
sudo mv libcrypto.so.0.9.8 bkp_libcrypto.so.0.9.8
```

Yup this one works....thanks !


I am doing exactly as the wiki :D  including download !!
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)


Google Earth now installs **within home**.... at least for me.


```
plun@plun:~$ cd google-earth
plun@plun:~/google-earth$ sudo mv libcrypto.so.0.9.8 bkp_libcrypto.so.0.9.8

```

---

### Post by plun on 2009-02-03
> **ronacc said:**
> as a mater of intrest here is a link to the online version of google mars 
it works fine in Opera , I haven't tried FF yet.
[http://www.google.com/mars/](http://www.google.com/mars/)

You have Mars within GE....;)

[[img]http://ubuntu-pics.de/thumb/9296/snapshot6_cTji15.png[/img]](http://ubuntu-pics.de/bild/9296/snapshot6_cTji15.png)


This blog is excellent about GE

[http://gearthblog.com/](http://gearthblog.com/)

.

---

### Post by plun on 2009-02-03
Just a followup about this bug.....

[http://www.google.com/support/forum/p/earth/thread?tid=7b1b524777b9b982&hl=en](http://www.google.com/support/forum/p/earth/thread?tid=7b1b524777b9b982&hl=en)

Every Debian/Ubuntu box is broken with this error, not a Jaunty problem.

---

### Post by Starks on 2009-02-03
The atmosphere view is slow as hell.

---

### Post by plun on 2009-02-03
> **Starks said:**
> The atmosphere view is slow as hell.

Intel....?  ;)

---

### Post by Starks on 2009-02-04
Indeed. GEM, UXA, DRI2...

Doesn't help at all.

<___<

---

### Post by andrewabc on 2009-02-04
The newest release on windows includes google updater, which runs in the background nonstop and constantly tries to connect to google servers.

I am very disappointed with google updater being bundled with the newest google. I think I solved the problem by deleting the google updater folder in program files. There was no mention that it was going to be installed, and there was no way to uninstall it (doesn't show up in add/remove programs, not mentioned in startup menu).

---

### Post by ronacc on 2009-02-04
thats typical of anything windows , think WGA and all the other malware/spyware that MS dumps on you.

---

