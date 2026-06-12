---
title: "Insane number of wakeups per second?"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by stephantom on 2008-10-05
Hello community,

This probably isn't realted to Intrepid directly, but I'm posting it here anyways because this happens on a testing system.

[center][img]http://img3.imagebanana.com/img/6jq0wda3/Screenshot.png[/img][/center]

I've got 15 - 40 thousand(!) wakeups per second - with no apparent way to reduce this. I've already followed all powertop recommendations and have nothing more than Firefox (at the latest [ibex] version) and a gnome-terminal (with powertop in it) running that the time of measuring.
The top cause should be [this bug](https://bugs.launchpad.net/ubuntu/+bug/194489), the touchpad. But that still leaves **a lot** to explain.
At least CPU scaling is working properly. That's a plus, I guess.

Any ideas how I could track those hidden interrupts/wakeups down?
I hear 200-500 wakeups pass as good.

Thanks,
stephantom

---

### Post by aldeby on 2008-10-05
Please try without firefox and not moving the mouse, you should first see how many wakeups you get at idle. 

Actually, CPU scaling is not working properly. 
You should have an **avg residency** at the lowest state above 90% at least for 20 secs for a sound power profile. The fact that this is not met in you case denote there are some problems with programs keeping the CPU busy. Firefox and some plugins (flash/javascript routines) can be the cause.

Try closing every program listed in "top causes" one after the other to figure out which one actually makes the difference.

---

### Post by jfernyhough on 2008-10-05
The touchpad wakeups are nothing to do with Ubuntu, it's a problem with synaptics touchpad drivers. There is a bug report on launchpad anyway, but it doesn't look like it's being touched.

It is quite annoying - my Acer goes from 100 wakeups to 600 when I move the pointer, and my Eee goes from 20 to 600 - with nothing else running. It's quite noticeable. The same problem exists in Fedora 10 Beta (Omega 10) too.

OK, so I've now just read the first post properly (I went off the content from the second which misses the point). It looks like an ACPI foulup - until the last gnome-power-manager update my laptop was apparently using 1000V and 20000W, or thereabouts.

What does gnome-power-manager report? Battery life etc.? Have you updated to 2.6.27-5?

Can you give some more information about your system? uname -a, for example.

---

