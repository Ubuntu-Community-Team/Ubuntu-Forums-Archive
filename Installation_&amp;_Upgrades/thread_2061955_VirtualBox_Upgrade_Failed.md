---
title: "VirtualBox Upgrade Failed"
date: 2012-09-23
forum: Installation &amp; Upgrades
---

### Post by Ubun2to on 2012-09-23
I just downloaded the latest version of VirtualBox, and GDebi and the Software Center said that it could not open it because the package was corrupt or broken.
So, I checked the checksums, and they were off, so I redownloaded it.
Now, the Software Center says this:
```
Breaks existing package 'virtualbox-4.1' that conflict: 'virtualbox'. But the '/home/davidlucadou/Downloads/virtualbox-4.2_4.2.0-80737~Ubuntu~precise_amd64.deb' provides it via: 'virtualbox'
```
GDebi gives me the same error.
The Update Manager (retrieving packages from the official PPA) can't install it, either. This is the error I get:
```
davidlucadou@HP-DESKTOP:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  virtualbox-4.1
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 70.1 MB of archives.
After this operation, 420 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://download.virtualbox.org/virtualbox/debian/ precise/contrib virtualbox-4.1 amd64 4.1.22-80657~Ubuntu~precise [70.1 MB]
Fetched 70.1 MB in 3min 25s (342 kB/s)                                                                                               
Preconfiguring packages ...
(Reading database ... 423112 files and directories currently installed.)
Preparing to replace virtualbox-4.1 4.1.18-78361~Ubuntu~precise (using .../virtualbox-4.1_4.1.22-80657~Ubuntu~precise_amd64.deb) ...
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/virtualbox-4.1_4.1.22-80657~Ubuntu~precise_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Processing triggers for python-central ...
Errors were encountered while processing:
 /var/cache/apt/archives/virtualbox-4.1_4.1.22-80657~Ubuntu~precise_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
It asked me to close the VBoxSVC daemon, but it did not show up on the System Monitor, so it should have been closed.
Why is this?

---

### Post by zvacet on 2012-09-25
Try with 

```
sudo dpkg --configure -a
```

---

### Post by perlinpinpin on 2013-01-09
Any news on that one?

I have the exact same problem on Ubuntu 12.04 LTS (using the .deb package from virtualbox website):

Breaks existing package 'virtualbox-4.1' that conflict: 'virtualbox'. But the '/***/Downloads/virtualbox-4.2_4.2.6-82870~Ubuntu~oneiric_i386.deb' provides it via: 'virtualbox'

("sudo apt-get upgrade" says everything is up to date - but this is unrelated)

Thanks.

---

### Post by efflandt on 2013-01-10
Try removing virtualbox 4.1 first.  I run 64-bit Ubuntu 12.04, but never did have virtualbox 4.1 because I first got into virtualbox when the current version was already 4.2.4 I think.

So I originally followed the instructions on the virtualbox website for "**Debian-based Linux distributions**" to enable the repository for it when installing with apt-get, and it recently updated to 4.2.6 automatically.

If you install a manually download a virtualbox deb file it will not update automatically if you did not add the proper repository and key.

PS: Now that I reread the original post, maybe you need to temporarily comment out the virtualbox specific respository in sources.list to purge the old Ubuntu virtualbox.

---

### Post by nestoribili on 2013-12-12
look no more; the solution is here:
[http://ubuntuhandbook.org/index.php/2013/11/virtualbox-4-3-2-released-upgrade-ubuntu-linux-mint/](http://ubuntuhandbook.org/index.php/2013/11/virtualbox-4-3-2-released-upgrade-ubuntu-linux-mint/)
nb

---

### Post by sky-salim on 2014-04-29
yo tengo el mismo problema, y al intentar repararlo aparece el siguiente error

problemas de dependencias impiden la configuración de virtualbox-qt:
 virtualbox-qt depende de virtualbox (= 4.1.12-dfsg-2ubuntu0.6); sin embargo:
  La versión de `virtualbox' en el sistema es 4.1.12-dfsg-2ubuntu0.5.


esto paso justo coando se actualizo la version de virtualbox y no encuentro manera de repararlo

---

### Post by sky-salim on 2014-04-29
adicionalmente me manda este mensaje cuando trato de reinstalar

El paquete virtualbox necesita ser reinstalado, pero no se encuentra un archivo para éste.

---

