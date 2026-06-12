---
title: "Upgrade from 18.04 to 20.04 without affecting installed software"
date: 2021-02-24
forum: Installation &amp; Upgrades
---

### Post by petarkozic on 2021-02-24
Hi folks,

does exists some way on how I can upgrade ubuntu 18.04 to 20.04 without affecting my repos and software like:

Mysql server
PHP

On example I have installed Mysql 5.7 and PHP 7.4

If I run dist-upgrade my MySQL server stop working because upgraded to MySQL 8 and upgrade process upgrade PHP to 8.
Of course I tried to change code name in my repository from bionic to focal but without success.

I tried to find some solution but I didn't found.

Thank you in advance.

---

### Post by schragge on 2021-02-24
Focal has [php7.4]("https://packages.ubuntu.com/focal/php7.4"). If the version from the official repo doesn't work for you, see [https://deb.sury.org](https://deb.sury.org)

As to MySQL 5.7, see [How to install MySQL 5.7 on Ubuntu 20.04 LTS]("https://www.fosstechnix.com/how-to-install-mysql-5-7-on-ubuntu-20-04-lts")

---

### Post by grahammechanical on 2021-02-24
This is what the manual page for apt-get says about dis-upgrade

> **dist-upgrade**
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. The dist-upgrade command may therefore remove some packages. 

The dis-upgrade command does not upgrade one version of Ubuntu to a newer version.

This is the official method to upgrade from 18.04 to 20.04

[https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today](https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today)

If this is a server install then you should read the section called: Upgrade to 20.04 LTS - on the command line. You should expect software to be upgraded to newer versions. The release notes list the changes.

[https://wiki.ubuntu.com/FocalFossa/ReleaseNotes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes)

Regards

---

### Post by SeijiSensei on 2021-02-24
You can tell apt not to upgrade a package with the command
```
sudo apt-mark hold packagename
```

I don't know how this applies to upgrading to an entirely new release using dist-upgrade.

See the man page for apt-mark: [http://manpages.ubuntu.com/manpages/bionic/man8/apt-mark.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/apt-mark.8.html)

---

### Post by petarkozic on 2021-02-25
Thank you to all on answer.

I already check all that document, but unfortunatelly that don't solve my problem. I have about 40 server and I don't want to upgrade MySQL on each one.

Thanks !

---

### Post by Impavidus on 2021-02-25
You can continue using 18.04 for 2 more years, but you can't continue using old software forever.

---

### Post by SeijiSensei on 2021-02-27
I suggest you install VirtualBox, then install a copy of 20.04 into a virtual machine. Migrate a copy of your database using mysqldump and copy over a website that uses PHP. Do they still work the same way? I'm going to guess the answer is yes.

---

