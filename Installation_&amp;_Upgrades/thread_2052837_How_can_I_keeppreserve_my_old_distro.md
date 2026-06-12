---
title: "How can I keep/preserve my old distro?"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by jg1 on 2012-09-04
I have a V Old (Pentium3) Packard Bell with 127MB RAM, 8GB+4GB IDE disks, floppy disk + CD/DVD -R/W drive.  This ran a very acceptable Xubuntu system 7.10 Gutsy which I managed to destroy yesterday.  Reloading from the Alternate CD was successful but unable to load various packages not on the CD as the repositories are no longer available.  Fortunately I've managed to install Xubuntu Hardy 8.04.  This seems to be OK but still have to explore it fully.

Problem now is how to preserve this system as later dstros won't even load on the system - let alone install!

Is it possible to download a "complete" copy of the Gutsy/Hardy distro that I can use as an archive once the repositories are no longer available?

Is it possible to take an "image" copy of my hard disks on another device (eg DVD or USB HDD) so I could restore the image using a live CD (eg an old Knoppix CD) in the event of a future failure?

I've explored some of the other distros (DSL, Vector, Puppy, Slackware) and while they seem to run, they are beyond my technical knowledge at the moment.  Is there a good guide for numpties that would help me to build a workable installation including my favorite apps (eg abiword, epiphany, etc).

Although I'm a Linux devotee and have been using Ubuntu for the last couple of years, I still regard myself as a newbie as I am dependent on a GUI for most activities and haven't tried compiling from source code.  Thus I'll need simple step-by-step command-line instrns for anything but the simplest of operations.  Please can someone give me a steer?
Tks
jg1

---

### Post by dino99 on 2012-09-04
with old and no more maintained distro, you still can download their cd:
[http://old-releases.ubuntu.com/releases/7.10/](http://old-releases.ubuntu.com/releases/7.10/)

but of course there is no more available updates.

maybe you should try to upgrade/change that hardware with refurbished or users selling on the net.

---

### Post by opensshd on 2012-09-04
Perhaps APTonCD would be a good solution here.

[https://launchpad.net/aptoncd](https://launchpad.net/aptoncd)

Fairly easy to use graphical user interface. Works like a local repo. Can backup/deploy all your packages in a few simple steps.

---

### Post by jg1 on 2012-09-04
> **opensshd said:**
> Perhaps APTonCD would be a good solution here.

[https://launchpad.net/aptoncd](https://launchpad.net/aptoncd)

Fairly easy to use graphical user interface. Works like a local repo. Can backup/deploy all your packages in a few simple steps.

Hi, Guys
Tks for your quick response.  Dino99 has the best idea but I don't get an IT budget like the rest of the family so I have to make do with kit others have finished with.  They've all just bought Mac's and iPad's so that should be interesting in 2-3 years time!
In the meantime the APTonCD/DVD looks brilliant - the answer to the maiden's prayer.  Thank you Opensshd!  I also run a netbook and a "big" laptop with secure carbon copies of Precise 12.04 but it's hard trying keeping them in step software-wise.  It looks as though it'll solve that problem too.:lolflag:
I'll give it a go and report back later.
Tks again
jg1

---

### Post by Frogs Hair on 2012-09-04
I discovered this distro as a result of your thread . [http://www.slitaz.org/en/](http://www.slitaz.org/en/)

---

### Post by kurt18947 on 2012-09-04
> **Frogs Hair said:**
> I discovered this distro as a result of your thread . [http://www.slitaz.org/en/](http://www.slitaz.org/en/)

Puppy might be another possibility.  I got it to boot on a system older than the O.P.s with 64 MB. RAM.  It would boot but that was about all.

---

### Post by jg1 on 2012-09-05
> **Frogs Hair said:**
> I discovered this distro as a result of your thread . [http://www.slitaz.org/en/](http://www.slitaz.org/en/)

Thanks for the tip, Frogs Hair!  This is new to me.  I've made myself a CD and hope to try it in the next day or two.  Nice that one can download the whole distro, too.  Makes me feel less nervous.

Meanwhile, back at the ranch, the APTonCD looks like a winner.  It's pretty straightforward to use (with the man pages in one hand and the terminal/keyboard in the other!).  It also means I can stick with Ubuntu.  Hardy seems to work OK on the old machine but it's a bit slower than Gutsy was.  One also has to stick to the lightweight Apps offered by Xubuntu.

I did try Puppy.  It loaded OK for me but configuring it after install looked like it was going to need a lot of intellectual effort to get to grips with it.  I did use an old version a couple of years ago before I installed Gutsy.  That worked OK but I wasn't enamoured of the GUI.

Thanks everyone who's contributed here.  Your efforts are much appreciated.
vbw
jg1

---

