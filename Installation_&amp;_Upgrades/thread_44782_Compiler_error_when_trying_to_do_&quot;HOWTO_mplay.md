---
title: "Compiler error when trying to do &quot;HOWTO: mplayerplug-in 2.85 for Hoary&quot;"
date: 2005-06-27
forum: Installation &amp; Upgrades
---

### Post by Grunt on 2005-06-27
Hello everyone,

Recently I tried to the "HOWTO: mplayerplug-in 2.85 for Hoary" ([http://www.ubuntuforums.org/showthread.php?t=44560&highlight=mplayer)](http://www.ubuntuforums.org/showthread.php?t=44560&highlight=mplayer)). Until the following command everyhing works fine: 
```
tar -xvzf gecko-sdk-i686-pc-linux-gnu-1.7.8.tar.gz 
```

But when I try to configure it with the command:
```
./configure --with-gecko-sdk=../gecko-sdk
```

I get the following error:
```
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.
```

I've been searching the forum for a while, but I can't find the information I need to solve this problem. 

If anyone can help me, I would be very appreciative!

---

### Post by The Na Kun on 2005-06-27
sudo apt-get install build-essentials

---

### Post by Grunt on 2005-06-27
Hi, thanks for the reply!

I tried "sudo apt-get install build-essential" because "sudo apt-get install build-essential**s**" didn't work. Unfortunately now I get the following error:

```
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
Using new (v1.7+) gecko-sdk
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
configure: WARNING: *** Running in X mode - Limited Features ***
checking for gthread-2.0... Package gthread-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gthread-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gthread-2.0' found
configure: error: Missing gthread package
```

Does this mean I have to install the gthread package?

Edit: I saw this in one of the replies:

sudo apt-get install libgtk2.0-dev

Would that work? Or is the build-essentials sufficient?

---

### Post by Grunt on 2005-06-28
I'm going to bump this in case someone has an answer.

Thanks.

EDIT: I decided to triy that command and everything seems to be working now!

---

