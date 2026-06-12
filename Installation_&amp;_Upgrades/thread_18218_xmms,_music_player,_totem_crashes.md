---
title: "xmms, music player, totem crashes"
date: 2005-03-05
forum: Installation &amp; Upgrades
---

### Post by hesee on 2005-03-05
I cannot open xmms, music player, totem, (most propably any multimedia software) anymore. This is for example what i get when try to start xmms on console:

heikki@ubuntu:~ $ xmms
libmikmod.so.2: cannot open shared object file: No such file or directory
Inconsistency detected by ld.so: ../sysdeps/generic/dl-tls.c: 72: _dl_next_tls_modid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx' failed!

All the sounds in gnome work. I haven't had any problems before, didn't install anything new, except firestarter. Oh yes and i did run apt-get update and upgrade also. Please help me!

---

### Post by bored2k on 2005-03-05
[QUOTE=hesee]I cannot open xmms, music player, totem, (most propably any multimedia software) anymore. This is for example what i get when try to start xmms on console:

heikki@ubuntu:~ $ xmms
libmikmod.so.2: cannot open shared object file: No such file or directory
Inconsistency detected by ld.so: ../sysdeps/generic/dl-tls.c: 72: _dl_next_tls_modid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx' failed!

All the sounds in gnome work. I haven't had any problems before, didn't install anything new, except firestarter. Oh yes and i did run apt-get update and upgrade also. Please help me![/QUOTE]


the questions is from what source did u upgrade.... anyways

try beep-media-player , vlc 


vlc is known to play everything no matter what ..

---

### Post by alastair on 2005-03-05
What version of Ubuntu - upgrade to what?

I have libmikmod here :

# ls -l  /usr/lib/libmikmod*
.. /usr/lib/libmikmod.so.2 -> libmikmod.so.2.0.4
.. /usr/lib/libmikmod.so.2.0.4

Do you?

Maybe try reinstalling xmms (or libmikmod).

---

### Post by bored2k on 2005-03-05
[QUOTE=alastair]What version of Ubuntu - upgrade to what?

I have libmikmod here :

# ls -l  /usr/lib/libmikmod*
.. /usr/lib/libmikmod.so.2 -> libmikmod.so.2.0.4
.. /usr/lib/libmikmod.so.2.0.4

Do you?

Maybe try reinstalling xmms (or libmikmod).[/QUOTE]
 he said he had upgraded, if he upgraded thru a *crooked* source stuff might pop up, thats all .

---

### Post by hesee on 2005-03-05
Ok, thanks for answers. First of all, i installed libmikmod again and now xmms is working. 

But, rhythmbox,etc, are not working. I cannot even start Applications -->  Multimedia --> Volume Control, gives an error: Sorry, no mixer elements and/or devices found.
Would be nice if someone could help with that.

Upgrading: I'm a newbie, this is what I thought upgrade does: It upgrades my existing, installed software (packages?). Please correct if i'm wrong. This is what i have in sources.list:


deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted   
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted   

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe

---

### Post by alastair on 2005-03-05
Upgrades are always slightly risky - a complete system upgrade more so. Debian/Ubuntu have a pretty good reputation for doing this sort of thing safely, but there is so much s/w and h/w around that there is always a risk.  Do not treat a system upgrade as trivial.

As for rhythmbox - try starting it from a shell and seeing what errors are printed i.e.

type : rhythmbox

---

### Post by hesee on 2005-03-05
I typed: rhythmbox

Nothing in the shell, put an error window pops up:
Error:
Failed to create the player: Couldn't initialise scheduler. Did you run gst-register?


Hmm, if it's risky to upgrade, how can i for example have all security updates for my system? Should i comment everything from sources.list except these:

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

...and then upgrade?

---

### Post by bored2k on 2005-03-05
[QUOTE=hesee]I typed: rhythmbox

Nothing in the shell, put an error window pops up:
Error:
Failed to create the player: Couldn't initialise scheduler. Did you run gst-register?


Hmm, if it's risky to upgrade, how can i for example have all security updates for my system? Should i comment everything from sources.list except these:

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

...and then upgrade?[/QUOTE]
 try running >  $ gst-register-0.8 then retrying

btw i installed most of the updates of universe main multiverse backports and java, and havent had anyproblems with sound . pointing that out so u dont get scared of upgrading next time [if its a backport its ok 2 be scared tho :P]

---

### Post by hesee on 2005-03-05
I installed multimedia codecs :

gstreamer0.8-plugins 
w32codecs

Now rhythmbox and everything works fine. Something was missing, maybe gstreamer?

---

### Post by bored2k on 2005-03-05
[QUOTE=hesee]I installed multimedia codecs :

gstreamer0.8-plugins 
w32codecs

Now rhythmbox and everything works fine. Something was missing, maybe gstreamer?[/QUOTE]
 the plugins are mainly to support mp3 playback and such, w32 had nuffin to do tho ...

now that u hav w32, it goes well with a mozilla-mplayer for streams ;)

---

