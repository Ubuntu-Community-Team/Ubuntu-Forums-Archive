---
title: "Gnome Do in Intrepid"
date: 2008-08-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jblackhall on 2008-08-22
Does anyone know if they plan on updating Gnome Do in Intrepid more than they already have?  The version in Hardy is 0.4.0.1.  The current version [listed for Intrepid]("https://edge.launchpad.net/ubuntu/intrepid/+source/gnome-do") is 0.4.2.0.  0.5 came out in early June and it [offered a lot of nice features]("http://blog.davebsd.com/2008/06/09/gnome-do-05/").  The current version in trunk is 0.5.99.  Doesn't it seem like Intrepid should be upgraded to at least 0.5.0?  That's the version I've been using from GetDeb for a while now and it appears to be working just great.  Anyone know the proper way to request this?  I know feature freeze is coming up quickly.  Seems from the numbering like 0.6 will probably be out very soon too, so I feel like we should at least get 0.5 in the Intrepid repos.  Especialy for such a great app!

---

### Post by RAOF on 2008-08-22
I'm on it.  0.5 can't be sanely packaged in Ubuntu or Debian - it has no way to load local plugins, so we can't ship a plugins package, and you're stuck hoping that we never make an ABI change on the server side for the 1.5 year duration of Intrepid's desktop support.

The 0.6 release candidates support local plugins, and 0.6 should be released this weekend.  And hit Intrepid soon after.

It's a bit of a pity that the ShowCase UI won't be included in that release.  It's pretty shiny!

---

### Post by plun on 2008-08-22
> **RAOF said:**
> I'm on it.  0.5 can't be sanely packaged in Ubuntu or Debian - it has no way to load local plugins, so we can't ship a plugins package, and you're stuck hoping that we never make an ABI change on the server side for the 1.5 year duration of Intrepid's desktop support.


Well, "tecnical details" but why ?  

The [ppa]("https://launchpad.net/~do-core/+archive") works great.

---

### Post by zekopeko on 2008-08-22
> **RAOF said:**
> I'm on it.  0.5 can't be sanely packaged in Ubuntu or Debian - it has no way to load local plugins, so we can't ship a plugins package, and you're stuck hoping that we never make an ABI change on the server side for the 1.5 year duration of Intrepid's desktop support.

The 0.6 release candidates support local plugins, and 0.6 should be released this weekend.  And hit Intrepid soon after.

It's a bit of a pity that the ShowCase UI won't be included in that release.  It's pretty shiny!

uuuuuuuuu, shinyyyyyyy!!! how do i get that UI for Do? Is it in ppa or...?

---

### Post by jblackhall on 2008-08-22
> **RAOF said:**
> I'm on it.  0.5 can't be sanely packaged in Ubuntu or Debian - it has no way to load local plugins, so we can't ship a plugins package, and you're stuck hoping that we never make an ABI change on the server side for the 1.5 year duration of Intrepid's desktop support.

The 0.6 release candidates support local plugins, and 0.6 should be released this weekend.  And hit Intrepid soon after.

It's a bit of a pity that the ShowCase UI won't be included in that release.  It's pretty shiny!

Great, thanks for the quick response.  I was also a little confused when you said that 0.5 couldn't be packaged properly, considering it's the version I grabbed from GetDeb.  But tbh, i'm looking forward to 0.6 anyways, so it works out for the best.  Plus I heard somewhere that there's automatic plugin upgrades, which will be nice.

And you're right, that ShowCase UI does look nice and shiny.  I've been really impressed with the amount of good work that has gone into this project recently.  It keeps getting more and more useful all the time.  Alright, I'll just sit back and wait for the next release :popcorn:

---

### Post by plun on 2008-08-22
This is maybe also useful....

[https://wiki.ubuntu.com/GnomeDo/](https://wiki.ubuntu.com/GnomeDo/)


Just to remember that you have Gnome-do....:)

---

### Post by conundrumx on 2008-08-22
> **plun said:**
> Well, "tecnical details" but why ?  

The [ppa]("https://launchpad.net/~do-core/+archive") works great.

0.5 depends on Do's own repositories for plugins, where as the distros would rather not release software to users which they can't support themselves.  With 0.6 it will be possible for a plugin package to be included, thus easing their worries.

To those curious about the Showcase skin, it will probably be in 0.7, and is currently a work in progress.  You can catch most relevant information on do.davebsd.org.

---

### Post by twisted_steel on 2008-08-24
Version 0.6 has hit the PPA:

[http://jassmith.wordpress.com/2008/08/23/gnome-do-060-talk-to-your-kids-about-06-before-somebody-else-does/](http://jassmith.wordpress.com/2008/08/23/gnome-do-060-talk-to-your-kids-about-06-before-somebody-else-does/)

---

### Post by go7Ul1ai on 2008-08-24
> **twisted_steel said:**
> Version 0.6 has hit the PPA:

[http://jassmith.wordpress.com/2008/08/23/gnome-do-060-talk-to-your-kids-about-06-before-somebody-else-does/](http://jassmith.wordpress.com/2008/08/23/gnome-do-060-talk-to-your-kids-about-06-before-somebody-else-does/)

Pretty old news :P

---

### Post by zekopeko on 2008-08-24
soooo...like... how can i get that fancy Showcase UI for gnome-do?

---

### Post by twisted_steel on 2008-08-24
> **lee.jarratt said:**
> Pretty old news :P

Haha, I guess I'll have to post instantly next time :-D

---

### Post by RAOF on 2008-08-24
> **zekopeko said:**
> soooo...like... how can i get that fancy Showcase UI for gnome-do?

By waiting 'till it's stable, and included in a release?  :)

Alternatively, by building from the bzr branch on Launchpad.  It's not finished, though, and since Do grabs the keyboard when you summon it, bugs can make your life really difficult!

---

