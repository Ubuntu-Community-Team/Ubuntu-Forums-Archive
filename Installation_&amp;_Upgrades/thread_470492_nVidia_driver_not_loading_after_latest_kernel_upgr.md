---
title: "nVidia driver not loading after latest kernel upgrade"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by Fibonacci on 2007-06-11
Hello,

I recently installed kernel 2.6.20-16, and only a couple of days ago I got it to boot without irqpoll. Just as I was done with that, I updated linux-headers-2.6.20-16-generic via update-manager; after rebooting into 20-16, the X server failed to start, with an error message saying that NVIDIA modules were not loaded (cannot remember the exact text of the message). Following a suggestion on this same forum, I apt-get removed nvidia-glx and apt-get installed nvidia-glx-new, which changed nothing - the X server fails to start on 20-16 with this error message:
```
(EE) Failed to load module "wfb" (module does not exist, 0)
FATAL: Error running install command for nvidia
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):   *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.
```
However, the nVidia drivers seem to be loading fine under 20-15 since X is working fine - I'm posting from 20-15 in fact.

Any ideas on how could I fix this problem with 20-16?

Thanks in advance,

-Fibo

---

### Post by masani3llo on 2007-06-11
different errors but same here. My idea is that as long as linux-restricted-modules are not updated to the same kernel version nvidia driver won't work...

---

### Post by freanki on 2007-06-11
same over here :(
The xserver says wrong nvidia-kernel-modules...

---

### Post by Fibonacci on 2007-06-13
> **masani3llo said:**
> My idea is that as long as linux-restricted-modules are not updated to the same kernel version nvidia driver won't work...

I don't think that's the cause of the problem - linux-restricted-modules-2.6.20-16-generic was installed at the same time as linux-image-2.6.20-16-generic.

---

### Post by Vola on 2007-06-13
same problem here.

I tried to reinstall restricted modules but nothing....

look like are not updated to the same kernel level.

strange things in synaptic there are installed:


linux-image-2.6.20-16-generic (version 2.6.20.16.29)
linux-image-generic                  (version 2.6.20.16.28.1)
linux-restricted-modules-genric                  (version 2.6.20.16.28.1) 
   
any ideas??

---

### Post by Pumalite on 2007-06-13
> **Vola said:**
> same problem here.

I tried to reinstall restricted modules but nothing....

look like are not updated to the same kernel level.

strange things in synaptic there are installed:


linux-image-2.6.20-16-generic (version 2.6.20.16.29)
linux-image-generic                  (version 2.6.20.16.28.1)
linux-restricted-modules-genric                  (version 2.6.20.16.28.1) 
   
any ideas??

Why don't you guys go to the NVIDIA site and download the driver to your /home/<username>, then go to virtual terminal ( Ctrl+Alt+F2 ), then run this:
[http://ubuntuforums.org/showthread.php?t=470821](http://ubuntuforums.org/showthread.php?t=470821)

It worked for me.

Good luck.

---

### Post by Fibonacci on 2007-06-13
> **Pumalite said:**
> Why don't you guys go to the NVIDIA site and download the driver to your /home/<username>, then go to virtual terminal ( Ctrl+Alt+F2 ), then run this:
[http://ubuntuforums.org/showthread.php?t=470821](http://ubuntuforums.org/showthread.php?t=470821)

Wouldn't that disrupt the Ubuntu package structure?

---

### Post by Pumalite on 2007-06-13
> **Fibonacci said:**
> Wouldn't that disrupt the Ubuntu package structure?

Absolutely not. The installation itself takes care of everything. Removes old modules and reconfigures your xorg.conf file. You end up with the newest driver . ( the latest I installed is 9755 and I'm happy with it ). Make sure you have kernel-headers matching your kernel version, that you have: 'make', 'automake', latest gcc, and 'autoconf' before you do it.

---

### Post by Fibonacci on 2007-06-14
> **Pumalite said:**
> Why don't you guys go to the NVIDIA site and download the driver to your /home/<username>, then go to virtual terminal ( Ctrl+Alt+F2 ), then run this:
[http://ubuntuforums.org/showthread.php?t=470821](http://ubuntuforums.org/showthread.php?t=470821)

It worked for me.

Good luck.

Didn't work for me. In fact it worsened the situation, since I cannot 
start X from *any* kernel, not just the last one. I'm posting this 
from w3m right now.

---

### Post by Pumalite on 2007-06-14
> **Fibonacci said:**
> Didn't work for me. In fact it worsened the situation, since I cannot 
start X from *any* kernel, not just the last one. I'm posting this 
from w3m right now.

Check this:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217)

And if that doesn't clear things up for you, then I don't know how to help you. Maybe someone more experienced will jump in.

---

### Post by Fibonacci on 2007-06-15
> **Pumalite said:**
> Check this:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217)

And if that doesn't clear things up for you, then I don't know how to help you. Maybe someone more experienced will jump in.

I don't think that has anything to do with my problem, since I wasn't getting any error messages about API mismatches.

Anyway, it doesn't matter now since I (finally!) got it to work, by uninstalling the NVIDIA-Linux-...-pkg1.run drivers, and then running Envy.

---

### Post by rafaelperrone on 2007-06-15
> **Fibonacci said:**
> I don't think that has anything to do with my problem, since I wasn't getting any error messages about API mismatches.

Anyway, it doesn't matter now since I (finally!) got it to work, by uninstalling the NVIDIA-Linux-...-pkg1.run drivers, and then running Envy.

OK, but how can it be done manually without using Envy? What if I don´t want to use Envy? Anyone know a solution?

Same problem here. 

Thanks

---

### Post by el_itur on 2007-06-18
sudo modprobe tells me that it can't install the module, it was correctly working untill I uninstalled the lowlatency kernel and rollback to generic.

---

### Post by AriciU on 2007-06-21
Latest kernel is useless. I've wasted around 14 hours now trying to get the god damn nvidia driver to work but no go. No envy, no guides, nothing helps. 

IT"S IMPOSSIBLE TO DO NOW FFS!

I'll just go back to the old kernel and drop this ****. I'm so pissed off i feel like breaking my monitor or something ](*,)](*,)](*,)](*,)

Last time i ever do a kernel update that's for sure.

---

