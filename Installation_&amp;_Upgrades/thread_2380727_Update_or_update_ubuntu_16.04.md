---
title: "Update or update ubuntu 16.04"
date: 2017-12-21
forum: Installation &amp; Upgrades
---

### Post by Samrat Rao on 2017-12-21
Hi,

I've been given a 16.04 desktop. I have admin rights over it.

[LIST=1]
[*]I want to update (or upgrade?) the system and **not move to a newer version**. So which command should i issue: ```
sudo apt-get update
``` or ```
sudo apt-get upgrade
```?
[*]How do i check if the repositories are correctly configured? Any settings i have to make to avoid wrong packages from getting installed?
[*]I am having frequent power cuts, so i want to install a few packages at a time. Any recommended path for this, that is, any packages that first need to be installed or installation procedure that wont break the system due to interruptions.
[/LIST]

Thanks.

---

### Post by howefield on 2017-12-21
The first command will update the information your sources list has, making the system aware of what packages can be updated, the second will update those packages to the newer versions. Regular updating generally only takes a few minutes but your first one may some longer depending on when last the machine was updated. When you do the upgrade command you will be told how large the download will be and be given an option to proceed or cancel.

Perhaps it might be best to configure the machine not to auto update given your power issues in order that you can control when they are done.

Posting the output of the following command will allow others to tell you if your repositories look incorrect.

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by Samrat Rao on 2017-12-21
Hi,

Thanks for the quick reply. So ```
sudo apt-get upgrade
``` will not take me to a newer version of ubuntu.

As you suggested, I have configured the settings only to display messages when updates are available and not install them.

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

```
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial main restricted
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-updates main restricted
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-updates universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial multiverse
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-updates multiverse
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/xenial-dell.list:deb [http://dell.archive.canonical.com/updates/](http://dell.archive.canonical.com/updates/) xenial-dell public
/etc/apt/sources.list.d/xenial-dell.list:deb-src [http://dell.archive.canonical.com/updates/](http://dell.archive.canonical.com/updates/) xenial-dell public]
```

I'm getting this error with **sudo apt-get update**:

