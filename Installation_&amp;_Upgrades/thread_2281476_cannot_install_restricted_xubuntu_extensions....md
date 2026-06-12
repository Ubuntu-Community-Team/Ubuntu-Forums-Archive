---
title: "cannot install restricted xubuntu extensions..."
date: 2015-06-07
forum: Installation &amp; Upgrades
---

### Post by hmag on 2015-06-07
Hello

The software center cannot install xubuntu extensions for proprietary extensions (flash, mp3, ...)

The issue is that the packages are not found on the server, as below

```
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/oxide-qt/liboxideqtcore0_1.4.3-0ubuntu0.14.04.1_i386.deb 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/oxide-qt/oxideqt-codecs-extra_1.4.3-0ubuntu0.14.04.1_i386.deb 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-codecs-ffmpeg-extra_40.0.2214.111-0ubuntu0.14.04.1.1069_i386.deb 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/liba/libav/libswscale2_9.16-0ubuntu0.14.04.1_i386.deb 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.442ubuntu0.14.04.1_i386.deb 404  Not Found [IP: 91.189.91.15 80]
```

My internet connection is OK, I am using the same now. The upgrade of xubuntu is on-going with no issue.
Trying to get the above files using Firefox returns the following. Clearly the packages are not on the server. Why ?
Thanks!
hmag
[h=1]Not Found[/h] The requested URL /ubuntu/pool/main/o/oxide-qt/liboxideqtcore0_1.4.3-0ubuntu0.14.04.1_i386.deb was not found on this server.
 [HR][/HR] Apache/2.2.22 (Ubuntu) Server at security.ubuntu.com Port 80

---

### Post by bapoumba on 2015-06-07
With the first and last error line, seems that you are not requesting the proper file number (I have not checked the others).
Please see here :
[http://security.ubuntu.com/ubuntu/pool/main/o/oxide-qt/](http://security.ubuntu.com/ubuntu/pool/main/o/oxide-qt/)
[http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/)

If you are sure about your repositories, please run :
```
sudo apt-get update
sudo apt-get upgrade
```
You may not have updated your lists.

Then try :
```
sudo apt-get install xubuntu-restricted-extras
```

If you are not sure about your repos, please post :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by deadflowr on 2015-06-07
> Trying to get the above files using Firefox returns the following. Clearly the packages are not on the server. Why ?

Simple really. 
All those packages have been upgraded to newer versions, so the versions you are trying to install no longer exist on the server.
Run a system update.
In fact you can just do a quick 
```
sudo apt-get update
```
and all the latest versions for those packages should show.
(As long as no errors are reported)

You might as well also run a
```
sudo apt-get upgrade
```
as well, to keep the system up-to-date.

Edit: HaHa, Ninja'd

---

