---
title: "Update Manager, Flash"
date: 2015-01-20
forum: Installation &amp; Upgrades
---

### Post by tomsubt on 2015-01-20
Hi,  I was running the update manager and I got this error message>>>"Failed to Download PKG Files" here are the details>>>

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.425ubuntu0.12.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.425ubuntu0.12.04.1_i386.deb) 404  Not Found [IP: 91.189.91.15 80]

It asked me to check my internet connection, but i am connected, but it acts like i am not!  any idea as to what is wrong here? Thanks.

---

### Post by ian-weisser on 2015-01-20
Apt is correct. 11.2.202.**425** is no longer in the repositories.

```
$ rmadison -u ubuntu flashplugin-installer | grep precise-security

 flashplugin-installer | 11.2.202.**429**ubuntu0.12.04.1 | precise-security/multiverse | amd64, i386

```

If you take a look at the publishing history at [https://launchpad.net/ubuntu/precise/i386/flashplugin-installer](https://launchpad.net/ubuntu/precise/i386/flashplugin-installer) ,
you can see that the package was updated earlier today.
Not the first time the repositories have been updated while software-updater was working.

Simply refresh your package lists and try again.

---

### Post by tomsubt on 2015-01-21
Ian: Thank You, got it.

---

