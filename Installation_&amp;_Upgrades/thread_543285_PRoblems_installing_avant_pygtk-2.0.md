---
title: "PRoblems installing avant pygtk-2.0"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by restwix on 2007-09-04
Hi I'm having some problems installing Avant, and I was wondering if someone could help me out. I've tried a lot of things to get this fixed but I couldn't get this one.

Here is my problem whenever I run autogen.sh

checking pkg-config is at least version 0.9.0... yes
checking for PYGTK... configure: error: Package requirements (pygtk-2.0 >= 2.8.0) were not met:

No package 'pygtk-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGTK_CFLAGS
and PYGTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I would appreciate it

Thanks in advance.

=)

---

### Post by restwix on 2007-09-05
I found something on this website [http://mail.codepoet.no/archives/revelation-list/2006-August.txt.gz]("http://mail.codepoet.no/archives/revelation-list/2006-August.txt.gz")
and apparently It  fixed that issue:
what you have to do is:

"
> It might be worth mentioning in Revelation's INSTALL or README file that autogen.sh must be run
> first (not all users will be familiar with the automake approach).

That way, you can just:

$ sudo apt-get build-dep revelation
$ sudo apt-get -b source revelation
$ sudo dpkg -i revelation*deb

"

But I'm getting other errors though

thx

---

### Post by coldstatue on 2007-09-06
I am getting this error as well. It says that 2.8.0 or greater is required, but my repos have 2.10.something as the latest.  This is a new issue, as I built from source last week. In a quest to get stacks, I tried some other repos. Unsuccessful, I decided to recompile. Now this... bummer. Guess I'm on Kiba for a bit.

---

### Post by coldstatue on 2007-09-06
Just go from the repos. Stacks are included. Here's what i have had to do. I still get a clock that is invisible unless I hover over it, and a grey line for a notification area, but stacks works, as well as everything else.

Remove any installations of awn, and try to get rid of all files .

Turns out you must delete usr/local/bin/awn-manager

add these sources

deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator

then install avant-window-navigator-bzr

then install awn-core-applets-bzr

try to run it, and check out the prefs. I have hear some people need to restart for stacks, but it worked for me.

Hope this helps./

---

