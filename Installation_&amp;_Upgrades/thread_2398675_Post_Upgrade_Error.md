---
title: "Post Upgrade Error"
date: 2018-08-15
forum: Installation &amp; Upgrades
---

### Post by btolman on 2018-08-15
Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh-cache > /dev/null; fi' E: Sub-process returned an error code

I could not find anything in the documentation or in google.  Any help is appreciated.

---

### Post by Impavidus on 2018-08-16
Could you tell us what command caused that error and the complete output of that command? Right now we've no way of knowing what's going on.

---

### Post by btolman on 2018-08-16
```

xxxxxxxx@xxxxxxx-desktop:~$ sudo apt-get update
[sudo] password for xxxxxxxxx: 
Hit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Get:3 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]    
Hit:4 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease  
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [138 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [31.4 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [53.7 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [152 kB]
Get:9 http://security.ubuntu.com/ubuntu bionic-security/universe Sources [14.2 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [153 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [262 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:13 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:14 http://security.ubuntu.com/ubuntu bionic-security/universe i386 Packages [50.7 kB]
Get:15 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [50.8 kB]
Get:16 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [5,768 B]
Get:17 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons [8,060 B]
Ign:18 http://dl.google.com/linux/chrome/deb stable InRelease                  
Get:19 http://dl.google.com/linux/chrome/deb stable Release [1,189 B]
Get:20 http://dl.google.com/linux/chrome/deb stable Release.gpg [819 B]
Get:21 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1,382 B]
Fetched 1,098 kB in 6s (197 kB/s)     
AppStream system cache was updated, but problems were found: Metadata files have errors: /var/cache/app-info/xmls/fwupd.xml
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh-cache > /dev/null; fi'
E: Sub-process returned an error code

```

And then after running upgrade...

```

xxxxxxxx@xxxxxxx-desktop:~$ sudo apt-get update
[sudo] password for xxxxxxxxx: 

Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:4 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
Hit:6 http://security.ubuntu.com/ubuntu bionic-security InRelease              
Hit:7 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease             
Hit:3 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease  
AppStream system cache was updated, but problems were found: Metadata files have errors: /var/cache/app-info/xmls/fwupd.xml
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh-cache > /dev/null; fi'
E: Sub-process returned an error code

```

---

### Post by Tony_Bennett on 2018-08-17
This link seems to be the same as your problem: [https://askubuntu.com/questions/1057515/error-when-updating-with-appstream](https://askubuntu.com/questions/1057515/error-when-updating-with-appstream)
It is classified as a duplicate of this:  [https://askubuntu.com/questions/943463/e-problem-executing-scripts-apt-updatepost-invoke-success-error-during-apt-ge](https://askubuntu.com/questions/943463/e-problem-executing-scripts-apt-updatepost-invoke-success-error-during-apt-ge)

I had the problem when I was on 16.04, but I upgraded to 18.04 two days ago and the problem went away.

Of course YMMV.

---

### Post by btolman on 2018-08-17
> **Tony_Bennett said:**
> This link seems to be the same as your problem: [https://askubuntu.com/questions/1057515/error-when-updating-with-appstream](https://askubuntu.com/questions/1057515/error-when-updating-with-appstream)
It is classified as a duplicate of this:  [https://askubuntu.com/questions/943463/e-problem-executing-scripts-apt-updatepost-invoke-success-error-during-apt-ge](https://askubuntu.com/questions/943463/e-problem-executing-scripts-apt-updatepost-invoke-success-error-during-apt-ge)

I had the problem when I was on 16.04, but I upgraded to 18.04 two days ago and the problem went away.

Of course YMMV.

Thank you.  I went to the original post, and tried all of the items.

```

sudo apt-get purge libappstream2
sudo rm /etc/apt/apt.conf.d/50appstream

``` 

The above fixed it for me.

---

