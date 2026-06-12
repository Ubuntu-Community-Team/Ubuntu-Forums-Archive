---
title: "running gnome-shell in oneiric in a virtual machine"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by psikobare on 2011-10-17
hi

before moving to oneiric with gnome-shell i decided to try it a few  days/weeks in a virtual machine in order to learn and get use to it
i use vmware player for its performance (tried virtualbox, with no success), version 4.0.0 build-471780 in win7 64bit

installation (desktop amd64) is fine

moving to gnome-shell seemed pretty easy according to tutorials

apt-get install gnome-shell

logged out, log back in in GNOME

but i appear to always end up using the fallback (GNOME and gnome classic look the same)
screenshot, loging with GNOME:
[[IMG]http://uppix.net/3/4/6/19f4b19ed80e4b3e8e8ef4bb5d971t.jpg[/IMG]]("http://uppix.net/3/4/6/19f4b19ed80e4b3e8e8ef4bb5d971.html")

3d acceleraton is activated in vmware

[COLOR=Black]glxinfo [COLOR=#000000]**|**[/COLOR] grep [/COLOR][COLOR=#FF0000][COLOR=Black]"direct rendering"
gives me [/COLOR][/COLOR]direct rendering: Yes

but gnome-shell --replace
gives me:
failed to create drawable
(gnome-shell:1487): clutter critical, unable to initialize clutter, unable to select the newly created GLX context
window manager error: unable to initialize clutter


as the title say, running gnome-shell in oneiric in a virtual machine, is it possible? has someone manage to do it?

---

### Post by zebx on 2011-10-27
Hi,

I have the same issue and error message on my Vaiio laptop without virtual machine. :(

---

### Post by subehsharma on 2011-10-29
i have also faced this problem now. anybody has any idea?

---

### Post by Shazaam on 2011-10-29
Virtual machine software normally do not access your actual video card hardware; Xen may be the exception. They usually use an "emulated" video card. As such you cannot get the true "3d" experience with them no matter what they say. To get true "3d" they would have to find a way to access your actual hardware with the virtual machine. AFAIK VmWare and VirtualBox do not have that capability right now.
In my experience Unity and gnome-shell usually work fine in 2d mode (or fallback mode in gnome-shell) in a virtual machine.

---

