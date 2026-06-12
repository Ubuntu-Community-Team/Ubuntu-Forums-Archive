---
title: "Cannot install intel drivers"
date: 2013-03-15
forum: Installation &amp; Upgrades
---

### Post by jackson070901 on 2013-03-15
I can't install intel gma 965 drivers

[https://01.org/linuxgraphics/](https://01.org/linuxgraphics/)

due to what i'm assuming is a broken package

due to this error

Error running transaction: GDBus.Error:org.debian.apt.TransactionFailed: error-cache-broken: The following packages have unmet dependencies:

libgl1-mesa-dri: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
libgl1-mesa-dri:i386: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed


using xubuntu 12.04 LTS

---

### Post by jackson070901 on 2013-03-15
i'm getting somewhere but now i have a

The package system is broken

---

### Post by jackson070901 on 2013-03-15
now i can't use apt-get at all :.(

---

### Post by jackson070901 on 2013-03-15
Preparing to replace libgl1-mesa-dri 8.0.4-0ubuntu0.4 (using .../libgl1-mesa-dri_9.0.1-0ubuntu1~precise7.3_amd64.deb) ...
Unpacking replacement libgl1-mesa-dri ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-dri_9.0.1-0ubuntu1~precise7.3_amd64.deb (--unpack):
 './usr/share/doc/libgl1-mesa-dri/changelog.Debian.gz' is different from the same file on the system
dpkg-deb (subprocess): subprocess data was killed by signal (Broken pipe)
dpkg-deb: error: subprocess <decompress> returned error exit status 2
Unpacking libllvm3.1:i386 (from .../libllvm3.1_3.1-2ubuntu1~precise6.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libllvm3.1_3.1-2ubuntu1~precise6.2_i386.deb (--unpack):
 './usr/share/doc/libllvm3.1/changelog.Debian.gz' is different from the same file on the system
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa-dri_9.0.1-0ubuntu1~precise7.3_amd64.deb
 /var/cache/apt/archives/libllvm3.1_3.1-2ubuntu1~precise6.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by MAFoElffen on 2013-03-15
Just what did you "try" to install by what method?

I would have thought that the method that would have easiest was to--
```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update
sudo apt-get install i965-va-driver

```
But instead now... you need to uninstall that driver and clean up to get back clean.

So what did you do?

---

### Post by gifford on 2013-03-16
There is a problem with installation on AMD 64, it is a bug.
This link explains the issue. [http://www.webupd8.org/2013/03/intel-releases-linux-graphics-drivers.html#more](http://www.webupd8.org/2013/03/intel-releases-linux-graphics-drivers.html#more)

---

### Post by MAFoElffen on 2013-03-16
I see. That wasn't good at all.

From that article and what the OP said happened to him... Looks like he needs to boot off the same version, same architecture LiveCD and copy over the sources list from it- over the one on his system. (the article said it added new repo's) That would get his apt-sources straighten out. Then he could uninstall and clean the cache.

---

### Post by Minarion on 2013-03-16
[COLOR=#696969]Hi guys.[/COLOR]

I'm running an Ubuntu 12.10 64-bit install and too have run the tool. It exits with a popup saying *libdrm-radeon1:386 cannot be removed*. This happens in the step "installing packages".

I've now uninstalled the *intel-linux-graphics-installer* using the software centre. 

What can I do to get my Intel HD 3000 functioning properly again, until 13.04 is released? (games used to crash after the installation, yet strangely enough, not anymore). 

Is 13.04 beta a viable option? Does anyone know, how smooth the transition from the beta to 13.04 is? 

[COLOR=#696969]Thanks in advance[/COLOR]

---

