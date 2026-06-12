---
title: "Upgrade error: &quot;Check your connection&quot; message but my connection is ok."
date: 2022-10-25
forum: Installation &amp; Upgrades
---

### Post by antonio-cpr on 2022-10-25
Hi! 
I'm using Lubuntu but when I type "lsb_release -a" I get "Ubuntu 21.10".
A window opens everytime I start the system asking me to enter my password to upgrade the system. This window shows me the following command: "lubuntu-upgrader --full-upgrade".
When I enter the password I get the following error message:
```
download-error openjdk-18-jre-headless0/47344904 404  Not Found [IP: 2001:67c:1562::18 80]
download-error openjdk-18-jre
0/179836 404  Not Found [IP: 2001:67c:1562::18 80]
Error Resume:
Eror Code: error-package-download-failed
Failed to download package files
Check your Internet connection.
Error Detail: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-18/openjdk-18-jre-headless_18%7e15ea-4_amd64.deb 404  Not Found [IP: 2001:67c:1562::18 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-18/openjdk-18-jre_18%7e15ea-4_amd64.deb 404  Not Found [IP: 2001:67c:1562::18 80]


Failed to download package files
Check your Internet connection.
Eror Code: error-package-download-failed
Failed to download package files
Check your Internet connection.
Error Detail: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-18/openjdk-18-jre-headless_18%7e15ea-4_amd64.deb 404  Not Found [IP: 2001:67c:1562::18 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-18/openjdk-18-jre_18%7e15ea-4_amd64.deb 404  Not Found [IP: 2001:67c:1562::18 80]


Failed to download package files
Check your Internet connection.
```

My connection is ok. I tried a wired connection but I get the same error message.
My question is what is happening and how can I fix this error?

---

### Post by QIII on 2022-10-25
It appears that there is a malformed URL being used, which is why you are getting the "check connection" response.  That resource does not exist.

Have you tried

```
 sudo apt update
```

to update the apt database prior to attempting to upgrade your pacakages?

---

### Post by antonio-cpr on 2022-10-25
> **QIII said:**
> It appears that there is a malformed URL being used, which is why you are getting the "check connection" response.  That resource does not exist.

Have you tried

```
 sudo apt update
```

to update the apt database prior to attempting to upgrade your pacakages?

Here the output of your suggestion:
> antonio@antonio-notebook:~$ sudo apt update
[sudo] password for rob: 
Ign:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) impish InRelease
Ign:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security InRelease
Ign:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) impish-updates InRelease
Err:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security Release
  404  Not Found [IP: 2001:67c:1562::18 80]
Ign:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) impish-backports InRelease
Err:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) impish Release    
  404  Not Found [IP: 2001:67c:1562::15 80]
Err:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) impish-updates Release           
  404  Not Found [IP: 2001:67c:1562::15 80]
Err:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) impish-backports Release         
  404  Not Found [IP: 2001:67c:1562::15 80]
Get:9 [https://debian.neo4j.com](https://debian.neo4j.com) stable InRelease [44,1 kB]
Get:10 [https://debian.neo4j.com](https://debian.neo4j.com) stable/latest amd64 Packages [845 B]
Get:11 [https://debian.neo4j.com](https://debian.neo4j.com) stable/latest i386 Packages [845 B]
Reading package lists... Done
E: The repository 'http://security.ubuntu.com/ubuntu impish-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu impish Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu impish-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu impish-backports Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by QIII on 2022-10-25
Ah.  Something I didn't catch in your first post:  21.10.

Impish was an interim release that only enjoyed support for 9 months.  It is no longer in its period of standard support, which ended on July 24th.  It is now past what used to be known as End Of Life.

It is not at all surprising that you are getting "not found" errors because the files will have been moved to old-releases.

It can be difficult to update old releases, but it can be done.  I would recommend against it and suggest a clean installation of a supported LTS, such as 22.04 after backing up your important files.  However, should you wish to update and upgrade rather than reinstall, you may try the instructions [here]("https://help.ubuntu.com/community/EOLUpgrades").  Again, I really suggest against going the old-releases route.

---

### Post by antonio-cpr on 2022-10-26
> **QIII said:**
> Ah.  Something I didn't catch in your first post:  21.10.

Impish was an interim release that only enjoyed support for 9 months.  It is no longer in its period of standard support, which ended on July 24th.  It is now past what used to be known as End Of Life.

It is not at all surprising that you are getting "not found" errors because the files will have been moved to old-releases.

It can be difficult to update old releases, but it can be done.  I would recommend against it and suggest a clean installation of a supported LTS, such as 22.04 after backing up your important files.  However, should you wish to update and upgrade rather than reinstall, you may try the instructions [here]("https://help.ubuntu.com/community/EOLUpgrades").  Again, I really suggest against going the old-releases route.

I cannot do this right now, so could you please tell me how to disable this window to open every time I start the system?

---

