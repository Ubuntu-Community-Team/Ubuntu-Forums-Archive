---
title: "sudo broken?!"
date: 2008-06-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2008-06-20
I've hit a biggie this morning, I write to you from my xubuntu live CD as sudo no longer functions on my install. Take a guess at how usable a system is without sudo!!

When accessing anything requiring root it states cannot access /etc/sudoer: permission denied. This causes errors during bootup and dumps me at a command line. This happened shortly after updates last night. I'm guessing my easiest way out is a re-install but I'm curious, is there any way to correct an error  in the filesystem without root access?

---

### Post by Raptor45 on 2008-06-20
What makes you say there is an error with the filesystem? Assuming that wasn't want you meant:

If the problem is just update related, you can simply chroot into your install to apply further updates until the problem resolves. To do this mount your root partition (from your livecd, or wherever), and do "sudo chroot /media/intrepid" replacing with the location of wherever your intrepid is mounted.

Was this caused by an update? Or were you doing anything else that might have caused /etc/sudoer to be denied?

---

### Post by caryb on 2008-06-20
In KDE4 at present to sudo you have to give the root user a password as sudo is actually the root user password not your password elevated! (I probably sound like I'm speaking gibberish) It got me at 1st but I'm now happily sudo-ing away:lolflag:


Cary

---

### Post by macroshaft on 2008-06-20
When I say a problem with 'the filesystem' I mean the partition labelled filesystem which all requires root to modify it.

---

