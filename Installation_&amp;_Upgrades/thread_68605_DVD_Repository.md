---
title: "DVD Repository"
date: 2005-09-23
forum: Installation &amp; Upgrades
---

### Post by birdman on 2005-09-23
I have a very slow dial-up connection (7Mb/hr) and am unable to download software like everyone else.  How can I use my Debian Sarge DVDs as a repository using the Synaptic GUI ????

---

### Post by MetalMusicAddict on 2005-09-23
[QUOTE=birdman]I have a very slow dial-up connection (7Mb/hr) and am unable to download software like everyone else.  How can I use my Debian Sarge DVDs as a repository using the Synaptic GUI ????[/QUOTE]
Im not sure you can sir.

I think Debian and Ubuntu are just different enough so that it will be really hit and miss if you could.

Maybe somone could send you a Breezy DVD when it goes final? :) I use the DVD also.

---

### Post by Ptero-4 on 2005-09-23
[QUOTE=MetalMusicAddict]Im not sure you can sir.

I think Debian and Ubuntu are just different enough so that it will be really hit and miss if you could.

Maybe somone could send you a Breezy DVD when it goes final? :) I use the DVD also.[/QUOTE]
 Actually you can. Just insert your Debian DVD and in a terminal window type apt-cdrom (or something like that. Look at the apt man page for info). It will scroll some text and some minutes later it should say that it detected a CD and show you it's name (which should be Sarge) and eject the DVD, after that just click reload in synaptic and the packages in your Sarge DVD should appear in synaptic.

---

### Post by matthew on 2005-09-23
It is possible, but not a good idea.

If you use Debian repositories you will probably break your Ubuntu installation and end up with a mess that will require lots of work or a reinstallation to fix.

---

