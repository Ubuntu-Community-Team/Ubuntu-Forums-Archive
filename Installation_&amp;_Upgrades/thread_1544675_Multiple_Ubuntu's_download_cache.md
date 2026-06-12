---
title: "Multiple Ubuntu's download cache?"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by wirefly on 2010-08-02
Hi Guys and Gals,

Here at home I have several Ubuntu installations, mine, the kids computers and a couple of laptops.  What I'm looking for is a solution or a pointer in the right direction to setup on our local Ubuntu server a sort of cache.

Each day each Ubuntu on the network, checks for updates and downloads, and installs.  What I'm looking for is a way for one machine to download the update and then the others to download from the local resource.

A sort of local cache to try and minimise everyone downloading straight from the net for pretty much the same updates.

I did a emerge cache many years ago when I was using Gentoo, so I'm wondering what I can use/do here with Ubuntu as we are all loving this distro now.

Thanks everyone!

Damian
:popcorn:

---

### Post by mikewhatever on 2010-08-02
Here you go.
[http://www.packtpub.com/article/create-local-ubuntu-repository-using-apt-mirror-apt-cacher](http://www.packtpub.com/article/create-local-ubuntu-repository-using-apt-mirror-apt-cacher)
You'll probably want the second way of using Apt-cacher.

---

### Post by wirefly on 2010-08-03
Thanks Mikewhatever

That second method is exactly what I'm looking for, and exactly the way I had things setup with Gentoo and its portage!

Thankyou very much!  :D

---

