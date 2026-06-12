---
title: "Can't install Mono on Ubuntu Server"
date: 2010-02-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by RoliSoft on 2010-02-27
I'd like to serve ASP.Net files with nginx from Ubuntu Server 10.04 alpha 3, but I can't install mono.

```
rolisoft@ncc1701e:~$ sudo aptitude install mono
[...]
No candidate version found for mono
No candidate version found for mono
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
[...]
rolisoft@ncc1701e:~$ mono
The program 'mono' is currently not installed.  You can install it by typing:
sudo apt-get install mono-runtime
rolisoft@ncc1701e:~$ sudo aptitude install mono-runtime
[...]
The following packages are BROKEN:
  mono-runtime
The following NEW packages will be installed:
  binfmt-support{a}
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,314kB of archives. After unpacking 3,703kB will be used.
The following packages have unmet dependencies:
  mono-runtime: Depends: mono-gac (= 2.4.4~svn151842-1ubuntu1) but it is not installable
The following actions will resolve these dependencies:

Keep the following packages at their current version:
mono-runtime [Not Installed]

Score is -9881

Accept this solution? [Y/n/q/?] n

*** No more solutions available ***
[...]
```

How can I install mono under lucid lynx alpha 3?
If the mono package is currently broken, what workarounds can I do to install mono, like installing it from another (Debian/older Ubuntu) repository?

This is a development server, so it's not an issue if it'll be unstable.

---

### Post by slakkie on 2010-02-27
> **RoliSoft said:**
> 
How can I install mono under lucid lynx alpha 3?
If the mono package is currently broken, what workarounds can I do to install mono, like installing it from another (Debian/older Ubuntu) repository?

This is a development server, so it's not an issue if it'll be unstable.

You should be able to install mono from karmic.

Add karmic to your sources.list, and then do:

aptitude install mono/karmic as root.

---

### Post by RoliSoft on 2010-02-27
> **slakkie said:**
> You should be able to install mono from karmic.

Add karmic to your sources.list, and then do:

aptitude install mono/karmic as root.

I managed to install mono, but I still can't install the mono-fastcgi-server2 package, because aptitude wants to downgrade everything to install this package.

---

### Post by gnomeuser on 2010-02-27
Currently there is a dependency issue with mono-runtime. Give the developers a bit of time to push it through the build system

---

### Post by RoliSoft on 2010-02-27
I managed to install mono-fastcgi-server2 from Debian Squeeze's repository. It's probably very unstable, but it works.

```
deb http://ftp.debian.org/debian/ squeeze main contrib non-free
```

---

