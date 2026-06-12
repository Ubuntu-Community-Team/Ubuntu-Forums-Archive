---
title: "Wine Error."
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by Roasted on 2006-07-30
I tried installing Wine with these directions.

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

After the first step immediately following after I hit "reload" I got this error.

W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)

Just trying to make sense of it. Do I already have Wine installed?

---

### Post by ajgreeny on 2006-07-30
Looks to me as though when you followed the instructions you added a line to your sources.list file that was already there.

Look in synaptic to see if wine is already installed.  If not install it, open a terminal and type:-
*winecfg*
This will configure your install and let you install windows programs (some of them at least).  I have to admit, I have yet to get anything to work properly in wine so have given up entirely.  I have always found a linux prog that does everything I need so it was more of an academic exercise for me, anyway.

---

### Post by Roasted on 2006-07-30
If I could find a Linux version of Counterstrike or GTA San Andreas, I wouldn't even bother with Wine. But until I do, something will have to do the job... and it won't be Windows.

I did the winecfg and got this:

jason@Linux:~$ winecfg
wine: creating configuration directory '/home/jason/.wine'...
wine: '/home/jason/.wine' created successfully.
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
jason@Linux:~$

---

### Post by ajgreeny on 2006-07-30
Looks like the error message I got when I tried to install and configure wine.  As I said, I gave up as I didn't need it really so I will have to say that I can help no further.  Unfortunately no-one seemed able to help me, but I hope you fare better.

---

