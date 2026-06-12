---
title: "Will Karmic be getting X-Server 1.6.4?"
date: 2009-09-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by X10N on 2009-09-06
The plan says 1.6.3, but is there any chance of the newer version showing up?

---

### Post by zipperback on 2009-09-06
I have Karmic 64bit installed and just checked synaptic.

xorg installed version 1:7.4+3ubuntu5 X.Org Window System
xserver-xorg-core 2:1.6.3-1ubuntu5 Xorg X server - core server


That's what I currently have with the alpha 5 release

- zipperback
:popcorn:

---

### Post by X10N on 2009-09-06
> **zipperback said:**
> I have Karmic 64bit installed and just checked synaptic.

xorg installed version 1:7.4+3ubuntu5 X.Org Window System
xserver-xorg-core 2:1.6.3-1ubuntu5 Xorg X server - core server


That's what I currently have with the alpha 5 release

- zipperback
:popcorn:

I have x86 Karmic installed, and you haven't answered my question!

You may as well have said my blood is red.... >___<

---

### Post by cdEWoozy on 2009-09-07
Bryce Harrington [wrote](https://lists.ubuntu.com/archives/ubuntu-x/2009-August/000602.html):

> Quick note that after discussing this with a bunch of people, the decision was finalized today that due to the lateness of xserver 1.7 **we will instead be targetting 1.6.3 in Karmic**.  Timo has done the merge for this already today.  Going forward we anticipate pulling patches in from the 1.7 tree as makes most sense.

---

### Post by VMC on 2009-09-07
I have x86 and here is what is installed on my karmic :
```
$ aptitude show xserver-xorg
Package: xserver-xorg
State: installed
Automatically installed: no
Version: 1:7.4+3ubuntu5
```

---

### Post by taavikko on 2009-09-08
> **VMC said:**
> I have x86 and here is what is installed on my karmic :
```
$ aptitude show xserver-xorg
Package: xserver-xorg
State: installed
Automatically installed: no
Version: 1:7.4+3ubuntu5
```

just a clarification, xserver-xorg-core is what provides the X server
```
Package: xserver-xorg-core
State: installed
Automatically installed: yes
Version: 2:1.6.3+git20090805+server-1.6-branch.f274e595-0ubuntu0sarvatt
```

Though IMHO naming scheme should be simplified..

---

### Post by zipperback on 2009-09-09
> **X10N said:**
> I have x86 Karmic installed, and you haven't answered my question!

You may as well have said my blood is red.... >___<


hmmm... Actually I did answer you.

I told you what the X Server was in Karmic by default.

xserver-xorg-core 2:1.6.3-1ubuntu5 Xorg X server - core server

That's what you asked about RIGHT?

- zipperback

---

### Post by dino99 on 2009-09-09
did you get the good answer for 25$ ?

seem that question ask about 1.6.4 in close future

---

