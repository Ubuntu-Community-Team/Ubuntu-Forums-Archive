---
title: "installation on an old pc: is it possible?"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by acidbee on 2006-12-05
Hi.
I'd like to install Ubuntu on a rather old machine (now I'm running vectorlinux on it, and I want to keep 'em both).
Here are the specs: 
cpu amd k-6 200 mhz
ram 64 mb
video: 8 mb
hd: 5gb+ 80 gb (this is NOT the poblem).

I saw somewhere that Ubuntu requires at least 256 mb.. but what if I use fluxbox o icewm or windowmaker istead of gnome/(kde)? And I could stop some daemons/procs...

Vector is running fine and fast (well, if I don't run too much applications), but I'd like to have a little more user-friendly system.. even because I have to install some complicated stuff, and I don't want (and I can't) spend a lot of time with dependencies and tarballs and command-line compiling (the most helpful feature is midnight commander..................).

The question is: is it possible?

thanks!

---

### Post by marianom on 2006-12-05
[Xubuntu]("http://www.xubuntu.org/") might help

---

### Post by wpshooter on 2006-12-05
I think it is probably possible with xubuntu, but IMO, I don't think it would be worthwhile.

Get youself a bit better system on which you can install and run Ubuntu/Gnome interface and I think you would be much more satified.

Good luck.

---

### Post by matt_risi on 2006-12-05
That's a little TOO low-end, I'm afraid to say. I'm really into using Ubuntu on lower-end machines, but your system's resources are just too low to have any reasonable performance, even using lightweight window managers. If I were thee, I'd stick to vector.

If you really wanna give it a shot, then download and burn the Ubuntu 6.06.1 Alternate cd and do the install. Then "sudo apt-get install x" where x is openbox, fluxbox, icewm, etc. Don't expect very much usability though. In fact, K. Mandla, a member of this forum sort of specializes in installing Ubuntu on legacy hardware and would probably be a better resource than me.

Good luck, let us know how it goes if you choose to dive in.

---

### Post by kerry_s on 2006-12-05
If it has to be ubuntu, i'd go for custom build up.-> [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

But if you want to just install, try DSL linux-> [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by matt_risi on 2006-12-05
Good of you to point that out kerry!

---

### Post by acidbee on 2006-12-06
thanks..
That machine is mainly meant for downloads from the web, so I don't need great speeds and all that. Besides, I'd like to recycle that pc for a 12 years old kid (my intention is to introduce him to linux but without scaring him too much).
Dsl is fine on old hardware but it lacks some useful apps.. for ex., it has no "great" graphical or word processing apps.. xpaint can't compete with the Gimp, and there's no compatibility with .doc format. On vectorlinux I have those apps, but installations, upgrades and system maintenance bore even ME.. and maybe Vector is a bit too radical for a 12 y.o. newbie..
I could try with xubuntu and install fluxbox.. or what could I do?

O.T.: I'm wrong or system requirements really increased in the latest (2) years? I still remember suse or mdk and the first ubuntu distros running fine on old/slow machines..

---

### Post by Titus A Duxass on 2006-12-06
Have a look at Puppy linux if you don't like DSL.

---

### Post by mibadt on 2006-12-06
Try looking at Feather Linux.
If you're ready for some investment upgrade the memory to 128MB and you'll be able to install Ubuntu alternate.

---

### Post by acidbee on 2006-12-06
I can't upgrade to 128 mb or more simply because I can't find those old memory sticks anymore..
I'm having a look at fluxbuntu, but the web pages are a bit poor on information. Or maybe I can try xbuntu and, then I could had fluxbox as default dm...

---

### Post by Sef on 2006-12-06
Some other distros to look at are [deli linux]("http://delili.lens.hl-users.com/"), [vector linux]("http://vectorlinux.com/"), and [dsl]("http://www.damnsmalllinux.org/").

---

### Post by Johnsie on 2006-12-06
dsl is good and I also liked [puppy]("http://www.puppylinux.com/"). Dsl is based on debian so it might be more comfortable for an ubuntu user.

---

### Post by acidbee on 2006-12-06
Thanks Sef... I'm already running vector, but the goal was having a more user-friendly distro.
Now I'm gonna try fluxbuntu...if it supports the same package administration as ubuntu/xubuntu, I'll keep it. Otherwise I'll try an alternate install of xbuntu and add fluxbox as the default dm..

---

