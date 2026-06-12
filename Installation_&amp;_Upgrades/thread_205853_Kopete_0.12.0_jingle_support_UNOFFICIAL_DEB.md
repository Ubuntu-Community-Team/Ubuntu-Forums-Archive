---
title: "Kopete 0.12.0 jingle support UNOFFICIAL DEB"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by Ranma on 2006-06-29
Hi to all!

A few days ago I realized that the new Kopete 0.12.0 was out and the most important feature (at least for me) was the Google Talk voice support. Knowing that compiling and installing from source could break Kdenetwork package I looked around the deb file to install and I ended in this post 

[http://www.ubuntuforums.org/showthread.php?t=190273&highlight=kopete+0.12.0](http://www.ubuntuforums.org/showthread.php?t=190273&highlight=kopete+0.12.0)


wich also explains if you are going to create your own deb file how to number and name it to avoid breaking kdenetwork.

The deb file contained in that post works great however it seems that the configure parameter to enable jingle support was missing.

That's why taking the ideas to avoid breaking kdenetwork i decided to create my own deb file with jingle support compiled in.

The dependencies to make jingle work are:
speex 
expat 
and oRTP [http://www.linphone.org/ortp/sources/](http://www.linphone.org/ortp/sources/)  only version 0.7.1 will work

more info of the dependencies are in: [http://wiki.kde.org/tiki-index.php?page=Kopete%20Jabber%20Jingle](http://wiki.kde.org/tiki-index.php?page=Kopete%20Jabber%20Jingle)

And finally the link to deb file: [http://www.tetsuo.com.ar/~ranma/kopete_3.5.3-ubuntu0_i386.deb](http://www.tetsuo.com.ar/~ranma/kopete_3.5.3-ubuntu0_i386.deb)

**REMEMBER THAT THIS IS AN UNOFFICIAL DEB FILE** 

Enjoy!!!

Ranma

---

### Post by sinanimam on 2006-10-30
Hi to all!

Does anyone have the Kopete package for Edgy Eft, but built with Jingle support? I don't want to download and install so many development packages, and thought someone most probably already has built a package for himself. If so, please share.

---

### Post by phyzome on 2006-11-12
> **Ranma said:**
> The dependencies to make jingle work are:
speex 
expat 
and oRTP [http://www.linphone.org/ortp/sources/](http://www.linphone.org/ortp/sources/)  only version 0.7.1 will work

Okay, so what is this oRTP link? It gives a 404 when I try to visit it. Is this something to put in /etc/apt/sources.list? If so, what is the section and type?

---

