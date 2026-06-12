---
title: "Installing ClamAV-0.97.6, ncurses not found warning"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by Ruslan Sharipov on 2013-02-16
I need to install the latest version of ClamAV antivirus from the source to Ubuntu 11.04. I have downloaded the file [COLOR=Green]clamav-0.97.6.tar.gz[/COLOR] and unpacked into the folder [COLOR=Green]/tmp/clamav-0.97.6[/COLOR]. Then I have started terminal and typed the following commands: [SIZE=4]
[/SIZE]
[COLOR=Blue]cd /
cd tmp
cd clamav-0.97.6
[/COLOR]
Then, according to the instractions in [COLOR=Green]/tmp/clamav-0.97.6/INSTALL[/COLOR], I typed

[COLOR=Blue]./configure[/COLOR]

Having executed this command, I got the following message:

[COLOR=Red]WARNING: ****** not building clamdtop: ncurses not found[/COLOR]

The matter is that [COLOR=Green]ncurses[/COLOR] package is installed on my machine. Its library files are 

[COLOR=Green]/lib/ncurses.so.5.7
/lib/ncursesw.so.5.7

[/COLOR]Therefore I tried

[COLOR=Blue]./configure --with-libncurses-prefix=/lib[/COLOR]
[COLOR=Blue]./configure --with-libncurses-prefix=/
[/COLOR][COLOR=Blue]./configure --with-libncurses-prefix=null
[/COLOR][COLOR=Blue]./configure --with-libncurses-prefix[/COLOR]

But the WARNING message is still persisting. Please, help me to avoid it.

---

### Post by Ruslan Sharipov on 2013-02-16
So, I have solved the problem, though it is not a good solution. Since it does not see the installed [COLOR=Green]ncurses [/COLOR]package, I was to install a new one. For this purpose I have downloaded the archive file [COLOR=Green]ncurses-5.9.tar.gz[/COLOR] and unpacked it to the folder [COLOR=Green]/tmp/ncurses-5.9[/COLOR]. This is a new version 5.9 different from the version 5.7 already installed on my machine. Then I typed the following commands in the terminal window: 

[COLOR=Blue]cd /
cd tmp
cd [/COLOR][COLOR=Blue]ncurses-5.9

[/COLOR]Then, according to the instructions in [COLOR=Green]/tmp/[/COLOR][COLOR=Green]ncurses-5.9[/COLOR][COLOR=Green]/INSTALL[/COLOR], I typed

[COLOR=Blue]./configure --prefix=/usr/local[/COLOR]

The prefix [COLOR=Blue]/usr/local [COLOR=Black]is very important[/COLOR][/COLOR]. It instructs to install the [COLOR=Green][COLOR=Black]package[/COLOR][/COLOR] [COLOR=Green]ncurses-5.9[/COLOR] locally without overriding the existing system package [COLOR=Green]ncurses-5.7[/COLOR], which is installed to the root of the file system [COLOR=Blue]/ [COLOR=Black].[/COLOR][/COLOR] The next step is to type the command 

[COLOR=Blue]make[/COLOR]

Then, according to the instructions in [COLOR=Green]/tmp/[/COLOR][COLOR=Green]ncurses-5.9[/COLOR][COLOR=Green]/INSTALL[/COLOR], I run various tests. For this purpose I had to set the environment variable TERMINFO by means of the command

[COLOR=Blue]export TERMINFO=/lib/terminfo[/COLOR]

Then I typed

[COLOR=Blue]cd test[/COLOR]

and started to run tests. They are invoked by the commands

[COLOR=Blue]./firework
./ncurses
./hanoi
[/COLOR]
etc. The next step was to type

[COLOR=Blue]cd ..
make install
[/COLOR]
As a result I got two versions of the [COLOR=Green]ncurses[/COLOR] package installed on my machine. Now I can reset the environment variable TERMINFO to a new value 
[COLOR=Blue]
[/COLOR][COLOR=Blue]export TERMINFO=/usr/local/lib/terminfo[/COLOR]

and run tests again. They appeared to be OK with the new version of the [COLOR=Green]ncurses[/COLOR] package. Then I returned to installing ClamAV

[COLOR=Blue]cd /tmp[/COLOR]
[COLOR=Blue]cd clamav-0.97.6[/COLOR]

Typing 

[COLOR=Blue]./configure[/COLOR]

in this case I did not see the WARNING message. It's a solution. But it is not a good solution. For this reason I ask experts how to avoid the WARNING message without installing [COLOR=Green]ncurses[/COLOR] locally. Please, help me.

---

### Post by steeldriver on 2013-02-16
You probably should just have installed the corresponding -dev package for your currently installed ncurses version

```
$ apt-cache show **libncurses5[COLOR=Red]-dev[/COLOR]**
Package: libncurses5-dev
Priority: optional
Section: libdevel
Installed-Size: 1024
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Craig Small <csmall@debian.org>
Architecture: i386
Source: ncurses
Version: 5.9-4
Replaces: libncurses-dev, ncurses-dev
Provides: libncurses-dev, ncurses-dev
Depends: libncurses5 (= 5.9-4), libtinfo-dev (= 5.9-4), ncurses-bin (= 5.9-4), libc-dev
.
.
.
Description-en: developer's libraries for ncurses
 The ncurses library routines are a terminal-independent method of
 updating character screens with reasonable optimization.
 .
 This package contains the header files, static libraries
 and symbolic links that developers using ncurses will need.
.
.
.
```

---

### Post by schragge on 2013-02-16
And *libncursesw5-dev*, too.

---

