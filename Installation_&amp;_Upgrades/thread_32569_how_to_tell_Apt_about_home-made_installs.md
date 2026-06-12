---
title: "how to tell Apt about home-made installs"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by gratefulfrog on 2005-05-08
I am doing a lot of compiling and installing software that is not available at the Ubuntu repositories, or if it is available, the version offered is defective or out of date.

Can anyone tell me how to inform apt of these installations so that it doesn't overwrite my versions with packages that it installs as dependencies?

An example of this is **ffmpeg**. The Ubuntu version is out of date and defective on my AMD64 platform. I unistalled the Ubuntu package, then downloaded the current cvs snapshot, built and installed it for my platform. It works perfectly! But, now, apt (synaptic)  won't let me install software that depends on ffmpeg! so I am stuck!

 :?

---

### Post by kvidell on 2005-05-08
[QUOTE=gratefulfrog]I am doing a lot of compiling and installing software that is not available at the Ubuntu repositories, or if it is available, the version offered is defective or out of date.

Can anyone tell me how to inform apt of these installations so that it doesn't overwrite my versions with packages that it installs as dependencies?

An example of this is **ffmpeg**. The Ubuntu version is out of date and defective on my AMD64 platform. I unistalled the Ubuntu package, then downloaded the current cvs snapshot, built and installed it for my platform. It works perfectly! But, now, apt (synaptic)  won't let me install software that depends on ffmpeg! so I am stuck!

 :?[/QUOTE]
 I may be wrong but I think you have to compile it in to a .deb package and install that, rather than compiling straight from source, for the dependancies and aptitude system to be aware of it's existance.
Though as was pointed out to me in one of my threads, compiling things by hand wont upset apt, per se.
I hand compiled a firefox install once ,then decided to go back to the Apt one, apt-get'd it and they both just kind of sat there like "'sup?" and the bins were updated for the apt'd one.. My compile remained but wasn't used unless I really needed something it did that the apt'd one didn't (this was on Debian, mind you).
- Kev

---

### Post by gratefulfrog on 2005-05-08
[QUOTE=kvidell]I may be wrong but I think you have to compile it in to a .deb package ...[/QUOTE]

Thanks for the tip!  Could you point me to doc on how to compile into a .deb package?

I definitely cannot let apt install over my builds since they work and the repository ones don't.

Cheers,
GF

---

### Post by kvidell on 2005-05-08
Source: [http://ubuntuforums.org/showthread.php?t=22237](http://ubuntuforums.org/showthread.php?t=22237)

> Just install "checkinstall" (from the Ubuntu repositories), then
everytime you compile sometihng from source instead of issuing a "make
install", run "checkinstall". It will integrate your new program
perfectly into the system, and you can see it in Synaptic etc :-D

That might do ya :)
- Kev

---

### Post by gratefulfrog on 2005-05-08
[QUOTE=kvidell]Source: [http://ubuntuforums.org/showthread.php?t=22237](http://ubuntuforums.org/showthread.php?t=22237)



That might do ya :)
- Kev[/QUOTE]
 Hey Kev,

Thanks that's just what I've been looking for! And once again, the Ubuntu forums are the place to be... This should go into a mini-hoto... How about it, jdodson or jdong?

---

