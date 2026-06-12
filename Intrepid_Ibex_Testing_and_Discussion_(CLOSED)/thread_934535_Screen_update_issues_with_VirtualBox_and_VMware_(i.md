---
title: "Screen update issues with VirtualBox and VMware (intel driver specific?)"
date: 2008-09-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lewiz on 2008-09-30
Hi guys

I use both VirtualBox and VMware on 8.04.1 and 8.10 on exactly the same hardware

When using VirtualBox/VMware on 8.10 I find that frequently the "display" doesn't get updated until I focus another window and then give focus back to VirtualBox/VMware

I've not got a root cause here, but the major difference that I am aware of is the newer intel driver in 8.10

Can anybody with 8.10, VirtualBox/VMware and an Intel X3100 confirm if they have any issues

---

### Post by ThePhantom on 2008-10-11
I also encountered these problems on X3100 after upgrading to Intrepid. 3D performance has also dropped to about 40% of the speed it had in Hardy.

---

### Post by Rumo on 2008-10-11
I can confirm this too, as well as several other people on this bug report: [https://bugs.launchpad.net/bugs/275285](https://bugs.launchpad.net/bugs/275285)

---

### Post by ThePhantom on 2008-10-12
> **Rumo said:**
> I can confirm this too, as well as several other people on this bug report: [https://bugs.launchpad.net/bugs/275285](https://bugs.launchpad.net/bugs/275285)
Thanks for that link. Setting FramebufferCompression to false fixes the problem with vmware (see [http://bugs.freedesktop.org/show_bug.cgi?id=16257#c6](http://bugs.freedesktop.org/show_bug.cgi?id=16257#c6)).

I'm still getting worse 3D performance than in Hardy, but otherwise it seems to work pretty well.

---

