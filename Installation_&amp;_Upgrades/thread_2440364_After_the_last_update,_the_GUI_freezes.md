---
title: "After the last update, the GUI freezes"
date: 2020-04-09
forum: Installation &amp; Upgrades
---

### Post by ahmed-mo2nis on 2020-04-09
I have been using Ubuntu for almost 2 years now on my current laptop (Dell G5 15 I7). I have been installing updates and upgrades whenever prompted to do so and restarting whenever it says so. After the last update (2 days ago). I turned off my laptop and when I opened again I noticed that my GUI freezes every few seconds except for the mouse ! That particularly happens when a certain program is open (Godot Engine) other than that it works OK but that problem wasn't there before installing the last update so is there hope that this problem will be fixed at the next update or is there something I can do now to fix this until the next update solves it ? Thanks in advance

---

### Post by mörgæs on 2020-04-11
Hi, welcome to the fora.

Freezing can have many reasons and it could take a while to find out why it happens in your installation. 

As a short-term fix you could run ```
sudo apt install xubuntu-desktop
``` if the terminal is stable enough to use. After that boot into the Xubuntu desktop environment in stead of Ubuntu to see if it works better.

The proper fix might be a clean install of 20.04. An update to your present OS might also solve the problem but again, we don't know the exact cause.

---

### Post by Impavidus on 2020-04-11
> **ahmed-mo2nis said:**
> ... my GUI freezes **every** few seconds ...
That suggests is temporary, not permanent, right? It recovers automatically after some time, you don't have to reboot.

It might help if you told us which release of Ubuntu you use. Also which packages were upgraded when this problem started. You can find that in your log files. Check /var/log/dpkg.log. I got a kernel upgrade 5 days ago. That may have triggered the problem. Maybe you can boot an older kernel. That might help for the moment.

---

