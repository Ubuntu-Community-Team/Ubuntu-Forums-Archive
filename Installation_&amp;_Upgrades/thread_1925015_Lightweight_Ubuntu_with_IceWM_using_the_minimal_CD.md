---
title: "Lightweight Ubuntu with IceWM using the minimal CD"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by H3R3T1K on 2012-02-13
I wanna do something like this:[U]
[/U][https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://easierbuntu.blogspot.com/2008/04/building-lightweight-ubuntu-install.html](http://easierbuntu.blogspot.com/2008/04/building-lightweight-ubuntu-install.html)

So I installed the Ubuntu core using the 11.10 minimal image in Virtualbox and selected to install packages myself. Problem is after booting I'm not greeted with a login prompt. I can't even access the command line. I don't know how to at least. Any ideas what could have gone wrong?

---

### Post by Paddy Landau on 2012-02-14
I'm sorry, I don't know the answer, but as no one else has answered, let me give you my suggestion.

Instead of trying to build your own from outdated documentation, what about using a ready-made lightweight distro? If you want to stay with the Ubuntu family, try [Lubuntu]("https://wiki.ubuntu.com/Lubuntu"). Otherwise have a look at other lightweight distros, such as [Bodhi]("http://www.bodhilinux.com/") or [Puppy]("http://puppylinux.org/").

---

### Post by josephmills on 2012-02-14
> **H3R3T1K said:**
> I wanna do something like this:[U]
[/U][https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://easierbuntu.blogspot.com/2008/04/building-lightweight-ubuntu-install.html](http://easierbuntu.blogspot.com/2008/04/building-lightweight-ubuntu-install.html)

So I installed the Ubuntu core using the 11.10 minimal image in Virtualbox and selected to install packages myself. Problem is after booting I'm not greeted with a login prompt. I can't even access the command line. I don't know how to at least. Any ideas what could have gone wrong?

what do you mean you can login ? you get the prompt and cant enter anything ?

---

### Post by H3R3T1K on 2012-02-15
> **josephmills said:**
> what do you mean you can login ? you get the prompt and cant enter anything ?

Well there's the blinking underscore at the top left after it's shown the "Ubuntu 11.10" sign and that's it. I'm waiting for it to finish booting and show the login prompt but there's nothing happening.

@Paddy: I know Bodhi and Puppy. I envisioned it to be kind of an exercise for me :D

---

### Post by A_T on 2012-02-24
I found myself in a similar situation. Ctl-Alt-F6 gave me a prompt though I've no idea why.

---

### Post by Paddy Landau on 2012-02-24
> **A_T said:**
> Ctl-Alt-F6 gave me a prompt though I've no idea why.
You have 12 "sessions" available to you, and they are started by Ctrl-Alt-1, Ctrl-Alt-2, etc. The normal GUI session is Ctrl-Alt-7. If you press Ctrl-Alt-6 by accident, just press Ctrl-Alt-7 to get back to your normal session.

---

