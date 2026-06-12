---
title: "HEY! ISN'T possible!!!"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by pbeasynote on 2007-06-13
Hey there!

Can anyone describe for me, how to install my ati radeon xpress 200M, on my Packard Bell Easynote (In KUBUNTU, The Kubuntu forum, is pretty dead!)?
I've been looking at several "howto's", but i still can't get my graphic work properly. I've got the Ati control "center" installed, but the 3d acceleration doesn't work. Help out a newbie here... thank you! Wink

---

### Post by pbeasynote on 2007-06-13
Hey!

Can anyone help me, how to get my ralink rt73 wireless usb adapter (internal), installed. Can't find any useful guide.. thank you ;)

---

### Post by pbeasynote on 2007-06-13
Hey..

Isn't it possible to install, either the ati radeon xpress 200 m, or the rt73 (ralink) wireless network adapter???
[http://kubuntuforums.net/forums/index.php?topic=3084209.0](http://kubuntuforums.net/forums/index.php?topic=3084209.0)
[http://kubuntuforums.net/forums/index.php?topic=3084208.0](http://kubuntuforums.net/forums/index.php?topic=3084208.0)

thank you  :D

---

### Post by dfreer on 2007-06-13
What have you done so far to try to get the ati card installed?
What are the outputs of these two commands:
```
cat /etc/X11/xorg.conf
glxinfo | head
```

EDIT:
Moderator, duplicate threads:
ATI = [http://ubuntuforums.org/showthread.php?t=472769](http://ubuntuforums.org/showthread.php?t=472769)
rt73 = [http://ubuntuforums.org/showthread.php?t=472793](http://ubuntuforums.org/showthread.php?t=472793)

---

### Post by treris on 2007-06-13
Have you tried using Ndiswrapper? It usually helps when dealing with wireless cards that don't work, you can install it through Synaptic (Ubuntu) or Adept (Kubuntu) or the command line (apt-get install etc).

On the ndiswrapper website you can find a lot of information on how to get things working, including wpa etc.

[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) this is the site I was talking about.

Hope that helps, 

by the way, what do you mean when you say that you have wireless usb adapter (internal)? is it an usb device or an internal wireless card?

---

### Post by shae on 2007-06-13
[http://ubuntuforums.org/showpost.php?p=2780602&postcount=9]("http://ubuntuforums.org/showpost.php?p=2780602&postcount=9")

---

### Post by bapoumba on 2007-06-14
Threads merged, thanks dfreer (had spotted one, but not the other ;)).

---

### Post by stchman on 2007-06-14
> **pbeasynote said:**
> Hey there!

Can anyone describe for me, how to install my ati radeon xpress 200M, on my Packard Bell Easynote (In KUBUNTU, The Kubuntu forum, is pretty dead!)?
I've been looking at several "howto's", but i still can't get my graphic work properly. I've got the Ati control "center" installed, but the 3d acceleration doesn't work. Help out a newbie here... thank you! Wink

What version of Ubuntu?  If you are using Feisty it has ATI restricted drivers for video cards.  My laptop has a 200M as well and it runs great.  Google Earth and a few openGL games work fine.

If you are using Edgy then I have a procedure to install drivers for ATI cards.

[http://www.stchman.com/video_drivers.html](http://www.stchman.com/video_drivers.html)

Hope this helps.

---

