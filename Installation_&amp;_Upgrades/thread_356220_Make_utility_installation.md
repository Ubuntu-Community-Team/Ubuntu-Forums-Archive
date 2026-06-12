---
title: "Make utility installation"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by talrasha on 2007-02-08
Hi everyone, Im using  Dapper as of now and I've downloaded "make-3.81.tar.gz" utility to install my modem driver conexant. I just want to know how to install the "make-3.81.tar.gz" in Drapper and where should I place the installation directory?

Thanks guys! Hoping for your reponse ^^

---

### Post by tkjacobsen on 2007-02-08
have you tried to install build-essential from synaptic instead, it includes make 3.81, and other software needed to compile programs/drivers yourself..

Usually you should always try to use software form synaptic, add/remove, apt when possible.

---

### Post by talrasha on 2007-02-08
I did but it's very slow coz I only have dial-up connection here... Right now I'm using Windows for browsing the net, that's why I can't fully switched my desktop to Ubuntu *nix.

Is there a way in Synaptic that I can install my downloaded file "make-3.81.tar.gz"???

---

### Post by tkjacobsen on 2007-02-08
It would be better if you downloaded the official ubuntu .deb package of make. Can be found here: [http://packages.ubuntu.com/dapper/devel/make](http://packages.ubuntu.com/dapper/devel/make)

Just select your architecture (probably i386) and afterwards a mirror.. Then inside ubuntu you can just double click on the package and gdebi will install it for you.

This is probably not the only package you need to compile your driver, you will assumably also need a compiler, which also can be found on packages.ubuntu.com

---

### Post by talrasha on 2007-02-08
Wow!!
that's what I exactly need!

Thanks a lot bro!:) 
I'll be posting here if I already installed my modem.

---

