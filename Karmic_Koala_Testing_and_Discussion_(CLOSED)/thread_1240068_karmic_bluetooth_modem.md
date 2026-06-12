---
title: "karmic bluetooth modem"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sycron on 2009-08-14
Is there a way to connect to the internet with karmic and a bluetooth modem? In 9.04 i've done it with blueman but in karmic doesn't work, when i go to setup i get a blank window and i can't connect to the dun modem.

Any help is apreciated as i'm offline for 2 days. I like karmic alot, even there are some problems but it's damn good.

---

### Post by Sycron on 2009-08-15
bump

---

### Post by Sycron on 2009-08-16
please

---

### Post by miegiel on 2009-08-16
Maybe I can hijack a friends phone to try it, my mobile is to ancient :(

---

### Post by Sycron on 2009-08-20
bump

---

### Post by plun on 2009-08-20
Bump...:)

Dan Williams wrote an blog article in early July about this.

[http://blogs.gnome.org/dcbw/2009/07/10/unwire-with-networkmanager/](http://blogs.gnome.org/dcbw/2009/07/10/unwire-with-networkmanager/)

I have tested it without success also with gnome-bluetooth from Gnome SVN.

Blueman ?

---

### Post by Sycron on 2009-08-20
neither of them works

---

### Post by dudude on 2009-08-21
I have gotten bluetooth PAN networking to work with Blueman and the bluez-compat package in the past.

On the the post about NetworkManager [here]("http://blogs.gnome.org/dcbw/2009/07/10/unwire-with-networkmanager/") it says that there is supposed to be support for PAN networking. I am not sure if the Ubuntu version of NetworkManager is older than the one in the link above, or there is a difference in the way that Ubuntu and Fedora package Bluez, but PAN networking does not work for me in Karmic.

Also, I don't know much about DUN networking, since the phone that I am using does not support it over Bluetooth.

---

