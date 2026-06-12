---
title: "VBox in Karmic?"
date: 2009-09-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by running_rabbit07 on 2009-09-10
In Karmic's repo will there be VBox 3.0 or will it still be the older version used in jaunty?

Thanx.

---

### Post by bodhi.zazen on 2009-09-10
Moved to [Karmic Koala Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=359")

---

### Post by dinxter on 2009-09-10
current is,
$ apt-show-versions virtualbox-ose
virtualbox-ose/karmic uptodate 3.0.4-dfsg-1ubuntu1

so it'll be at least that version

---

### Post by running_rabbit07 on 2009-09-10
> **bodhi.zazen said:**
> Moved to [Karmic Koala Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=359")
 
Thanx!

> **dinxter said:**
> current is,
$ apt-show-versions virtualbox-ose
virtualbox-ose/karmic uptodate 3.0.4-dfsg-1ubuntu1

so it'll be at least that version

Awesome!

---

### Post by Sophont on 2009-09-10
Would be strange if they used a newer version as 3.0.4 is the most recent by Sun. :-)

Yup - have it installed on my Karmic laptop and it runs a VM with another Karmic. :-)

Only used it a few times - but so far without problems.

---

### Post by running_rabbit07 on 2009-09-10
I am using 3.0.6 which is the newest update.

---

### Post by inportb on 2009-09-10
indeed. the latest version is 3.0.6.

---

### Post by juancarlospaco on 2009-09-10
**[COLOR="Blue"]I can't find KVM on Karmic oficial repos!![/COLOR]**
:(

---

### Post by inportb on 2009-09-10
> **juancarlospaco said:**
> **[COLOR="Blue"]I can't find KVM on Karmic oficial repos!![/COLOR]**
:(

qemu-kvm ftw?

---

### Post by bodhi.zazen on 2009-09-10
> **juancarlospaco said:**
> **[COLOR=Blue]I can't find KVM on Karmic oficial repos!![/COLOR]**
:(

As suggested by [inportb]("http://ubuntuforums.org/member.php?u=222428") , the name of the project has been changed to qemu-kvm

[http://packages.ubuntu.com/karmic/qemu-kvm](http://packages.ubuntu.com/karmic/qemu-kvm)

---

### Post by pulpo69 on 2009-09-11
i don't nothing about virtualisatin. if i install virtual box (in karmic),
i can ran windows-programs within karmic?
i have vista 64bit inone partition (came preinstalled with the computer).
can i directly with vbox access this windows partitin and run a windows program?

---

### Post by novafluxx on 2009-09-11
Short Answer: No

Long Answer: Maybe... you CAN use a raw HDD/partition in virtualbox, but I do not know how to do it, and seeing as this wouldn't be a fresh install, Windows may not work in VBox without being installed in VB first.

So you're better off just going with the short answer, unless you wanna experiment and have a learning process!

---

### Post by pulpo69 on 2009-09-11
so what other possibilities are, running windows programs within karmic and not using wine?

---

### Post by inportb on 2009-09-11
> **novafluxx said:**
> Short Answer: No

Long Answer: Maybe... you CAN use a raw HDD/partition in virtualbox, but I do not know how to do it, and seeing as this wouldn't be a fresh install, Windows may not work in VBox without being installed in VB first.

So you're better off just going with the short answer, unless you wanna experiment and have a learning process!

I think there's a good chance that it'd work, with some glitches. Windows would most likely also detect a drastic hardware profile change and request reactivation. If you're good with Windows, you might just be able to fix it all. I've tried installing first in Vbox, then booting the physical disk directly on bare metal. The reverse might be similar.

> **pulpo69 said:**
> so what other possibilities are, running windows programs within karmic and not using wine?

What's wrong with using a virtual disk?

---

### Post by andrewabc on 2009-09-11
Any news on if newly released 3.0.6 will be included? Anyone gonna file a Feature Freeze exception to try to get it in?

Debian has 3.0.6, but only 3.0.4 guest additions.

[http://packages.debian.org/sid/virtualbox-ose](http://packages.debian.org/sid/virtualbox-ose)
[http://packages.ubuntu.com/karmic/virtualbox-ose](http://packages.ubuntu.com/karmic/virtualbox-ose)

---

### Post by xebian on 2009-09-12
> **pulpo69 said:**
> so what other possibilities are, running windows programs within karmic and not using wine?

You can run VBox as host in Karmic and then install Windows as guest in a virtual disk..

I haven't done it yet but I've seen how2s about running an installed windows in a separate partition.  AFAIK you will have problems later when you run it as a stand-alone session. It's well covered in the VBox docs.

---

