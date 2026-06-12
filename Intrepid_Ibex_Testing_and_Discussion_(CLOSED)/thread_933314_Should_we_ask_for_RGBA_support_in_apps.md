---
title: "Should we ask for RGBA support in apps?"
date: 2008-09-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-09-29
I've noticed that a couple apps (the system monitor, the terminal) already show RGBA support if you use the default, murrine-based, Human theme.

I'm somehow under the impression that adding this to apps is not too difficult, should we file some requests and ask for it in other apps?

---

### Post by plun on 2008-09-29
The main problem is a stable driver.

nVidia driver works sometimes and is broken with next version.

Example how "RGBA trashing" looks, it happens for some apps during scrolls.

[[img]http://ubuntu-pics.de/thumb/3821/rgbatrashing_U78NX6.jpg[/img]](http://ubuntu-pics.de/bild/3821/rgbatrashing_U78NX6.jpg)

Cimi tried with nVidia but no reaction...


All apps with plugins are easy to enable for example Rhythmbox

[http://www.cimitan.com/murrine/rgba-support/list](http://www.cimitan.com/murrine/rgba-support/list)

**Note 2 pages **!


Perhaps if Cimis sees this he can add his view...?  :)

---

### Post by Bou on 2008-09-29
Is this a problem with RGBA or compositing, anway? I was using a nvidia card until recently and I had corruption problems even though I wasn't using RGBA...

---

### Post by amano on 2008-09-29
> **plun said:**
> The main problem is a stable driver.

nVidia driver works sometimes and is broken with next version.

...

Cimi tried with nVidia but no reaction...



If GNOME itself as a project moved to support RGBA, nVidia would probably care more for it...

---

### Post by plun on 2008-09-29
> **Bou said:**
> Is this a problem with RGBA or compositing, anway? I was using a nvidia card until recently and I had corruption problems even though I wasn't using RGBA...

I have never seen it except with RGBA enabled..I also don't know for sure what causing this ?

MacSlows Spit&Polish spec maybe can give clues ?
[https://wiki.ubuntu.com/DesktopTeam/Specs/SpitAndPolish](https://wiki.ubuntu.com/DesktopTeam/Specs/SpitAndPolish)

Nevertheless Murrines plugins and patches works just fine..

I have never used Rhythmbox until I found the RGBA plugins.  :D

[http://www.cimitan.com/murrine/node/81](http://www.cimitan.com/murrine/node/81)

From "terrible" to great...:)

---

### Post by Arlanthir on 2008-09-29
Ibex's Murrina has RGBA support? Is it default?

---

### Post by mc4100 on 2008-09-29
Personally, I would love it. But I think it's too soon:
NVidia drivers allegedly having problems, and I know that blurring doesn't work with the Intel ones -- which makes transparent menus, etc., harder to read. Until these issues are resolved, I think we would be pushing for something that **lessens** the Desktop experience. On the other hand, promoting RGBA might make the vendors fix the problems quicker.

---

### Post by plun on 2008-09-29
> **Arlanthir said:**
> Ibex's Murrina has RGBA support? Is it default?

Yup but not for latest themes from Murrine which requires code from svn.

I am unsure what version Ubuntu choosed

[http://changelogs.ubuntu.com/changelogs/pool/main/g/gtk2-engines-murrine/gtk2-engines-murrine_0.60.1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/g/gtk2-engines-murrine/gtk2-engines-murrine_0.60.1/changelog)

from a May-svn to a upstream release, I haven't seen any release from Cimi.


@mc4100

The big dragon will use transparency a lot in Windooooze 7.... (December)

[[img]http://ubuntu-pics.de/thumb/3832/2311634559_j5y8XR.jpg[/img]](http://ubuntu-pics.de/bild/3832/2311634559_j5y8XR.jpg)    [[img]http://ubuntu-pics.de/thumb/3833/194521518_62TLOK.jpg[/img]](http://ubuntu-pics.de/bild/3833/194521518_62TLOK.jpg)


Ubuntu "blows" both a new theme and RGBA.....:(

---

### Post by Bou on 2008-09-29
> **mc4100 said:**
> and I know that blurring doesn't work with the Intel ones

Could you elaborate on that? I'm using an Intel card and I noticed that activating blurring completely messes up the screen. Is there an open bug?

> **mc4100 said:**
> which makes transparent menus, etc., harder to read

I don't think transparent menus are a good idea at all. Technically they can remain opaque while the rest of the window is translucent, right?

---

### Post by psyke83 on 2008-09-29
> **Bou said:**
> I've noticed that a couple apps (the system monitor, the terminal) already show RGBA support if you use the default, murrine-based, Human theme.

I'm somehow under the impression that adding this to apps is not too difficult, should we file some requests and ask for it in other apps?

It would be a good idea to request support, yes. However, the default themes may ship with RGBA effects disabled. The last time I talked to Kenneth Wimer, he wanted to keep it enabled, but others are concerned about stability, etc.

---

### Post by plun on 2008-09-29
> **Bou said:**
> 
I don't think transparent menus are a good idea at all. Technically they can remain opaque while the rest of the window is translucent, right?

Yup this is the "key" with RGBA that its intelligent transparency.

Example:

Latest murrine svn

Gnome-terminal , built in transparency enabled

Rhythmbox,  plugin enabled

Gedit, plugin enabled

[http://www.cimitan.com/murrine/rgba-support/list](http://www.cimitan.com/murrine/rgba-support/list)

[[img]http://ubuntu-pics.de/thumb/3843/rgba_Rr7i6s.jpg[/img]](http://ubuntu-pics.de/bild/3843/rgba_Rr7i6s.jpg)

```
sudo apt-get remove gtk2-engines-murrine

svn checkout http://svn.gnome.org/svn/murrine/trunk/ murrine

cd murrine

./autogen.sh --enable-animation

make

sudo make install
```

Have fun...:D

---

