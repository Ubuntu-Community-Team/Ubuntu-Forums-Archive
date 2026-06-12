---
title: "kdm IO Error in XOpenDisplay"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by jrcmuniz on 2007-06-03
Hi,

I'm facing some kdm problems and I hope I could get workarounds to sort this problem out!
I just installed Feisty Fawn DVD from scratch (everything went smoothly) and then, decided to install nvidia driver (downloaded from nvidia.com)... now, I just can't get logged in Kubuntu anymore...

I don't know, but it seems to be a nvidia issue:

1st: with /etc/init.d/kdm stop; ./NVIDIA-Linux-x86_64-1.0-9755-pkg2.run and then /etc/init.d/kdm start everything works again.

2nd: just for test, I changed "nvidia" to "vesa" and rebooted... I could login again (without nvidia acceleration driver).

3rd: tried to install nvidia driver using Automatix2... same error... no log screen

Here is what I found in KSystemLog:
kdm IO Error in XOpenDisplay

Internal error: memory corruption detected

<WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - org.freedesktop.NetworkManagerInfo.NoNetworks. 

So, to get my nvidia driver working and to get logged I need to stop kdm and do all the 1st step again and again...

PLEASE, could someone give me any clue??? I am really exhausted and I am sure that this is not the smartest thing to do.

Many many thanks in advance.

Best regards,

Joao.

Kubuntu Feisty Fawn 64 bits
kernel 2.6.20-16-generic #2 SMP
asus P5B
Intel core 2 duo 6400
Gforce xfx 7600 GT.

---

