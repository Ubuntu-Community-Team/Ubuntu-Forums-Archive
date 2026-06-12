---
title: "Installation on a really old computer"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by tromort on 2008-08-07
Well I got this headless pc at home, which is 5+ years old and has a 333mhz Cpu, 64mb ram and a 6gb harddisk. _Would this be enough for Xubuntu?_ and would it be better to put something lighter on it like puppy linux? im planning to use it to play music while im gaming/doing my stuff.

It doesnt has a usb port so i cant connect my 50gb music collection to it, but it does has a network port. _Would it be hard to set it up to use my network and let me control it with my main computer(ubuntu 8.04.1 amd64), like using remote desktop?_ since im not planning to give it a 'head'(monitor) or keyboard/mouse.

Thanks in advance, TroMorT.

---

### Post by Pumalite on 2008-08-07
Better a Minimal Install:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by tromort on 2008-08-07
> **Pumalite said:**
> Better a Minimal Install:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
thansk, that has been usefull. 
now the only question thats left: Would it be hard to set it up to use my network and let me control it with my main computer(ubuntu 8.04.1 amd64), like using remote desktop?

---

### Post by Pumalite on 2008-08-07
You can use openssh.
At the Terminal or
fish:// in Konqueror

---

### Post by tromort on 2008-08-07
> **Pumalite said:**
> You can use openssh.
At the Terminal or
fish:// in Konqueror
would you mind explaining what it is and does?

---

### Post by Pumalite on 2008-08-07
This might help:
[http://en.wikipedia.org/wiki/OpenSSH](http://en.wikipedia.org/wiki/OpenSSH)
[http://www.openssh.com/](http://www.openssh.com/)

---

### Post by snowpine on 2008-08-07
> **Pumalite said:**
> Better a Minimal Install:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

No, no, no... that would be good advice except for this: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959)

Basically, there is a bug in the Ubuntu installer. Nothing in the Ubuntu family will install easily on 64mb of ram until this bug is fixed! 

Your options are either get more ram, or try something outside the Ubuntu family, such as DSL or Puppy. Sorry. :(

ps It may be possible to use an older version of Xubuntu that doesn't have the installer bug.

---

### Post by tromort on 2008-08-07
> **Pumalite said:**
> This might help:
[http://en.wikipedia.org/wiki/OpenSSH](http://en.wikipedia.org/wiki/OpenSSH)
[http://www.openssh.com/](http://www.openssh.com/)
looks pretty complicated >.< so i install openssh on it and on my main pc and after opening some ports I will be able to controll it? if so, will it be command-line based of is a Graphical environment available? I'd probably be a huge noob when it comes down to just command line...

---

### Post by Pumalite on 2008-08-07
'ssh' at the cli
'fish://' (graphical) in Konqueror

---

