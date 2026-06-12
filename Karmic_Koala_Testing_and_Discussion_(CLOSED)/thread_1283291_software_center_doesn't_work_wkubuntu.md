---
title: "software center doesn't work w/kubuntu"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2009-10-05
is this intentional?  It's always been my understanding that if you don't like kpackagekit (which I don't) you can use anything else just by installing it.  I have ubuntu-desktop and kubuntu-desktop both installed.  

I can start it, browse, read descriptions, and see the images but clicking 'install' does nothing.  I looked behind the viewer to make sure my admin login wasn't hiding but it doesn't bring it up at all.  nothing happens at all.  it doesn't lock up, still can browse applications but install doesn't do anything.

Is this intentional?  Is software center for ubuntu/gnome only?  or does this qualify as a bug?

am up to date on all updates.

EDIT:  also running from terminal reports no errors.

---

### Post by mpt on 2009-10-05
It’s not intentional. Please report a bug.

Keep in mind, though, that it’s not necessarily because you’re running Kubuntu; the cause might be something else.

---

### Post by slakkie on 2009-10-05
Could be this bug:

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/443994](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/443994)

---

### Post by buzzmandt on 2009-10-05
nope, not same bug, I get no crash and have no errors in cli

if this were ubuntu it'd be ubuntu-bug software-center
kubuntu-bug doesn't work. what's the commande for kubuntu bug? or do i still file it as ubuntu-bug?

---

### Post by slakkie on 2009-10-06
> **buzzmandt said:**
> nope, not same bug, I get no crash and have no errors in cli

if this were ubuntu it'd be ubuntu-bug software-center
kubuntu-bug doesn't work. what's the commande for kubuntu bug? or do i still file it as ubuntu-bug?

Don't be fooled by Kubuntu/xubuntu/edubuntu, they all use the exact same tools, so use ubuntu-bug.

See it like this: You are running Ubuntu with a DE and they just branded it Kubuntu. If you install a Ubuntu cli system or server you can convert it into any kind of desktop machine. Do `aptitude search tu-desktop` and see how many meta-packages there are just to install some kind of desktop system om Ubuntu. Just a name, nothing more. You are using Ubuntu.

---

### Post by zoomy942 on 2009-10-06
its a bug thats been reported and confirmed.

---

### Post by slakkie on 2009-10-06
There is a new package coming your way.

---

### Post by Falc7 on 2009-10-06
I also have the same problem

---

