---
title: "Gnome doesn't mount encrypted USB stick in Karmic beta"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by uaaquarius on 2009-10-04
Hi all!

I've installed Karmic **beta** and now Gnome does not asks for pass-phrase when I insert my encrypted USB stick :confused: This works fine on my two Jaunty boxes and other distros.
I suspect this is a bug (regression) in Karmic. If this is the case I would post a bug.
But maybe this is the result of some change in default Gnome configuration. And all I need to do is just a little modification in settings...
What do you think of this?

Thanks in advance

---

### Post by sedawk on 2009-10-05
Is the stick listed in "Places". E.g. "Removable Media"?


You can check if everything works fine from the
command line:
* insert stick and wait 10 seconds
* check address of new stick with "dmesg"
* "uncrypt it" with "sudo cryptsetup luksOpen /dev/sdX1 testing"
* Mount it, e.g. "sudo mount /dev/mapper/testing /mnt"
  (You might have to create directory /mnt first ...)

---

### Post by uaaquarius on 2009-10-05
Thanks for your answers, sedawk.

> **sedawk said:**
> Is the stick listed in "Places". E.g. "Removable Media"?


No, it is not listed. On contrast not encrypted USB stick is mounted fine and is listed in "Places".

> **sedawk said:**
> You can check if everything works fine from the
command line:
* insert stick and wait 10 seconds
* check address of new stick with "dmesg"
* "uncrypt it" with "sudo cryptsetup luksOpen /dev/sdX1 testing"
* Mount it, e.g. "sudo mount /dev/mapper/testing /mnt"
  (You might have to create directory /mnt first ...)

That's exactly how I mount it. I just skip steps 1 and 2 because I know the exact device name :)

I suspect this is a bug #-o

---

