---
title: "Upgrade to Lucid on 5,3 keyboard not responding"
date: 2010-03-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by viktara on 2010-03-05
Hi,

I upgraded to Lucid with update manager last night.

Everything seemed to go ok - except now the keyboard has stopped working!

Anyone seen this already?

TIA


Vik

---

### Post by alpine4 on 2010-03-05
Yeah, I'm currently having the same issue on my iMac. Keyboard only works for about 2 seconds after plugging it in, then just stops  :-?

---

### Post by viktara on 2010-03-06
According to this bug:
[https://bugs.launchpad.net/bugs/513932](https://bugs.launchpad.net/bugs/513932)

It appears that the problem is caused by the mouseemu package.

I logged in using the virtual keyboard, removed that package - and my keyboard is now working again :)

---

### Post by alpine4 on 2010-03-06
Sweet! That seemed to do the trick. Thanks!

---

### Post by robyinno on 2010-03-11
On my PowerBook 12 1Ghz is solved in the same way!

Thanks

---

### Post by nitrofurano on 2010-03-26
@alpine4 this is not a trick, since mouseemu on macs are very important... :(

---

### Post by kfsone on 2010-03-26
I'm running 10.4 in a VMWare environment, I haven't rebooted the virtual machine in a while, but I just had to, and I had the keyboard-not-responding issue;

Additionally: The on-screen keyboard app kept crashing as soon as it opened until I booted off the install DVD with the onscreen keyboard set at the initial menu.

I don't have mouseemu installed...

---

### Post by padangbond on 2010-04-16
I've also found out that if you have a line on /etc/modprobe.d/options.conf:

options hid pb_fnmode=2

Change it to:

#options hid pb_fnmode=2

And save. If you have no access to your keyboard, ssh into your machine and change it that way. Suddenly all your usb will just work!

---

