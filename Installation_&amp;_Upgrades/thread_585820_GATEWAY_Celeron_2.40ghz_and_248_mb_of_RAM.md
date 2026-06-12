---
title: "GATEWAY Celeron 2.40ghz and 248 mb of RAM"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Octavgmail.come on 2007-10-21
I know this isn't the newest laptop but i can't run either the 7.04 or the 7.1 live  cd's.  Does anyone know how i can fix this problem?  I'm pretty new to Linux but i thought it was supposed to use less resources than windows? this is really starting to irritate me. I've tried everything i know, i mean the live cd doesn't even work. I've downloaded 3 different ones and they all do the same thing. any help would greatly be appreciated.

---

### Post by Pumalite on 2007-10-21
With that RAM> Xubuntu Alternate CD: [http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

---

### Post by vraknari on 2007-10-21
> **Pumalite said:**
> With that RAM> Xubuntu Alternate CD: [http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

Per the documentation found at that link, it says 128MB of RAM is the minimum needed to install from the cd.

I'm having a similar problem in that once I reach the desktop from the Live CD, my dvd drive and hard drive are constantly spinning and the system crawls to the point where it's unbearable.

I'm currently running:
Dell Latitude C840
Mobile Pentium 4 - 2.2 GHz
256MB RAM

I thought for sure I'd be able to install 7.10 without any hassles.

Are there any major differences between the Alternate CD and the Live CD?

Thanks.

---

### Post by kerry_s on 2007-10-22
> **Octavgmail.come said:**
> I know this isn't the newest laptop but i can't run either the 7.04 or the 7.1 live  cd's.  Does anyone know how i can fix this problem?  I'm pretty new to Linux but i thought it was supposed to use less resources than windows? this is really starting to irritate me. I've tried everything i know, i mean the live cd doesn't even work. I've downloaded 3 different ones and they all do the same thing. any help would greatly be appreciated.


you need to burn the iso as a image at 4x.->
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

and you should go with "Pumalite" suggestion and use xubuntu, gnome is heavy for that amount of ram.

---

### Post by kerry_s on 2007-10-22
> **vraknari said:**
> Per the documentation found at that link, it says 128MB of RAM is the minimum needed to install from the cd.

I'm having a similar problem in that once I reach the desktop from the Live CD, my dvd drive and hard drive are constantly spinning and the system crawls to the point where it's unbearable.

I'm currently running:
Dell Latitude C840
Mobile Pentium 4 - 2.2 GHz
256MB RAM

I thought for sure I'd be able to install 7.10 without any hassles.

Are there any major differences between the Alternate CD and the Live CD?

Thanks.

yes, the alternate cd does not use a gui installer, so it use way less resources to install.

---

### Post by Octavgmail.come on 2007-10-22
I burned 3 cd's 2 regular and one alternate @ 4x and even got a torrent none worked :(

---

### Post by Pumalite on 2007-10-22
Stick to a smaller distro then. (you probably have integrated graphics that reduce your 'usable' RAM). Try: DSL, Puppy, Zenwalk

---

### Post by kerry_s on 2007-10-22
> **Octavgmail.come said:**
> I burned 3 cd's 2 regular and one alternate @ 4x and even got a torrent none worked :(

are you burning it as a image? you can't just copy it.
follow the how to in my other post.
then make sure your cd is set to boot first in your bios.

---

### Post by ezsit on 2007-10-22
> Celeron 2.40ghz and 248 mb of RAM 

Get this puppy up to 512mb RAM before installing. I have 1ghz processors running ubuntu just fine, but all my machines have between 512mb and 1gb of RAM.

---

