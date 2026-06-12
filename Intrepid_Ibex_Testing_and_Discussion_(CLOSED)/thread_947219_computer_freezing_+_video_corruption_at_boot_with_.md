---
title: "computer freezing + video corruption at boot with kernel 2.27.x + dell lattitude n830"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by nIRV on 2008-10-14
Is anybody experience computer freezing accompanied by video corruption at boot time (see attached screenshot) using the kernel 2.6.27.x series? The only way to regain control of the laptop is by doing a hard reset. It randomly happens when booting (I'd say +/- 1 time per 3 boots)

The problem appeared with the first 2.6.27.2 kernel image and is still happening with latest 2.6.27.7 kernel. I was hoping it'd be fixed during development process but I'm getting worried as release day approaches.

Has a launchpad bug been created for this?

---

### Post by dro0g on 2008-10-14
> **nIRV said:**
> Is anybody experience computer freezing accompanied by video corruption at boot time 

Yes I've been seeing the same thing on a Latitude D630. The boot sequence reads "Loading Hardware Drivers" just before it happens. I've been avoiding it by booting to recovery mode and then booting normally, though it hasn't happened to me since the latest updates.

---

### Post by nIRV on 2008-10-14
> **dro0g said:**
> Yes I've been seeing the same thing on a Latitude D630. The boot sequence reads "Loading Hardware Drivers" just before it happens. I've been avoiding it by booting to recovery mode and then booting normally, though it hasn't happened to me since the latest updates.

'since the latest updates' as in 2 days ago or as in 1 month ago? :)

---

### Post by yelo3 on 2008-10-15
OMG! this is my problem too, though I have an HP! I've had it since the first "release" of intrepid (just when there was the change from the herdy kernel to the intrepid one)
Please add your information here [https://bugs.launchpad.net/bugs/279189](https://bugs.launchpad.net/bugs/279189)

---

### Post by yelo3 on 2008-10-15
Have you done a clean beta install? maybe this fixes the problem... I will try with a clean install when final is released

---

### Post by jerrylamos on 2008-10-15
IBM Thinkpad R31 freezes on Beta during boot when the first Gnome Ubuntu desktop should load.  Xubuntu & Kubuntu Beta work O.K.

The problem isn't the kernel, it's compiz.  As far as I can tell install doesn't use compiz so Beta does install O.K.  Then if I boot in rescue mode to a command line, sudo apt-get remove compiz & compiz-core, sudo startx resumes boot and Intrepid runs O.K., without compiz eye candy of course.

CD Live is a bit tricky by doing Ctrl-Alt-F1 as Gnome is loading, then sudo apt-get remove compiz & compiz-core, sudo startx.

So long as Alpha 5 ISN'T UPDATED! it works, not because of the kernel changes but because of compiz changes which occurred before Alpha 6 and are still there on Beta.  Launchpad bug is 277344.

jerry

---

### Post by dro0g on 2008-10-15
> **nIRV said:**
> 'since the latest updates' as in 2 days ago or as in 1 month ago? :)

I've rebooted a few times over the past 2-3 days and haven't had it happen. It previously wasn't consistent (it didn't happen every time) but it seemed to happen more frequently when warm booting.

---

