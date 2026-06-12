---
title: "How to turn off Bluetooth in Intrepid at start ? Like in Hardy."
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Axx83 on 2008-10-26
Hello, I've just upgraded from hardy to Intrepid, no problem so far besides the horrible pulseaudio practically EVERYWHERE and this strage behaviour with bluetooth:

On my thinkpad x60s it's turned on at start, if I press the "fn" button on the keyboard it kills it but if I restart it's there again.

In hardy it was kept off until I would press the fn button again.

How to restore that ? I loved it and I miss it very much...please help me.

---

### Post by uidb4056 on 2008-10-26
You can go to System-Preferences-Sessions menu and uncheck Bluetooth.

---

### Post by Axx83 on 2008-10-27
> **uidb4056 said:**
> You can go to System-Preferences-Sessions menu and uncheck Bluetooth.

I did this, but as I expected the software is not loaded at startup while the hardware module is still loaded (the led is on)...

Other possible solutions ?

---

### Post by uidb4056 on 2008-10-27
Have you checked also in menu System-Administration-Services if service for Bluetooth is still enabled?, if yes try to disable it.

---

### Post by Axx83 on 2008-10-29
> **uidb4056 said:**
> Have you checked also in menu System-Administration-Services if service for Bluetooth is still enabled?, if yes try to disable it.

I did that too but the led is still turned on and I guess the bluetooth still consumes power. Powertop doesn't recognize it anymore, but I don't trust it in this, with hardy the led was off and my wattage was below 12 now it's above 13...

And, by the way, in hardy I just had to turn the bluetooth on (with keyboard) and it worked, for the few times I needed it. Now it's completely shut and I have to manually load the module.

---

### Post by uidb4056 on 2008-10-29
Searching in google I've found a bug report related with this issue [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/280811](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/280811)

Wait and see if it's solved soon.

---

### Post by Axx83 on 2008-10-29
Thank you so much, that is exactly the problem

---

