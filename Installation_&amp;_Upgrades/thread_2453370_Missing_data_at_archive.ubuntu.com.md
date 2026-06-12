---
title: "Missing data at archive.ubuntu.com"
date: 2020-11-09
forum: Installation &amp; Upgrades
---

### Post by af-crm on 2020-11-09
```


$ sudo apt -y update && sudo apt -y upgrade && sudo apt autoremove -y && sudo apt install freeipa-client

* * * * * * * * * * * * * * * * * * * * 

Need to get 24.7 MB of archives.
After this operation, 115 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Err:1 http://ppa.launchpad.net/certbot/certbot/ubuntu bionic/main amd64 python-augeas all 0.5.0-1+ubuntu18.04.1+certbot+1
  Temporary failure resolving 'ppa.launchpad.net'
Ign:2 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libwbclient0 amd64 2:4.7.6+dfsg~ubuntu-0ubuntu2.21
Ign:3 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libpython2.7-minimal amd64 2.7.17-1~18.04ubuntu1.2
Ign:4 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 python2.7-minimal amd64 2.7.17-1~18.04ubuntu1.2
Err:5 http://archive.ubuntu.com/ubuntu bionic/main amd64 python-minimal amd64 2.7.15~rc1-1
  Temporary failure resolving 'archive.ubuntu.com'
Ign:6 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libpython2.7-stdlib amd64 2.7.17-1~18.04ubuntu1.2
Ign:7 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 python2.7 amd64 2.7.17-1~18.04ubuntu1.2
Err:8 http://archive.ubuntu.com/ubuntu bionic/main amd64 libpython-stdlib amd64 2.7.15~rc1-1
  Temporary failure resolving 'archive.ubuntu.com'
Err:9 http://archive.ubuntu.com/ubuntu bionic/main amd64 python amd64 2.7.15~rc1-1
  Temporary failure resolving 'archive.ubuntu.com'


```

[http://archive.ubuntu.com/](http://archive.ubuntu.com/)

Why is this archive empty? What am I missing!?

---

### Post by DuckHook on 2020-11-10
Welcome to the Forums, af-crm

There is no: ```
http://archive.ubuntu.com/ubuntu bionic/main
```&#8230;because the unsecured HTTP site for Canonical has been gone for quite some time. All Canonical sites are now TLS&#8209;secured (your URL is missing the trailing "s").

This is not the natural *sources.list* file that is part of any pristine initial install. It indicates that you've manually changed it. The PPA also indicates this. Launchpad PPAs also require HTTPS.

When using PPAs, you must appreciate that you are opening up a security risk. Unless you have absolute confidence in the PPA's author, you are basically allowing a stranger to access your computer.

BTW, it is not advisable to invoke the -y flag when installing an app in case of something unexpected requiring intervention midway.

---

### Post by deadflowr on 2020-11-10
The output is correct, Ubuntu repositories still use plain http since they also use gpg for the package signing keys for secure downloading.

The issue more likely stems from a broken dns, see this for a what to check and possibly fix, at least temporarily:
[https://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error]("https://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error")


Edit: while you're at it you might also look into switching mirrors.
It's hard o to believe you're best mirror option is the main archive.
This might help, though i'm not sure whether you're on a desktop or server version of Ubuntu:
[https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server]("https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server")
This is the desktop way, at least.

---

### Post by DuckHook on 2020-11-10
> **deadflowr said:**
> The output is correct…

My bad. I should check for accuracy before I post. Thanks for setting things straight, deadflowr.

---

### Post by ActionParsnip on 2020-11-11
Please mark as solved if the issue is resolved

---

