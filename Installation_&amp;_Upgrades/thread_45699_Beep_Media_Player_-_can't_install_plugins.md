---
title: "Beep Media Player - can't install plugins"
date: 2005-07-01
forum: Installation &amp; Upgrades
---

### Post by mozz on 2005-07-01
I successfully installed the Beep Media Player, but when it comes to installing the plugins nothing works...

Here's what I did:

Extract the plugin archives, open a terminal, go to the extracted folder, type "make"
Terminal output:

> root@mozz1:/home/mozz/My Downloads/BeepMediaLibrary-0.12 # make
gcc -Wall -rdynamic -fPIC  `pkg-config gtk+-2.0 --cflags` `pkg-config bmp --cflags` -c command_queue.c
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package bmp was not found in the pkg-config search path.
Perhaps you should add the directory containing `bmp.pc'
to the PKG_CONFIG_PATH environment variable
No package 'bmp' found
/bin/sh: gcc: command not found
make: *** [command_queue.o] Error 127

Can someone explain to me what that means and how I can get the install done? 

thx a lot, mozz (2-day-ubuntu-newbie)

---

### Post by FLeiXiuS on 2005-07-01
Looks like your going to need some libs :-P.  

sudo apt-get install build-essential beep-media-player-dev

---

### Post by mozz on 2005-07-01
woow thx a lot!

If you're bored you could explain to me what I *actually did* with that build-essential thingy  :roll: 

if not, don't bother...I'll find it out myself ;)

---

