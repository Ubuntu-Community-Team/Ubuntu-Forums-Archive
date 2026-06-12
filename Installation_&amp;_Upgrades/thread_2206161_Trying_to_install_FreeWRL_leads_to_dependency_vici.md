---
title: "Trying to install FreeWRL leads to dependency vicious circle"
date: 2014-02-17
forum: Installation &amp; Upgrades
---

### Post by desconocido on 2014-02-17
Not sure whether this would be better in "General Support" - please comment if you think so.

I have a new computer which has the amd64 version of Ubuntu 12.04.3 installed. (Also has unity and unity2d removed and gnome-shell installed - I use Gnome Classic.)

I am trying to install FreeWRL ([http://freewrl.sourceforge.net/index.html](http://freewrl.sourceforge.net/index.html)).
So I downloaded the latest:
freewrl_1.22.13-1_amd64.deb
and tried to open it with Ubuntu Software Center. Installing gave the error "Dependency could not be satisfied - libfontconfig1 (>= 2.9.0)"

I then tried it with dpkg

```
$ sudo dpkg -i freewrl_1.22.13-1_amd64.deb 
[sudo] password for : 
Selecting previously unselected package freewrl.
(Reading database ... 191413 files and directories currently installed.)
Unpacking freewrl (from freewrl_1.22.13-1_amd64.deb) ...
dpkg: dependency problems prevent configuration of freewrl:
 freewrl depends on default-jre | java-runtime; however:
  Package default-jre is not installed.
  Package java-runtime is not installed.
 freewrl depends on libfontconfig1 (>= 2.9.0); however:
  Version of libfontconfig1 on system is 2.8.0-3ubuntu9.1.
 freewrl depends on libglew1.7 (>= 1.7.0); however:
  Package libglew1.7 is not installed.
 freewrl depends on libimlib2; however:
  Package libimlib2 is not installed.
 freewrl depends on libmotif4; however:
  Package libmotif4 is not installed.
 freewrl depends on libmozjs10d; however:
  Package libmozjs10d is not installed.
 freewrl depends on libnspr4-0d (>= 1.8.0.10); however:
  Package libnspr4-0d is not installed.
dpkg: error processing freewrl (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 freewrl

```

So I downloaded  libfontconfig1_2.9.0-7.1_amd64.deb from debian:
```
sudo gdebi libfontconfig1_2.9.0-7.1_amd64.deb
[sudo] password for bob: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Building data structures... Done 
This package is uninstallable
Dependency is not satisfiable: fontconfig-config (= 2.9.0-7.1)

```
So I downloaded fontconfig-config_2.9.0-7.1_all.deb from debian:
```
 sudo gdebi fontconfig-config_2.9.0-7.1_all.deb 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Building data structures... Done 
This package is uninstallable
Breaks existing package 'libfontconfig1' dependency fontconfig-config (= 2.8.0-3ubuntu9.1)

```

So I tried a trick I learnt from [http://forums.codeblocks.org/index.php?PHPSESSID=vdcae2kd3o9fdncos9ru9i4ke2&/topic,17945.0.html](http://forums.codeblocks.org/index.php?PHPSESSID=vdcae2kd3o9fdncos9ru9i4ke2&/topic,17945.0.html) and created a folder with both .deb files:
```
$ sudo dpkg -i *.deb
(Reading database ... 191440 files and directories currently installed.)
Preparing to replace fontconfig-config 2.8.0-3ubuntu9.1 (using fontconfig-config_2.9.0-7.1_all.deb) ...
Unpacking replacement fontconfig-config ...
Preparing to replace libfontconfig1 2.8.0-3ubuntu9.1 (using libfontconfig1_2.9.0-7.1_amd64.deb) ...
De-configuring libfontconfig1:i386 ...
Unpacking replacement libfontconfig1 ...
Setting up fontconfig-config (2.9.0-7.1) ...
Installing new version of config file /etc/fonts/conf.avail/65-nonlatin.conf ...
Installing new version of config file /etc/fonts/conf.avail/60-latin.conf ...
Installing new version of config file /etc/fonts/conf.avail/45-latin.conf ...
Installing new version of config file /etc/fonts/conf.avail/40-nonlatin.conf ...
Installing new version of config file /etc/fonts/conf.avail/30-urw-aliases.conf ...
Installing new version of config file /etc/fonts/conf.avail/30-metric-aliases.conf ...
Installing new version of config file /etc/fonts/fonts.dtd ...
dpkg: error processing libfontconfig1 (--install):
 libfontconfig1:amd64 2.9.0-7.1 cannot be configured because libfontconfig1:i386 is in a different version (2.8.0-3ubuntu9.1)
dpkg: error processing libfontconfig1:i386 (--install):
 libfontconfig1:i386 2.8.0-3ubuntu9.1 cannot be configured because libfontconfig1:amd64 is in a different version (2.9.0-7.1)
Processing triggers for man-db ...
Errors were encountered while processing:
 libfontconfig1
 libfontconfig1:i386

```

At this point I don't know what to do next and don't understand why libfontconfig1:i386 is there.

Help.

---

### Post by ian-weisser on 2014-02-17
Trying to install new versions of software on an older system like 12.04 often leads to dependency problems like this.
Perhaps you wish to try an older version of the freewrl package?
An older package may be happy with your older 12.04.3 libfontconfig version.

Another, more drastic option is to upgrade your version of Ubuntu, which will also upgrade libfontconfig. If you are installing new versions of software on your system, you're rather outside the envelope of intended LTS use (stability without changes).

Don't forget to tell this problem to the developer or packager of your problem. Since this package is not in the Ubuntu Repositories, this forum doesn't support it. The developer or packager supports it.
Of course, we'll try anyway.

And if their software is stable, remind them to jump through the final hoop and submit their software to the Debian archive. Then Ubuntu will pick it up automatically and we will support it here.

---

### Post by desconocido on 2014-02-18
> **ian-weisser said:**
> Trying to install new versions of software on an older system like 12.04 often leads to dependency problems like this.
Perhaps you wish to try an older version of the freewrl package?
An older package may be happy with your older 12.04.3 libfontconfig version.

Thanks for these comments. There were a couple of older versions available. I don't know if these look more promising:

```
~/Downloads/freewrl$ ls -al
total 1972
drwxrwxr-x 2 bob bob   4096 Feb  8 21:43 .
drwxr-xr-x 5 bob bob   4096 Feb 11 19:07 ..
-rw-rw-r-- 1 bob bob 659596 Jan 25 05:23 freewrl_1.22.10-1_amd64.deb
-rw-rw-r-- 1 bob bob 669978 Jan 25 05:26 freewrl_1.22.12-pre1_amd64.deb
-rw-rw-r-- 1 bob bob 673462 Jan 25 05:17 freewrl_1.22.13-1_amd64.deb
```
```
bob@Otilia:~/Downloads/freewrl$ sudo dpkg -i freewrl_1.22.10-1_amd64.deb 
[sudo] password for bob: 
Selecting previously unselected package freewrl.
(Reading database ... 195986 files and directories currently installed.)
Unpacking freewrl (from freewrl_1.22.10-1_amd64.deb) ...
dpkg: dependency problems prevent configuration of freewrl:
 freewrl depends on libglew1.5 (>= 1.5.4); however:
  Package libglew1.5 is not installed.
 freewrl depends on libimlib2; however:
  Package libimlib2 is not installed.
 freewrl depends on libmotif4; however:
  Package libmotif4 is not installed.
 freewrl depends on libmozjs2d (>= 1.9.1); however:
  Package libmozjs2d is not installed.
 freewrl depends on libnspr4-0d (>= 1.8.0.10); however:
  Package libnspr4-0d is not installed.
dpkg: error processing freewrl (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 freewrl
```
```
bob@Otilia:~/Downloads/freewrl$ sudo dpkg -i freewrl_1.22.12-pre1_amd64.deb 
(Reading database ... 196013 files and directories currently installed.)
Preparing to replace freewrl 1.22.10-1 (using freewrl_1.22.12-pre1_amd64.deb) ...
Unpacking replacement freewrl ...
dpkg: dependency problems prevent configuration of freewrl:
 freewrl depends on libglew1.5 (>= 1.5.8); however:
  Package libglew1.5 is not installed.
 freewrl depends on libimlib2; however:
  Package libimlib2 is not installed.
 freewrl depends on libmotif4; however:
  Package libmotif4 is not installed.
 freewrl depends on libmozjs2d (>= 1.9.1); however:
  Package libmozjs2d is not installed.
 freewrl depends on libnspr4-0d (>= 1.8.0.10); however:
  Package libnspr4-0d is not installed.
dpkg: error processing freewrl (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 freewrl

```
> Another, more drastic option is to upgrade your version of Ubuntu, which will also upgrade libfontconfig. If you are installing new versions of software on your system, you're rather outside the envelope of intended LTS use (stability without changes).
Yes, I'm thinking of looking at 14.04 LTS when it comes out.

> Don't forget to tell this problem to the developer or packager of your problem. Since this package is not in the Ubuntu Repositories, this forum doesn't support it. The developer or packager supports it.
Of course, we'll try anyway.

And if their software is stable, remind them to jump through the final hoop and submit their software to the Debian archive. Then Ubuntu will pick it up automatically and we will support it here.

I'll do that too.

---

### Post by ian-weisser on 2014-02-18
It looks to me like the Squeeze package should offer the least problems...

> **desconocido said:**
> 
```

[...]
-rw-rw-r-- 1 bob bob 659596 Jan 25 05:23 freewrl_1.22.10-1_amd64.deb
[...]
dpkg: dependency problems prevent configuration of freewrl:
 **freewrl depends on libglew1.5 (>= 1.5.4)**; however:
  Package libglew1.5 is not installed.
 **freewrl depends on libimlib2**; however:
  Package libimlib2 is not installed.
 **freewrl depends on libmotif4**; however:
  Package libmotif4 is not installed.
 [COLOR=#ff8c00]**freewrl depends on libmozjs2d (>= 1.9.1)**[/COLOR]; however:
  Package libmozjs2d is not installed.
 **freewrl depends on libnspr4-0d (>= 1.8.0.10)**; however:
  Package libnspr4-0d is not installed.

```

Four of the five packages are in the Ubuntu Repositories. One is in Debian's Squeeze archive.

```
$ rmadison -u ubuntu libglew1.5
 libglew1.5 | 1.5.7.is.1.5.2-1ubuntu4 | precise        | amd64, armel, armhf, i386, powerpc

$ rmadison -u ubuntu libimlib2
 libimlib2 | 1.4.4-1build1  | precise | amd64, armel, armhf, i386, powerpc

$ rmadison -u ubuntu libmotif4
 libmotif4 | 2.3.3-5ubuntu1         | precise/multiverse         | amd64, armel, armhf, i386, powerpc
 libmotif4 | 2.3.3-5ubuntu1.12.04.2 | precise-updates/multiverse | amd64, armel, armhf, i386, powerpc

$ rmadison -u ubuntu libmozjs2d
[not found]
$ rmadison -u [COLOR=#ff8c00]**debian**[/COLOR] libmozjs2d
 libmozjs2d | 1.9.1.16-20 | squeeze-security | amd64, armel, i386, ia64, kfreebsd-amd64, kfreebsd-i386, mips, mipsel, powerpc, s390, sparc
 libmozjs2d | 1.9.1.16-20 | squeeze          | amd64, armel, i386, ia64, kfreebsd-amd64, kfreebsd-i386, mips, mipsel, powerpc, s390, sparc

$ rmadison -u ubuntu libnspr4-0d
 libnspr4-0d | 4.8.9-1ubuntu2         | precise/universe          | amd64, armel, armhf, i386, powerpc
```

Try installing the Ubuntu dependencies and Debian dependencies before installing the freewrl package. I sure you already know that dpkg -i merely installs the specified package, it doesn't automatically install dependencies.
```
sudo apt-get install libglew1.5 limilib2 libmotif4 libnspr4-0d
sudo dpkg -i /path/to/libmozjs2d.deb
sudo dpkg -i /path/to/freewrl_1.22.10-1_amd64.deb
```

---

### Post by desconocido on 2014-02-18
> **ian-weisser said:**
> It looks to me like the Squeeze package should offer the least problems...


Thanks, it installed, even on my damaged system:
```
sudo apt-get install libglew1.5 libimlib2 libmotif4 libnspr4-0d
sudo dpkg -i libmozjs2d_1.9.1.16-20_amd64.deb 
sudo dpkg -i freewrl_1.22.10-1_amd64.deb 

```

Mind you, it crashed, but I wonder if that is because libfontconfig1 is in a mess. If so, it might pay me to re-install Ubuntu again.
```
$ /usr/bin/freewrl
FreeWRL: initializing...
copying application supplied params...
request sent to parser thread, main thread joining display thread...
glX: direct rendering enabled
create_main_window: top widget realized: TRUE
opengl version=4.3.12682 Compatibility Profile Context 13.30
GLEW initialization: version 1.5.2
Shader support:       TRUE
Multitexture support: TRUE
Occlusion support:    TRUE
Max texture size      16384
Texture units         8
FreeWRL: running as a plugin: FALSE
xfont not initialized !!! initializing with defaults (fixed white)
freewrl: fcmatch.c:548: IA__FcFontMatch: Assertion `result != ((void *)0)' failed.
Aborted (core dumped)

```

---

