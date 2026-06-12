---
title: "Ubuntu 10.10 - firefox 10 - failed to create drawable"
date: 2013-03-15
forum: Installation &amp; Upgrades
---

### Post by sebastiaopburnay on 2013-03-15
Hi,

I have a 32bit Ubuntu 10.10 (maverick) and as I want this version to stay the same I've edited /etc/sources.list as follows:
> **/etc/apt/sources.list]# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) maverick main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) maverick-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) maverick-security main restricted universe multiverse

# Optional
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
[/QUOTE]

All fine untill here... I also needed my firefox to be in the 10.0 version and to do so, I've fetched manually the tar.bz2 package from firefox' page dedicated to old releases () said:**
> 
root@server: tar -xjvf firefox-10.0.tar.bz2 -C /opt
root@server: ln -s /opt/firefox/firefox /usr/bin/firefox


I can launch firefox from the CLI and it opens, I can browse the web, etc...

My problem is that an apparenyt error/warning message is sent to the stdout saying «failed to create drawable»

Do you know what it is and how to correct it?

Furthermore, I would like to add this app to the graphical menu in «Applications > Internet» section/menu.

Thank you very much for the help

Yours sincerely,
sebastiaopburnay

---

### Post by nibal on 2013-03-15
@sebastiaopburnay:
> I can launch firefox from the CLI and it opens, I can browse the web, etc...

> My problem is that an apparenyt error/warning message is sent to the stdout saying «failed to create drawable»

> Do you know what it is and how to correct it?

Try:

```

dbus-launch firefox

```

And see if it helps. If it doesn't, since you have the sources you might try:

```

grep -rl "drawable" firefox/

```

And see what the code tries to do.

HTH,
Nikos

---

### Post by sebastiaopburnay on 2013-03-15
Well, Ive tried launching firefox wth the 'dbus-launch', but I got the same output «failed to create drawable».

About the grep (good idea, by the way) it indicates a single match upon a binary library file:
```
root@SERVER:/opt/firefox# grep -irn 'drawable' *
Binary file libxul.so matches
```
So, I don't really know what to do about it

P.S.: I've forgotten to mention that this machine is a guest VM with, with an ESX 4.1 host, the Ubuntu guest's VMware Tools are version 8.3.2

---

### Post by nibal on 2013-03-15
> **sebastiaopburnay said:**
> Well, Ive tried launching firefox wth the 'dbus-launch', but I got the same output «failed to create drawable».

About the grep (good idea, by the way) it indicates a single match upon a binary library file:
```
root@SERVER:/opt/firefox# grep -irn 'drawable' *
Binary file libxul.so matches
```
So, I don't really know what to do about it

Yeap. Don't grep the binary file, only the source tree, unless you can read binary!:) 
I magine you downloaded and compiled firefox from the sources, right? At least now you know
it should be a simple case, since it is referenced only once.

BR,
Nikos

---

### Post by sebastiaopburnay on 2013-03-15
> **nibal said:**
> Yeap. Don't grep the binary file, only the source tree

Sorry for my ignorance, but I don't really know what you mean (i.e. what to do)

---

### Post by nibal on 2013-03-15
> **sebastiaopburnay said:**
> Sorry for my ignorance, but I don't really know what you mean (i.e. what to do)

You extracted firefox-10.0.tar.bz2 in /opt. Right?
Could you please post 10 lines from the output of:

```

ls -la /opt/firefox*

```

Thanks,
Nikos

---

### Post by sebastiaopburnay on 2013-03-18
```
root@SERVER:~# ls -la /opt/firefox*
total 31672
drwxr-xr-x 10 root root     4096 2012-01-29 11:18 .
drwxr-xr-x  6 root root     4096 2013-03-11 20:06 ..
-rw-r--r--  1 root root     2149 2012-01-29 11:18 application.ini
-rw-r--r--  1 root root    11678 2012-01-29 11:18 blocklist.xml
drwxr-xr-x  3 root root     4096 2012-01-29 11:18 chrome
-rw-r--r--  1 root root       36 2012-01-29 11:18 chrome.manifest
drwxr-xr-x  2 root root     4096 2012-01-29 11:18 components
-rwxr-xr-x  1 root root   134036 2012-01-29 11:18 crashreporter
-rw-r--r--  1 root root     3803 2012-01-29 11:18 crashreporter.ini
-rw-r--r--  1 root root      583 2012-01-29 11:18 crashreporter-override.ini

```

---

