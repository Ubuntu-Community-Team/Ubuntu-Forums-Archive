---
title: "Getting Gnome Back"
date: 2008-09-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Rashedul on 2008-09-13
After a recent careless update (quite possibly partial) I lost Gnome. Now I can't start Gnome. I can only access the x terminal. I have few other problems. One of the big one being my CD drive stopped working so I can't use a live cd to chroot to fix the update. I have tried Unetbootin to create a Live USB harddrive but that doesnt work. Fedora's live USB creator worked and I can boot into Fedora. I also can't "sudo apt-get intall ubuntu-desktop" since I'm not connected to Wireless internet if Gnome doesn't start.

So any ideas on how I can fix this? Seems like I got myself into quite a mess.

---

### Post by Nullack on 2008-09-13
One tip is to partition out your home directory so that if during testing you can format the file system and come in clean with your user setup still there.

Anyway, are you unable to start X, or is GDM failing or you cant log in?

Have you been through the relevant logs to see what the issue is?

---

### Post by Rashedul on 2008-09-13
Okay the solution was fairly simple. The problem was Gnome (nautilus, gnome-panel, ubuntu-desktop) was removed during an upgrade. I could get up to the GDM login page but from there I didn't have the option of Gnome session, only xterm. All I had to do is get on the internet by plugging in through the ethernet instead of depending on wireless. I use wireless so much that I completely forgot I can still get on the net without wireless. After that it was as simple as update, upgrade and install ubuntu-desktop. My apologies about the false alarm. Thank you.

---

### Post by inportb on 2008-09-13
You could also connect wirelessly using ifconfig, iwconfig, and dhclient.

---

