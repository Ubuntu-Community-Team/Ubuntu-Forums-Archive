---
title: "Crippling kernel issue ubuntu 12.04"
date: 2012-06-02
forum: Installation &amp; Upgrades
---

### Post by ntzrmtthihu777 on 2012-06-02
HELP!

Was trying to get my laptop's (hp dv9000) sound right (headphones work but not speakers) and followed the advice here
[http://ubuntuforums.org/showthread.php?t=1967394&highlight=sound+work+built+speakers&page=2](http://ubuntuforums.org/showthread.php?t=1967394&highlight=sound+work+built+speakers&page=2)

should of stayed away as im a total noob in linux, but forged ahead and got screwed. Now anytime i use the software center, synaptic, or anything of that sort (including various terminal commands apt-get remove, install etc) I get this error

E:The package linux-image-3.0.0-13-generic needs to be reinstalled, but I can't find an archive for it.

Please help!

---

### Post by ntzrmtthihu777 on 2012-06-02
Whew! just found a solution:

sudo dpkg --remove --force-remove-reinstreq linux-image-3.0.0-13-generic

My advice for other total noobz: Don't screw around with kernels unless you know EXACTLY what you're doing

---

