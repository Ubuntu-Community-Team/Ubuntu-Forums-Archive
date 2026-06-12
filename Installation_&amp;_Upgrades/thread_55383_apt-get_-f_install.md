---
title: "apt-get -f install"
date: 2005-08-08
forum: Installation &amp; Upgrades
---

### Post by cjoshuav on 2005-08-08
I've noticed that if I try to install an application and it doesn't seem to work because of missing dependent librararies typing

```
sudo apt-get -f install
```

goes and finds those libraries and allows me to then install the app.

Am I doing this bass ackwards or is this a common way to deal with this?

Also, is there a Linux MP3 player that has a feature comparable to WinAmp 5's Media Library?  XMMS seems a bit sparse in the music management department.

- Joshua

---

### Post by dave9191 on 2005-08-08
If apt-get dependancies break, you can tell apt-get to fix it all by typing apt-get -f intsall. So its a common way to fix it. 

I havent seen winamp since verion 3 so I cant compare. But amoraK is a brilliant music player with a nice liabry and ipod sync features. Its a kde app, but you can still use it in gnome. Its in the repositories. 

Dave

---

### Post by FreeJack on 2005-08-08
I've a problem please help!!! acl-pro-installer i cant install it 
[B]"Setting up acl-pro-installer (6.2.31) ...
Aborting
dpkg: error processing acl-pro-installer (--configure):
subprocess post-installation script returned error exit status 1
Setting up xmms (1.2.10-2ubuntu1) ...

Errors were encountered while processing:
acl-pro-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)"[B]
now can some please explain to me what directory he means??? cause i'm sure have no idea
please help!!!!!! :(

---

### Post by rwabel on 2005-08-10
[QUOTE=cjoshuav]I've noticed that if I try to install an application and it doesn't seem to work because of missing dependent librararies typing

```
sudo apt-get -f install
```

goes and finds those libraries and allows me to then install the app.

Am I doing this bass ackwards or is this a common way to deal with this?

Also, is there a Linux MP3 player that has a feature comparable to WinAmp 5's Media Library?  XMMS seems a bit sparse in the music management department.

- Joshua[/QUOTE]
 xmms has a ugly UI, have a look at beep-media-player. but it's basically the same as xmms

---

