---
title: "ppp connection through new Network Manager"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by robbak on 2008-10-15
I am trying to restore internet connection through my phone after installing intrepid.

What I need is to do a ppp connection, without authentication (or auth with dummy values), to /dev/rfcomm0, with a phone number of ", *99***1#'. I had this done through the old network manager, via its "PPP connections" option, and by fiddling with the ppp scripts.

How do I achieve this with the new one? There does not appear to be a way to specify a device name, which seems strange.

---

### Post by robbak on 2008-10-15
I have it working using gnome-ppp. Settings are:
Username: r 
Password: 1234
(These are the actual values. It seems to need a username and password, but anything will do.) 
Phone Number: *99***1#
Device: /dev/rfcomm0
Speed: 460800

Options: Ignore terminal strings: on, Wait for dialtone: off.

Some other options could be set; I get ConfigNak on all compression protocol requests, so I would probably test with header compression off as well. However, gnome-ppp works with these settings. I hve got rfcomm set up with the bluetooth tools.

Now I need to duplicate them under NetworkManager's ageis. How do I do this?

---