### Post by nibal on 2013-03-18
> **sebastiaopburnay said:**
> ```
root@SERVER:~# ls -la /opt/firefox*
total 31672
drwxr-xr-x 10 root root     4096 2012-01-29 11:18 .
drwxr-xr-x  6 root root     4096 2013-03-11 20:06 ..
-rw-r--r--  1 root root     2149 2012-01-29 11:18 application.ini
-rw-r--r--  1 root root    11678 2012-01-29 11:18 blocklist.xml
drwxr-xr-x  3 root root     4096 2012-01-29 11:18 chrome
-rw-r--r--  1 root root       36 2012-01-29 11:18 chrome.manifest
drwxr-xr-x  2 root root     4096 2012-01-29 11:18 components
-rwxr-xr-x  1 root root   134036 2012-01-29 11:18 crashreporter
-rw-r--r--  1 root root     3803 2012-01-29 11:18 crashreporter.ini
-rw-r--r--  1 root root      583 2012-01-29 11:18 crashreporter-override.ini

```
Smt is very wrong. This is chrome, not firefox. Besides, during yuor installation you linked to /opt/firefox/firefox. I don't see it, where is it?
Please type output of:

```

ls -la $(which firefox)
ls -la $(which chrome)

```

BR,
Nikos

---

### Post by sebastiaopburnay on 2013-03-18
It also seemed strange to me that there was a chrome inside the /opt/firefox folder, but the app is really firefox (it was downloaded from Mozilla).

```
root@SERVER:/# ls -la $(which firefox)
lrwxrwxrwx 1 root root 20 2013-03-15 11:24 /usr/bin/firefox -> /opt/firefox/firefox
```


```
root@SERVER:/# ls -la $(which chrome)
total 116
drwxr-xr-x  24 root root  4096 2012-08-10 17:34 .
drwxr-xr-x  24 root root  4096 2012-08-10 17:34 ..
drwsrwxrwx   3 root root  4096 2013-02-01 15:09 bash
drwxr-xr-x   2 root root  4096 2011-10-25 15:38 bin
drwxr-xr-x   3 root root  4096 2013-03-15 12:36 boot
-rw-r--r--   1 root root    24 2012-08-10 17:34 CdbsMutex
drwxr-xr-x   2 root root  4096 2011-02-18 17:48 cdrom
drwxr-xr-x  16 root root  3960 2013-03-15 12:36 dev
drwxr-xr-x 148 root root 12288 2013-03-15 12:41 etc
drwxr-xr-x   4 root root  4096 2011-02-18 18:10 home
lrwxrwxrwx   1 root root    33 2011-02-18 17:51 initrd.img -> boot/initrd.img-2.6.35-22-generic
drwxr-xr-x  16 root root 12288 2011-02-22 10:07 lib
drwx------   2 root root 16384 2011-02-18 17:43 lost+found
drwxr-xr-x   3 root root  4096 2013-03-15 12:41 media
drwxr-xr-x   3 root root  4096 2013-03-15 12:33 mnt
drwxr-xr-x   6 root root  4096 2013-03-11 20:06 opt
dr-xr-xr-x 382 root root     0 2013-03-14 18:36 proc
drwx------  32 root root  4096 2013-03-15 11:02 root
drwxr-xr-x   2 root root  4096 2013-03-15 12:33 sbin
drwxr-xr-x   2 root root  4096 2010-05-09 16:54 selinux
drwxr-xr-x   2 root root  4096 2010-10-07 16:56 srv
drwxr-xr-x  12 root root     0 2013-03-14 18:36 sys
drwxrwxrwt  37 root root  4096 2013-03-18 11:02 tmp
drwxr-xr-x  14 root root  4096 2013-03-11 10:35 usr
drwxr-xr-x  17 root root  4096 2012-08-10 16:26 var
lrwxrwxrwx   1 root root    30 2011-02-18 17:51 vmlinuz -> boot/vmlinuz-2.6.35-22-generic
drwx------   2 root root  4096 2012-06-25 17:55 .w3m

```

---

### Post by nibal on 2013-03-18
@sebastiaopburnay:
> It also seemed strange to me that there was a chrome inside the  /opt/firefox folder, but the app is really firefox (it was downloaded  from Mozilla).

You are right. I guess there is a lot of cooperation between Mozilla and Google.;)
I have the same setup from the default (binary) Ubuntu installation.
This is just binary. You could download the sources to 10.0.0 and make them.

I am sorry but I cannot help you with a binary release. :( However the firefox
users group would be able to.

BL,
Nikos

---

