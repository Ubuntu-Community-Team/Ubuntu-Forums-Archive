---
title: "Mplayer cannot open."
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by ForksHolder on 2008-07-03
Hello,
When i run mplayer it just won't start.. don't know why..

my ubuntu is Hardy.

Thanks,
ForksHolder

---

### Post by brazemcee on 2008-07-03
Try removing it and reinstalling it.
You can do it with Synaptic app.

---

### Post by ForksHolder on 2008-07-03
> **brazemcee said:**
> Try removing it and reinstalling it.
You can do it with Synaptic app.

already tried it few times.. =/

---

### Post by spike_strip on 2008-07-03
I prefer to use xine. Works well!

---

### Post by ForksHolder on 2008-07-08
Here is the Terminal error:

> older@holder-laptop:~$ gmplayer
MPlayer dev-SVN-r27141-4.2.3 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 2.00GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Cannot load bitmap font: Tahoma
[skin] file ( /usr/local/share/mplayer/skins/default/skin ) not found.
Skin not found (default).


1) It won't open
2) I need this Tohama
3) The skin? Dunno what's with it..


Any ideas?

---

### Post by confused57 on 2008-07-08
You could try reinstalling mplayer-skins...may not work, but worth trying.

---

### Post by forger on 2008-07-08
close mplayer

remove/backup the configuration:
```
mv ~/.mplayer ~/OLDmplayer
```

```
sudo aptitude purge mplayer mplayer-skins
sudo aptitude install mplayer
```

It should run now :)

---

### Post by ForksHolder on 2008-07-09
> **forger said:**
> close mplayer

remove/backup the configuration:
```
mv ~/.mplayer ~/OLDmplayer
```

```
sudo aptitude purge mplayer mplayer-skins
sudo aptitude install mplayer
```

It should run now :)

Well, I've tried it and:

> holder@holder-laptop:~$ gmplayer
MPlayer dev-SVN-r27141-4.2.3 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 2.00GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Creating config file: /home/holder/.mplayer/config
[skin] file ( /usr/local/share/mplayer/skins/default/skin ) not found.
Skin not found (default).



Again. =/
Ideas?

---

### Post by andrew.46 on 2008-07-11
Hi,

You seem to be opening the gui of the svn mplayer *without* a skin. You could try to load a skin:

```
$ cd $HOME
$ mkdir -pv $HOME/.mplayer/skins/default
$ wget http://www.mplayerhq.hu/MPlayer/skins/Blue-1.7.tar.bz2
$ tar xjvf Blue-1.7.tar.bz2 
$ cp -Rv $HOME/Blue/* $HOME/.mplayer/skins/default
```

And then try again. There are of course many skins but Blue is pretty standard.

  Andrew

---

### Post by ForksHolder on 2008-07-11
Thanks! Sloved!

---

