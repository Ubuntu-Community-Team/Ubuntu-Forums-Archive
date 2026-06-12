---
title: "howto dri2 with 2.6.26 kernel and intel (i915)?"
date: 2008-06-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by marijus on 2008-06-29
can anybody give some advice what i have to do to get this running?
i think this howto:

[http://hoegsberg.blogspot.com/2008/02/building-and-installing-drmdrix-stack.html]("http://hoegsberg.blogspot.com/2008/02/building-and-installing-drmdrix-stack.html")

is outdated since we are using 2.6.26 kernel now or am i wrong???
thanks in advance!
marijus

---

### Post by psyke83 on 2008-06-29
It's not a good idea to try DRI2 at the moment - everything is in a state of flux. There was a lot of work on the "batchbuffer" branch as the basis for DRI2, but the Xorg/Mesa developers seem to have abandoned it overnight in favour of yet another new idea, "drm-gem".

Lots of components need to be built from a non-master branch in git - and if you do manage to get everything built, this new code is extremely experimental, prone to crashing, and when it doesn't crash, performance is no better than what we're using now.

I'd say you're better off waiting.

---

### Post by marijus on 2008-06-29
hm... regarding many posts on the net should be pretty stable at least for intel graphics... :(

---

### Post by psyke83 on 2008-06-30
> **marijus said:**
> hm... regarding many posts on the net should be pretty stable at least for intel graphics... :(

I'd like you to point those posts out to me, please. Also, there is quite a large range of Intel chipsets and they don't have a perfectly unified architecture. The fact is that the "drm-gem" code is highly experimental and has probably been tested on a very limited subset of (Intel) graphics chipsets - those that the Xorg/Mesa developers use.

Building Xorg from git, without a lot of experience, is not a good idea on a Debian-based system. A distribution such as Gentoo, Slackware or perhaps Fedora rawhide may be suited better.

---

### Post by RAOF on 2008-06-30
There's nothing particularly harder building a git X server on Debian than Gentoo or Slackware or whatever.  The only possible exception is if you need some newer infrastructure (newer libdri, or something) in order to build one of the pieces.  Given that you're already building at least libdrm, the kernel modules, mesa, and xorg-xserver from git (and some from non-master branches), one or two more components isn't going to make a lot of difference :).

---

### Post by psyke83 on 2008-06-30
> **RAOF said:**
> There's nothing particularly harder building a git X server on Debian than Gentoo or Slackware or whatever.  The only possible exception is if you need some newer infrastructure (newer libdri, or something) in order to build one of the pieces.  Given that you're already building at least libdrm, the kernel modules, mesa, and xorg-xserver from git (and some from non-master branches), one or two more components isn't going to make a lot of difference :).

I'll take your word for it, then ;). The last time I made a serious attempt to build all the Xorg/Mesa components from scratch (a couple of years ago), it was difficult to integrate the -dev sources without conflicting with Ubuntu's older package versions. It may have been more difficult since I was attempting to build from a non-master branch ;).

My point is that Ubuntu's development packages are referenced from Debian's latest (unstable?), whereas Gentoo and others tend to work more directly with upstream's code.

---

### Post by marijus on 2008-07-02
> **psyke83 said:**
> I'd like you to point those posts out to me, please.

[http://forum.compiz-fusion.org/showthread.php?t=7722]("http://forum.compiz-fusion.org/showthread.php?t=7722")

you can find more by google "dri2 intel"
regards!
marijus

---

### Post by plun on 2008-07-02
Maybe a good start point....

[http://wiki.debian.org/XStrikeForce](http://wiki.debian.org/XStrikeForce)


And for sure try to build it.... just a stupid MS way
to not trying.  We must explore and learn more.

Please share what you finds out even if it fails...:)

---

### Post by psyke83 on 2008-07-02
> **marijus said:**
> [http://forum.compiz-fusion.org/showthread.php?t=7722]("http://forum.compiz-fusion.org/showthread.php?t=7722")

you can find more by google "dri2 intel"
regards!
marijus

That thread is from April, talking about TTM - work on that seems to have been halted in favour of DRM-GEM. There's not much information on this simply because it's so new...

[http://lwn.net/Articles/283798/](http://lwn.net/Articles/283798/)
Edit: this may also help: [http://lists.freedesktop.org/archives/intel-gfx/2008-July/000165.html](http://lists.freedesktop.org/archives/intel-gfx/2008-July/000165.html)

---

### Post by plun on 2008-07-02
Some more findings after a quick look within Xstrikeforce mailing list...

There is a new dri2-dev package within Debian Sids repo

[http://packages.debian.org/sid/x11proto-dri2-dev](http://packages.debian.org/sid/x11proto-dri2-dev)

[http://lists.debian.org/debian-x/2008/06/msg00322.html](http://lists.debian.org/debian-x/2008/06/msg00322.html) 

Maybe a start...:)

(I am using a few Debian Sid packages for Google Gadgets built from source)

---

### Post by tormod on 2008-07-02
Please have a look at [https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers) for a project that has easy scripts to build packages from git. It's basically [http://wiki.debian.org/XTips](http://wiki.debian.org/XTips) automated.

Peter Clifton posted to ubuntu-x about this: [https://lists.ubuntu.com/archives/ubuntu-x/2008-June/000187.html](https://lists.ubuntu.com/archives/ubuntu-x/2008-June/000187.html) but I haven't had time to look at it and change the mesa build like he suggests.

Hint: to build something from the drm-gem branch, just use the -b option to "auto-xorg-git".

---

### Post by marijus on 2008-07-03
thanks for the help...
seems to be more complicated than i thought to... i'll give it a try when i have some spare time though...
regards! marijus

---

### Post by Gina on 2008-07-03
Please bear in mind that Intrepid is in the very early stages and in many cases will need complicated "hacks" to get things working.  If this is a problem I suggest watching and waiting for these things to be fixed before continuing with testing Intrepid.  If you want things to work, stick with Hardy 8.04.1 release due one any time now.  Though I'm not trying to discourage you from having a go :)

---

### Post by aamukahvi on 2008-07-03
libdrm 2.3.1 just came through, shouldn't be long now
[http://tjaalton.wordpress.com/2008/07/03/new-libdrmmesaxorg-serverxorg-shaping-up/](http://tjaalton.wordpress.com/2008/07/03/new-libdrmmesaxorg-serverxorg-shaping-up/)

---

### Post by FranMichaels on 2008-07-25
Can anyone confirm if it is in the alpha 3. If so, I'll dist-upgrade right now and join the testers. Been waiting for this for a long time now... :KS

EDIT: Thanks spamzilla. My real question is, does one get redirected direct rendering with an intel chipset.
I'm just looking for a "yes" from one user :D

---

### Post by spamzilla on 2008-07-25
libdrm2.3.1 is in alpha 3

---

### Post by funnypanks on 2008-07-25
> **FranMichaels said:**
> Can anyone confirm if it is in the alpha 3. If so, I'll dist-upgrade right now and join the testers. Been waiting for this for a long time now... :KS

EDIT: Thanks spamzilla. My real question is, does one get redirected direct rendering with an intel chipset.
I'm just looking for a "yes" from one user :D

no it doesnt. when i move windows around that are playing videos the video stays stationary and then moves when i release the mouse.

opensuse 11 and fedora 9 have it working but fullscreen video playback is borked in both of those distros

---

### Post by psyke83 on 2008-07-25
> **FranMichaels said:**
> Can anyone confirm if it is in the alpha 3. If so, I'll dist-upgrade right now and join the testers. Been waiting for this for a long time now... :KS

EDIT: Thanks spamzilla. My real question is, does one get redirected direct rendering with an intel chipset.
I'm just looking for a "yes" from one user :D

You're not going to get a "yes" for Intrepid. DRI2 is now based upon the GEM (Graphics Execution Manager) which has not yet landed in the main branches of mesa/xorg/drivers. Furthermore, libdrm 2.3.1 does not support DRI2 (2.4.0 or later will), and the older batchbuffer and TTM has been obsoleted by GEM.

You can compile from GIT to test GEM (and thus DRI2), but it's simply not going to make it into Intrepid.

---

### Post by FranMichaels on 2008-07-25
> **psyke83 said:**
> You're not going to get a "yes" for Intrepid. DRI2 is now based upon the GEM (Graphics Execution Manager) which has not yet landed in the main branches of mesa/xorg/drivers. Furthermore, libdrm 2.3.1 does not support DRI2 (2.4.0 or later will), and the older batchbuffer and TTM has been obsoleted by GEM.

You can compile from GIT to test GEM (and thus DRI2), but it's simply not going to make it into Intrepid.

Thanks. I may indeed give it a try, if there is a good how-to for hardy. Or I'll wait a bit. I'm not as confident with compiling big things like xorg.

---

