---
title: "Palimpsest on the LiveCD?"
date: 2009-06-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ghindo on 2009-06-08
I really appreciate the Ubuntu LiveCD; not only does it allow me to install Ubuntu, but it provides a bunch of handy utilities like Gparted and Memtest.  Palimpsest (AKA gnome-disk-utility) seems like it would be an excellent inclusion for repairs and diagnostics.  However, I know that CD space is at a premium.  Has there been any discussion of including Palimpsest in the Karmic LiveCD?

---

### Post by durand on 2009-06-08
That would be cool but they need to get devicekit integrated properly first.

---

### Post by ranch hand on 2009-06-11
I may just make a LiveDVD using remastersys and include that.  You may want to try that too.

You can include anything that you want but it doesn't take but a little to put the size over what will fit an a CD.

---

### Post by blueridgedog on 2009-06-13
I can't seem to find either palimpsest or gnome-disk-utility in the repos...where did you get it?  I loved it when I tested Fedora 11.

---

### Post by inportb on 2009-06-13
Hmm...

> $ apt-cache search palimpsest
gnome-disk-utility - manage and configure disk drives and media

---

### Post by blueridgedog on 2009-06-13
```
$ sudo apt-get install gnome-disk-utility
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-disk-utility
$ 
```

What repo are you seeing it in?

---

### Post by inportb on 2009-06-13
It's apparently in [universe]("http://packages.ubuntu.com/karmic/gnome-disk-utility").

Incidentally... it'd be awesome if there were a comparable Qt/KDE disk utility =D

---

### Post by Regenweald on 2009-06-13
> **blueridgedog said:**
> I can't seem to find either palimpsest or gnome-disk-utility in the repos...where did you get it?  I loved it when I tested Fedora 11.

I was just in 'Add Remove' and happened across it. But then i always activate all the repos after i install :) Will try it later in the cycle.

---

### Post by Gourgi on 2009-06-13
Palimpsest :guitar:
I've just installed it and i'm just shocked by its capabilities and _simplicity_. Good work from the fedora devs!
Definitely keeping it installed :D

---

### Post by ghindo on 2009-06-13
> **Gourgi said:**
> Palimpsest :guitar:
I've just installed it and i'm just shocked by its capabilities and _simplicity_. Good work from the fedora devs!
Definitely keeping it installed :DIt even sounds like the UI might be [simplified further]("http://people.freedesktop.org/~david/grid-3.png").

---

### Post by xebian on 2009-06-13
> **inportb said:**
> It's apparently in [universe]("http://packages.ubuntu.com/karmic/gnome-disk-utility").

Incidentally... it'd be awesome if there were a comparable Qt/KDE disk utility =D

There is KwikDisk and inside it is KdiskFree, and KpartitionManager

---

### Post by blueridgedog on 2009-06-14
> **inportb said:**
> It's apparently in [universe]("http://packages.ubuntu.com/karmic/gnome-disk-utility").

Incidentally... it'd be awesome if there were a comparable Qt/KDE disk utility =D

It appears that it is only in Karmic's univers repo, as I have univers enabled as well, but it is not an option.

---

### Post by blueridgedog on 2009-06-14
I downloaded the deb, and found out that I need a newer library.  How can I tell dpkg or apt-get to force the upgrade of the library?

```
# dpkg -i gnome-disk-utility_0.3-0ubuntu2_i386.deb 
Selecting previously deselected package gnome-disk-utility.
(Reading database ... 196546 files and directories currently installed.)
Unpacking gnome-disk-utility (from gnome-disk-utility_0.3-0ubuntu2_i386.deb) ...
dpkg: dependency problems prevent configuration of gnome-disk-utility:
 [B]gnome-disk-utility depends on libdbus-glib-1-2 (>= 0.78); however:
  Version of libdbus-glib-1-2 on system is 0.76-1.[/B]
```

---

### Post by blueridgedog on 2009-06-14
OK, I forced the install of the karmic package for the library I was missing, and then it revealed yet another dependency that was missing, so I think i will give up until I install KK when released.
```

# dpkg -i gnome-disk-utility_0.3-0ubuntu2_i386.deb 
Selecting previously deselected package gnome-disk-utility.
(Reading database ... 196548 files and directories currently installed.)
Unpacking gnome-disk-utility (from gnome-disk-utility_0.3-0ubuntu2_i386.deb) ...
dpkg: dependency problems prevent configuration of gnome-disk-utility:
 gnome-disk-utility depends on libgdu-gtk0 (>= 0.3-0ubuntu1); however:
  Package libgdu-gtk0 is not installed.
```

---

### Post by ranch hand on 2009-06-14
There are quite a few false positives under Fedora 11 and several recient bugs files for RH.

I don't know anything about it but it would be nice to have more accesable info on the HDDs (I have 5).

---

### Post by inportb on 2009-06-14
@blueridgedog: well this *is* the Karmic development forum ;)
I don't think 8.10 has devicekit integration or some of the other prerequisites. But Palimpsest is pretty neat.

---

### Post by blueridgedog on 2009-06-14
> **inportb said:**
> @blueridgedog: well this *is* the Karmic development forum ;)
I don't think 8.10 has devicekit integration or some of the other prerequisites. But Palimpsest is pretty neat.

Ha...I didn't even notice (I found the thread by searching for palimpsest).  My goof.

---

### Post by inportb on 2009-06-15
No worries... if it gets on the live CD anyone could use it :)

> **xebian said:**
> There is KwikDisk and inside it is KdiskFree, and KpartitionManager

Good call; I'll have to check this out later.

---

