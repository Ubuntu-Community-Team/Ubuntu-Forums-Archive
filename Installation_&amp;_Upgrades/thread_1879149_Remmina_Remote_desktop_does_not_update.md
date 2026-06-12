---
title: "Remmina Remote desktop does not update"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by swissinvestor on 2011-11-11
I just installed Remmina and I get access to my remote machine. It also shows the desktop of my remote machine. However, when I change something on my remote machine, it does not update on my screen, i.e. from now on I am blind.

Is there anything which I have to allow like "desktop sharing allowed"?? Could not find anything like that.

any help appreciated.





Ubuntu 11.10 64

---

### Post by dino99 on 2011-11-11
[http://www.ubuntugeek.com/remmina-remote-desktop-client.html](http://www.ubuntugeek.com/remmina-remote-desktop-client.html)

[http://translate.google.com/translate?sl=fr&tl=en&js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fremmina](http://translate.google.com/translate?sl=fr&tl=en&js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fremmina)

---

### Post by swissinvestor on 2011-11-12
Thanks for this info. It did unfortunately not help me solve my problem.  Connection to my remote machine works perfectly and I also get the  screen view of my remote machine. However any changes are visible only  on my remote machine, the screen of my own machine does not update and I  can only watch on my remote machine what I am doing. I fiddled around  but cannot figure out the reason.

I am using Ubuntu 11.10 64 bit

---

### Post by Canaryguy on 2011-11-16
I'm also having this problem. When I connect to the remote computer I see the screen but it's a static one. I can do changes from my computer but I cannot see the effects on the remote one, and the refresh option doesn't work either. Only once it worked everything fine (about two weeks ago) and I thought it was because they released some updates but it was only that time. I hope a someone finds the solution for this.

I'm using Ubuntu 11.10 x32 (on a netbook)

---

### Post by sputnikeee on 2012-01-07
Hi.  I had exactly the same problem, Debian Squeeze, both machines, one an exact clone of the other, different hardware.  Funny thing was Remmina worked perfectly on the newer clone machine.  One way, not the other.
Anyhow, I believe you'll find popey here has the answer, worked great for me: [http://askubuntu.com/questions/14484/how-to-actually-use-remote-desktop?s=804a0c89-56a0-4c9c-a952-10e250511997#new-answer]("http://askubuntu.com/questions/14484/how-to-actually-use-remote-desktop?s=804a0c89-56a0-4c9c-a952-10e250511997#new-answer")

In case that disappears, here's the info:
>gconf-editor>desktop>gnome>remote access>disable_xdamage>check box.  That's it, it'll work now!

---

### Post by dually on 2012-09-10
Went to remote desktop, logged out and then logged back in "Ubuntu 2D".  Problem solved.

---

