---
title: "Intrepid Broke on Virtual Machines Again?"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by EmyrB on 2008-10-10
Hi all,

I am running Intrepid on a virtual machine, VMware Workstation ACE Edition 6.0.4 build 93057 to be precise. I did a dist-upgrade today and now its broke :(

GDM comes up and I can enter my username and password but then all I get is the orange screen and that's it. No disk activity, nothing.

This is very reminiscent of the kernel/virtual box/vmware issue that was plaguing Intrebid's early development cycle.

Cheers

EmyrB

---

### Post by grigio on 2008-10-10
I've the same problem, but if I press ctrl+alt+backspace and I try again, gnome-session starts.

You can also login in console recovery mode and start manually "gnome-session&"

---

### Post by EmyrB on 2008-10-10
Interestingly, I logged in via the failsafe terminal and ran gnome-session& and it said that gnome-session was not installed!

Now I know I didn't uninstall it, so did the update today remove it?

Cheers

EmyrB

---

### Post by EmyrB on 2008-10-10
Now this is really weird...

I can't install gnome-session as it depends on gnome-control-center, gnome-settings-deamon, gnome-panel and nautilus, but Intrepid is not going to install these... damn fine of it I say :(

Any ideas folks?

---

### Post by EmyrB on 2008-10-13
Never mind I solved this by installing a daily build snapshot ;D

---

