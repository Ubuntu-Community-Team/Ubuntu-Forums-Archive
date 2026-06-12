---
title: "HP laptop owners: please do this test"
date: 2008-06-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2008-06-30
I have an HP DV6627EL and I discovered a bug in the touchpad, that was already filed
[https://bugs.launchpad.net/bugs/193575](https://bugs.launchpad.net/bugs/193575)

I simply ask you to do this simple test, to see if the problem is common for all HP laptops.
[B]
rapidly press CAPS-LOCK button (at least 10 times), while moving your finger on the touchpad[/B]
The result in my case is that the touchpad loses the scroll capability.

What about you? please tell us your model and if this problem exists
Thanks

---

### Post by scradock on 2008-06-30
Doesn't seem to show the same problem on my HP Pavilion zv6000 (6007us).

---

### Post by Vegetarianrage on 2008-07-02
HP DV 6736nr  I have the same issue although i hadn't noticed if it was related or not to the capslock.

My capslock does fishy things sometimes anyway... like completely kill the keyboard, touchpad, and quicktouch buttons. They won't come back even after powerdown/reboot. I have to take the battery out of the laptop and put it back.

---

### Post by yelo3 on 2008-07-02
So it might be a BIOS failure... but I don't know how to contact HP without passing through the useless assistance crew that is only capable of suggesting to use the recovery to get the system to the factory defaults :(

---

### Post by olskar on 2008-07-02
I think this could have something to do with bug 34501.

I get the very same error when trying to use my SD-card and I am not using HP.

Check what your dmesg says right after the mouse begins to work strange.

Anyway it is marked as High so it should be sorted out if what you are suffering from is the same as in the bugreport :)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/34501](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/34501)

---

### Post by Vegetarianrage on 2008-07-05
I can now verify the capslock trick. I also posted everything we've mentioned here in the launchpad ticket for this bug. Hopefully that will get sorted out somehow or another.

---

### Post by yelo3 on 2008-07-06
I've got a solution for this. put this file in /etc/hal/fdi/policy/ and remove the .txt extension that was forced by the forum attachments handling

This will solve the reconnect issue

---

