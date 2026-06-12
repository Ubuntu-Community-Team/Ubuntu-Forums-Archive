---
title: "Please Remove Pulseaudio!!!!!!!!!!"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Hackbert's Celine on 2008-10-15
I couldnt find any improvement for a Desktop User. Why not put in Ubuntu Studio or some other Port vor Special Audio interests. At the moment i will just remove it from my hardy, since it needs a fix for almost every sound app wich wants to use it. And it refuses to be turned off in Boot up manager (wtf?). As in many Forum posts said ITS NOT STABLE ENOUGH AND MUCH MUCH TO SPECIALLY.

---

### Post by olskar on 2008-10-15
> **Hackbert's Celine said:**
> I couldnt find any improvement for a Desktop User. Why not put in Ubuntu Studio or some other Port vor Special Audio interests. At the moment i will just remove it from my hardy, since it needs a fix for almost every sound app wich wants to use it. And it refuses to be turned off in Boot up manager (wtf?). As in many Forum posts said ITS NOT STABLE ENOUGH AND MUCH MUCH TO SPECIALLY.

And as has been said before, it is not pulseaudios fault,it is a poor implementation in Ubuntu. It will only get better and better :)

---

### Post by Slug71 on 2008-10-15
Switch to Intrepid. Pulse works perfect.

---

### Post by plun on 2008-10-15
For Hardy users I recommend this howto. A great one...

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

:guitar:

---

### Post by xebian on 2008-10-15
> **Slug71 said:**
> Switch to Intrepid. Pulse works perfect.

The OP is posting here at Intrepid Ibex forum.  So it's reasonable to assume he has Intrepid.  ???

---

### Post by psyke83 on 2008-10-15
> **xebian said:**
> The OP is posting here at Intrepid Ibex forum.  So it's reasonable to assume he has Intrepid.  ???

Unfortunately I don't think so - he's referred to Hardy in his post.

---

### Post by xebian on 2008-10-15
> **psyke83 said:**
> Unfortunately I don't think so - he's referred to Hardy in his post.

You are right.  Sorry I missed that tiny hardy there.

---

### Post by psyke83 on 2008-10-15
> **Hackbert's Celine said:**
> I couldnt find any improvement for a Desktop User. Why not put in Ubuntu Studio or some other Port vor Special Audio interests. At the moment i will just remove it from my hardy, since it needs a fix for almost every sound app wich wants to use it. And it refuses to be turned off in Boot up manager (wtf?). As in many Forum posts said ITS NOT STABLE ENOUGH AND MUCH MUCH TO SPECIALLY.

UbuntuStudio doesn't use PulseAudio because they need low latency, which is something that PulseAudio can't provide at the moment. From what you wrote, it seems you don't have a full understanding of how PulseAudio works. In Hardy, disabling PulseAudio from the Session properties can cause ALSA applications to fail, depending on the way you configured your system.

PulseAudio is much improved in Intrepid, and should work "out of the box", unlike Hardy. There is a guide for [Hardy]("http://ubuntuforums.org/showthread.php?t=789578") and [Intrepid]("http://ubuntuforums.org/showthread.php?t=866965") (the latter is to ensure that obsolete configuration files from Hardy won't interfere).

---

### Post by FuturePilot on 2008-10-15
It wouldn't make any sense to put it in Ubuntu Studio. PulseAudio is not meant for audio/video production. You need low latency for that. The Hardy configuration of PulseAudio was bad, there's no denying that. But it is 100x better in Intrepid.

---

