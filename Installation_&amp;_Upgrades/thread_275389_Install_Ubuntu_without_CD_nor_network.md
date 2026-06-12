---
title: "Install Ubuntu without CD nor network ?"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by pangel on 2006-10-11
Hi !

I have to install Ubuntu (or Kubuntu, I don't know what's the best for an ex-winxp user) on a somehow destroyed laptop. The cdrom drive is broken and it has no disk reader. He's also not supporting USB Boot...

But I have a direct access to the hard drive (with a usb adapter). Is it possible to install Ubuntu this way, then insert the hard drive back into the laptop, and then simply boot ?

Thanks for your help, the world of partitions, MBRs and boot sectors is extremly complex for me so I'd simply appreciate links for newbies (i searched and only found experts articles).

---

### Post by AgenT on 2006-10-17
You have a few options, one is a [network install]("http://www.ubuntuforums.org/showthread.php?t=276532"). The other would be to install via your USB drive. You may also use the cd image and mount it instead of burning the cd image to a cd and then installing using a cd rom drive. For example, extract the cd image into the hard drive and see if it will boot. If not, make your own booting hard drive. If you have access to the hd, it may be best to do some type of bare install, then connect it back into your laptop, boot into it, and continue with the rest of the install (possibly using chroot). 

You probably want more help than the above (how-to's or articles). Try searching these forums and google. Or maybe someone else will come by that knows links to such articles and by reading the above suggestions will be able to help you further. You may also try IRC and asking in the #ubuntu channel (server irc.freenode.org). TIP: Use X-Chat to connect to IRC (it will have the Ubuntu server listed and connect you to the channel automatically if you select it).

You should know that you will probably NOT find any newbie articles because what you are trying to do is not normal and requires know-how.

---

### Post by K.Mandla on 2006-10-18
> **AgenT said:**
> You should know that you will probably NOT find any newbie articles because what you are trying to do is not normal and requires know-how.
AgenT is right; that's a fairly complicated stunt.

You might have better luck installing Ubuntu on the drive in another laptop, then moving it back and reconfiguring it. That could be equally tricky.

Another option would be to copy the ISO on to the hard drive, and set up the hard disk to boot to the ISO. Again, not impossible, but definitely not easy. Here's a link that might help.

[http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948)

Good luck! ;)

---

### Post by AgenT on 2006-10-18
Also, you may want to look into this:
[http://www.damnsmalllinux.org/wiki/index.php/Loadlin_Install](http://www.damnsmalllinux.org/wiki/index.php/Loadlin_Install)
With this you can either 1) try to adapt this guide to Ubuntu or 2) install DSL and try to  dist-upgrade to Ubuntu (minimal). DSL is based on Knoppix which is based on Debian. Whatever the case may be, they use apt-get which is all you should need.

EDIT:
And this may interest you:
debootstrap (install Debian without an installation + more)
[ man debootstrap]("http://manpages.debian.net/cgi-bin/display_man.cgi?id=979b6659f1505e7d44a1e914f4875868&format=html")
[http://www.inittab.de/manuals/debootstrap.html](http://www.inittab.de/manuals/debootstrap.html)

---

