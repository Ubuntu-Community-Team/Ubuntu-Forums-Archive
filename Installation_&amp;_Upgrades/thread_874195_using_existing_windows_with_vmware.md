---
title: "using existing windows with vmware"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by SpikeyMike on 2008-07-29
Hi, I installed vmware and configured it to boot an existing windows installation by creating a new hardware profile in windows as described in this howto:

[http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/](http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/)


it works but I have one problem, when I booted windows xp using vmware I had to reactivate it which worked ok, but when I boot windows normally it also asks me to activate it, i tried this but it tells me it has been activated too many times and if I try after this to boot xp with vmware it asks me again to activate it so im stuck in a loop, I can reactivate windows in vmware no problem and it works fine until I boot windows normally which messes it up again. when I boot windows normally i choose the vmware hardware profile as I also do when I boot with vmware, does anyone know if this correct? and do you know any way I can fix the activation problem?

Regards

Spikey

---

### Post by SpikeyMike on 2008-07-30
anyone?

---

### Post by pc80 on 2008-08-16
Not sure exactly, but I had read somewhere that you need to call up the M$ customer support to reactivate the subscription. XP has a hardware lock in which it requires you to reactivate the OS once the underlying hardware changes. When you are booting in normally, the hardware the OS is detecting is that of your (physical) computer. However, under the virtual mode, it is actually working on a virtual hardware made available to it by vmware. This is causing the OS to think that it is being run on a totally different hardware. As far as I know, the only way to solve this is to stick with one of versions, actual or virtual, to run XP on. Sucks, but I rarely use M$ on my laptop... so doesn't bother me that much...

---