```
Ign:230 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial-backports/multiverse DEP-11 64x64 Icons
Err:174 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
  Connection failed [IP: 91.189.88.162 80]
Err:175 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main i386 Packages
  Connection failed [IP: 91.189.88.149 80]
Ign:176 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial/main Translation-en
Ign:177 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:178 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main DEP-11 64x64 Icons
Err:179 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial/restricted amd64 Packages
  Connection failed [IP: 91.189.88.161 80]
Err:180 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/restricted i386 Packages
  Connection failed [IP: 91.189.88.152 80]
Ign:181 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial/restricted Translation-en
Ign:182 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial/restricted amd64 DEP-11 Metadata
Err:183 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
  Connection failed [IP: 91.189.88.161 80]
Err:184 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial/universe i386 Packages
  server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
Err:193 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
  Connection failed [IP: 91.189.88.161 80]
Err:194 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages
  Connection failed [IP: 91.189.88.152 80]
Ign:195 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en
Ign:196 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata
Ign:197 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons
Err:198 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial-updates/restricted amd64 Packages
  Connection failed [IP: 91.189.88.149 80]
Err:199 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/restricted i386 Packages
  Connection failed [IP: 91.189.88.162 80]
Ign:200 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial-updates/restricted Translation-en
Ign:201 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/restricted amd64 DEP-11 Metadata
Err:202 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages
  Connection failed [IP: 91.189.88.149 80]
Err:203 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages
  Connection failed [IP: 91.189.88.162 80]
Err:212 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial-backports/main amd64 Packages
  Connection failed [IP: 91.189.88.162 80]
Err:213 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main i386 Packages
  Connection failed [IP: 91.189.88.149 80]
Ign:214 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial-backports/main Translation-en
Ign:215 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata
Ign:216 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main DEP-11 64x64 Icons
Err:217 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial-backports/restricted amd64 Packages
  Connection failed [IP: 91.189.88.161 80]
Err:218 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/restricted i386 Packages
  Connection failed [IP: 91.189.88.152 80]
Ign:219 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial-backports/restricted Translation-en
Ign:220 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/restricted amd64 DEP-11 Metadata
Err:221 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 Packages
  Connection failed [IP: 91.189.88.161 80]
Err:222 [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://archive.ubuntu.com/ubuntu) xenial-backports/universe i386 Packages
  Connection failed [IP: 91.189.88.152 80]
Reading package lists... Done                                  
W: The repository 'http://dl.google.com/linux/chrome/deb stable Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.canonical.com/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://security.ubuntu.com/ubuntu xenial-security Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://dell.archive.canonical.com/updates xenial-dell Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.ubuntu.com/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.ubuntu.com/ubuntu xenial-updates Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.ubuntu.com/ubuntu xenial-backports Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-amd64/Packages](http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-amd64/Packages)  Connection failed [IP: 216.58.197.46 80]
E: Failed to fetch [http://archive.canonical.com/ubuntu/dists/xenial/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/xenial/partner/binary-amd64/Packages)  Connection failed [IP: 91.189.92.191 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/xenial-security/main/binary-amd64/Packages)  server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
E: Failed to fetch [http://archive.canonical.com/ubuntu/dists/xenial/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/xenial/partner/binary-i386/Packages)  Connection failed [IP: 91.189.92.150 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/xenial-security/main/binary-i386/Packages)  Connection failed [IP: 91.189.91.23 80]
E: Failed to fetch [https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://dell.archive.canonical.com/updates/dists/xenial-dell/public/source/Sources](https://10.10.10.10:6082/php/uid.php?vsys=1&rule=0&url=http://dell.archive.canonical.com/updates/dists/xenial-dell/public/source/Sources)  Connection failed
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial/main/binary-amd64/Packages)  Connection failed [IP: 91.189.88.162 80]
E: Failed to fetch [http://dell.archive.canonical.com/updates/dists/xenial-dell/public/binary-amd64/Packages](http://dell.archive.canonical.com/updates/dists/xenial-dell/public/binary-amd64/Packages)  Connection failed
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial/main/binary-i386/Packages)  Connection failed [IP: 91.189.88.149 80]
E: Failed to fetch [http://dell.archive.canonical.com/updates/dists/xenial-dell/public/binary-i386/Packages](http://dell.archive.canonical.com/updates/dists/xenial-dell/public/binary-i386/Packages)  Connection failed
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/restricted/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/xenial-security/restricted/binary-amd64/Packages)  Connection failed [IP: 91.189.91.23 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/xenial-security/restricted/binary-i386/Packages)  Connection failed [IP: 91.189.88.162 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial/restricted/binary-amd64/Packages)  Connection failed [IP: 91.189.88.161 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial/restricted/binary-i386/Packages)  Connection failed [IP: 91.189.88.152 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/universe/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/xenial-security/universe/binary-amd64/Packages)  Connection failed [IP: 91.189.88.162 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/xenial-security/universe/binary-i386/Packages)  Connection failed [IP: 91.189.91.26 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial/universe/binary-amd64/Packages)  Connection failed [IP: 91.189.88.161 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial/universe/binary-i386/Packages)  server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/binary-amd64/Packages)  Connection failed [IP: 91.189.88.161 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/binary-i386/Packages)  Connection failed [IP: 91.189.88.152 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-updates/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/restricted/binary-amd64/Packages)  Connection failed [IP: 91.189.88.149 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/restricted/binary-i386/Packages)  Connection failed [IP: 91.189.88.162 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-updates/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/universe/binary-amd64/Packages)  Connection failed [IP: 91.189.88.149 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/universe/binary-i386/Packages)  Connection failed [IP: 91.189.88.162 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-backports/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial-backports/main/binary-amd64/Packages)  Connection failed [IP: 91.189.88.162 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-backports/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial-backports/main/binary-i386/Packages)  Connection failed [IP: 91.189.88.149 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-backports/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial-backports/restricted/binary-amd64/Packages)  Connection failed [IP: 91.189.88.161 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-backports/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial-backports/restricted/binary-i386/Packages)  Connection failed [IP: 91.189.88.152 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-backports/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial-backports/universe/binary-amd64/Packages)  Connection failed [IP: 91.189.88.161 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-backports/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/xenial-backports/universe/binary-i386/Packages)  Connection failed [IP: 91.189.88.152 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Is is fine to update?

---

### Post by Impavidus on 2017-12-21
**sudo apt-get update** refreshes the list of available packages, making your system aware of updates.
**sudo apt-get upgrade** downloads and installs the available upgrades, but will never install a new package or uninstall something.
**sudo apt-get dist-upgrade** downloads and installs all available upgrades, even when that means that some packages have to be removed or new packages have to be installed. You often need this for kernel upgrades.
**sudo apt upgrade** uses the somewhat higher-level apt instead of apt-get and downloads and installs all available upgrades, even when that means installing new packages, but will not remove any packages.You can use that for kernel upgrades too.

Finally, **sudo do-release-upgrade** is what will upgrade your entire system to a new release of Ubuntu.

The package manager can usually recover from interuptions without much difficulty. Whenever an interuption happened, try```
sudo apt install -f
```to finish the upgrade. Sometimes you may first need```
sudo dpkg --configure -a
```

---

### Post by Samrat Rao on 2017-12-23
Hi Impavidus,

Thanks for your explanations.

But i'm unable to download any packages since I am getting the error i listed in post #3. I'm from India and i tried using both Main Server and Server from India. Neither is working. I didn't set up a proxyserver for my browser so there may not be an issue with proxy settings.

---

