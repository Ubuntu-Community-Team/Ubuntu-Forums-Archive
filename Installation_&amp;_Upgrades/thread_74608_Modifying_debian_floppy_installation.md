---
title: "Modifying debian floppy installation"
date: 2005-10-12
forum: Installation &amp; Upgrades
---

### Post by mr_mop on 2005-10-12
Hi,

Is it possible to say modify the debian floppy installer:
[http://ftp.uk.debian.org/debian/dists/sarge/main/installer-i386/current/images/floppy/](http://ftp.uk.debian.org/debian/dists/sarge/main/installer-i386/current/images/floppy/)
to install the ubuntu base system?

I have followed the thread
[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)
to install on a laptop, but I would like to install breezy and type 'server' at the install prompt.  Doing it following the thread it is not possible to get the installer prompt.

Thanks

MM

---

### Post by mlomker on 2005-10-12
> 
Is it possible to say modify the debian floppy installer:
[http://ftp.uk.debian.org/debian/dists/sarge/main/installer-i386/current/images/floppy/](http://ftp.uk.debian.org/debian/dists/sarge/main/installer-i386/current/images/floppy/)
to install the ubuntu base system?


I've seen the question asked quite a few times, but never answered.

If the machine is capable of booting to a network card then you could explore configuring a PXE boot server instead.

---

### Post by mr_mop on 2005-10-12
Thanks for that, I will try.  I take it this does give you chance to type 'server' at the prompt?  I will try it tonight and install on my laptop!

I was also hoping to take on boot floppy challenge to see if I could do it.  Been looking for a nice linux task to tackle for a while and this looked a worthy one.  As you said having a floppy install is a popular request :)
If anyone has any ideas, please let me know :)

---

### Post by mlomker on 2005-10-12
> I take it this does give you chance to type 'server' at the prompt?

If the laptop supports network boot then it actually boots the .iso image of the CD, but through the network card.

---

### Post by mr_mop on 2005-10-12
In the boot order in the BIOS, there is an option to set network, so this must be possible.  I imagine that CD-less laptops will all be able to do this, otherwise there would be no way to get the OS on in the first place :)

---

### Post by mlomker on 2005-10-12
>  I imagine that CD-less laptops will all be able to do this, otherwise there would be no way to get the OS on in the first place

Exactly.  We have a bunch of the tiny IBM laptops at work and that's how we get WinXP installed on them.

---

### Post by mr_mop on 2005-10-16
Well I ran into a problem.  The PCMICA ethernet card is not detected by the BIOS, so its not booting from the network! :(
I'll have to go back to the drawing board....

---

### Post by mr_mop on 2005-10-19
Looks like someone beat me to it! :)
[http://ubuntuforums.org/showthread.php?t=75372](http://ubuntuforums.org/showthread.php?t=75372)

---

