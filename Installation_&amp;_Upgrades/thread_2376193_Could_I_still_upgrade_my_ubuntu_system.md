---
title: "Could I still upgrade my ubuntu system?"
date: 2017-10-31
forum: Installation &amp; Upgrades
---

### Post by chowhao on 2017-10-31
It seems my ubuntu version is too old and the software source has lose maintaince.

```
Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found

apt-get update
  404  Not Found [IP: 91.189.88.162 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted Sources
  404  Not Found [IP: 91.189.88.162 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe Sources
  404  Not Found [IP: 91.189.88.162 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse Sources
  404  Not Found [IP: 91.189.88.162 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main amd64 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe amd64 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/main i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/restricted i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/universe i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) wily-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.162 80]
Reading package lists... Done
W: Failed to fetch [http://apt.wxwidgets.org/dists/wily-wx/InRelease](http://apt.wxwidgets.org/dists/wily-wx/InRelease)  

W: Failed to fetch [http://apt.wxwidgets.org/dists/wily-wx/Release.gpg](http://apt.wxwidgets.org/dists/wily-wx/Release.gpg)  Could not resolve 'apt.wxwidgets.org'

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily/main/source/Sources](http://cn.archive.ubuntu.com/ubuntu/dists/wily/main/source/Sources)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily/restricted/source/Sources](http://cn.archive.ubuntu.com/ubuntu/dists/wily/restricted/source/Sources)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily/universe/source/Sources](http://cn.archive.ubuntu.com/ubuntu/dists/wily/universe/source/Sources)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily/multiverse/source/Sources](http://cn.archive.ubuntu.com/ubuntu/dists/wily/multiverse/source/Sources)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily/main/binary-amd64/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily/restricted/binary-amd64/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily/restricted/binary-amd64/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily/universe/binary-amd64/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily/universe/binary-amd64/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily/multiverse/binary-amd64/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily/multiverse/binary-amd64/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily/main/binary-i386/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily/restricted/binary-i386/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily/restricted/binary-i386/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily/universe/binary-i386/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily/universe/binary-i386/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily/multiverse/binary-i386/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily/multiverse/binary-i386/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/main/source/Sources](http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/main/source/Sources)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/restricted/source/Sources](http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/restricted/source/Sources)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/universe/source/Sources](http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/universe/source/Sources)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/multiverse/source/Sources](http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/multiverse/source/Sources)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-amd64/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-amd64/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/restricted/binary-amd64/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/restricted/binary-amd64/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/universe/binary-amd64/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/universe/binary-amd64/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/multiverse/binary-amd64/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/multiverse/binary-amd64/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-i386/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/main/binary-i386/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/restricted/binary-i386/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/universe/binary-i386/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/universe/binary-i386/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/multiverse/binary-i386/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/wily-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/wily-security/main/source/Sources)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/main/source/Sources](http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/main/source/Sources)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/restricted/source/Sources](http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/restricted/source/Sources)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/universe/source/Sources](http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/universe/source/Sources)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/multiverse/source/Sources](http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/multiverse/source/Sources)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/main/binary-amd64/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/main/binary-amd64/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/wily-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/wily-security/restricted/source/Sources)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/restricted/binary-amd64/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/restricted/binary-amd64/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/universe/binary-amd64/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/universe/binary-amd64/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/multiverse/binary-amd64/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/multiverse/binary-amd64/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/main/binary-i386/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/main/binary-i386/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/restricted/binary-i386/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/universe/binary-i386/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/universe/binary-i386/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/multiverse/binary-i386/Packages](http://cn.archive.ubuntu.com/ubuntu/dists/wily-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 175.6.249.100 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/wily-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/wily-security/universe/source/Sources)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/wily-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/wily-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/wily-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/wily-security/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/wily-security/restricted/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/wily-security/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/wily-security/universe/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/wily-security/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/wily-security/multiverse/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/wily-security/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/wily-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/wily-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/wily-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/wily-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/wily-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/wily-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/wily-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/wily-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.162 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by westie457 on 2017-10-31
Hello chowhao, welcome to Ubuntu Forums.

Before you begin to upgrade please back up / copy your personal important files to somewhere safe.
Open 'Software & Updates', go to the 'Other Software' tab and uncheck all boxes except the one that has '**Canonical Partners**'.
Next go to the 'Updates' tab, at the bottom of this you should see 'Notify me of a new Ubuntu version' in the box next to this select 'Fir long-term support versions'.
Click on Close and follow the on-screen prompts.

---

### Post by ajgreeny on 2017-10-31
You will need to manually edit your software sources to the EOL repositories to make sure that wily is fully as updated as possible then you can, or should be able to, upgrade to 16.04.

I have never upgraded my OS this way, always dong a clean install to get a clean start with the new OS so I can't give you any personal experience to help you, but if it does not work you can start again with a clean install; just make absolutely certain you have backups of everything you need before doing either.

---

### Post by Topsiho on 2017-10-31
I would do as ajgreeny suggests: doing a clean install of Ubuntu 16.04.3, and as westie457 suggests: first back up all your personal files which you would hate to lose, to somewhere safe.
Even if you have a slow internet connection, this is preferable over doing a full upgrade, from 15.10 to 16.04, as during such an upgrade much more data may have to be downloaded.
Success,
Topsiho

---

### Post by chowhao on 2017-10-31
Thanks for help.There are many software installed on my system.Most of them are through apt-get.Is there convenient way to back-up these "apt-get" software?Or just back-up the software's names and install them through apt-get on upgraded system again.If I do not want install them one by one,dpkg would help me?  
What's more,there are some software were installed through configure&make install,could I do something to let it installed through dpkg?

---

### Post by SeijiSensei on 2017-10-31
Look at the --get-selections and --set-selections [options to dkpg]("http://manpages.ubuntu.com/manpages/xenial/man1/dpkg.1.html").  You can create a list of installed software with --get-selections and feed it into dpkg on the new installation.

Most software compiled from source installs into /usr/local/ or /opt/.  Back up these directories before continuing and transfer their contents to the new installation.

---

### Post by deadflowr on 2017-10-31
> What's more,there are some software were installed through configure&make install,could I do something to let it installed through dpkg?
Yes.
Before you install the software you would use the package checkinstall instead of make install.
checkinstall will create a deb package of the software and then auto install the package from that.
[https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")

---

### Post by chowhao on 2017-12-02
Could I upgrade my system in this way:Firstly install the newer system in a partition of my portable disk.And copy all the file of the new system and override the file of old system.Then update the grub.
As a result,I could keep all my installed software.

---

