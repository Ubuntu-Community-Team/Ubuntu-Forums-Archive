---
title: "[SOLVED] gnome startup sound error. No network. Beta"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2008-10-04
I tried the beta livecd. I had previously tried the alpha 6 live cd which worked fine.

When it started I got a gnome startup sound error. The startup sound worked, but the popup appeared afterwards (it couldn't close it or something). I didn't get a screenshot of the error.

another difference is that there is no network. Alpha 6 network automatically recognized my network but the beta did not.

Where has the network option gone so I can set my network option?
The menu is missing. It is not shown in menueditor either.
system->admin->network.

I tried beta in virtualbox and there was no sound error (no sound is possible since it cannot find a device) and the internet works fine.

Anyone have similar problems?

EDIT:
While installing it to a virtualbox I noticed network connections doing stuff. It now lists like 5 different connections with a bunch connected at once. See screenshot
I presume this is because it was detecting hardware? After rebooting when install was finished connections went back to normal.

EDIT:
Tried the livecd and I did not get a sound error. There still is no network, and no way to choose a network.

---

### Post by cariboo on 2008-10-04
Try:

```
nm-applet&
```

In a terminal. This should start up the network manager applet.

If that doesn't work in a terminal type:

```
sudo dhclient eth0
```

Jim

---

### Post by Frijolie on 2008-10-04
> 
nm-applet&


Thanks, I was having the same problem (network-manager applet not starting) and your suggestion allowed me to type in my passkey for my wifi network. Now, however the applet isn't appearing in my taskbar each time I load the OS. I know that it's working--because I have an internet connection--but the applet doesn't manifest itself. I've checked my "Sessions" under the Preferences menu and made sure that the applet was there. I guess, is this a bug that should be reported?

---

### Post by andrewabc on 2008-10-04
ubuntu@ubuntu:~$ nm-applet&
[1] 9167
ubuntu@ubuntu:~$ 
** (nm-applet:9167): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:9167): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


ubuntu@ubuntu:~$ nm-applet&
[1] 9167
ubuntu@ubuntu:~$ 
** (nm-applet:9167): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:9167): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


Looks like it doesn't recognize my computer having any network card. Which is silly because Alpha 6 worked.

---

### Post by Frijolie on 2008-10-05
I'm getting this same error. I have to have type "nm-applet&" in a terminal to get a working internet connection each time I start my computer. I've typed it in "Sessions" but it won't load on startup.

---

### Post by Simplicius on 2008-10-17
I've upgraded just now (October 17) and I also get the same error as the previous two posts. Ethernet was working fine in Hardy.

---

### Post by andrewabc on 2008-10-18
> **Simplicius said:**
> I've upgraded just now (October 17) and I also get the same error as the previous two posts. Ethernet was working fine in Hardy.

I'm waiting for the release candidate on Oct 21 to be released. Then I will test the livecd again and see if the same problem appears.

No one seemed to answer whether it was normal for the system->administration->network option to be gone in the beta livecd

---

### Post by shane19174 on 2008-10-18
> No one seemed to answer whether it was normal for the system->administration->network option to be gone in the beta livecd 

Well, I don't know about the live CD, but my Intrepid beta install has system -> administration -> Network Tools.

---

### Post by andrewabc on 2008-10-18
> **shane19174 said:**
> Well, I don't know about the live CD, but my Intrepid beta install has system -> administration -> Network Tools.

Yes network tools is there.
But in Hardy there was "network" just above network tools location.
Network was used to edit the network (such as wireless, or to change IP address etc).

This is one problem why I couldn't get the internet to work in the beta, because there was no "network" menu item for me to see what it was trying to connect to or to tell it to connect to something different.

---

### Post by shane19174 on 2008-10-18
> Yes network tools is there.
But in Hardy there was "network" just above network tools location.
Network was used to edit the network (such as wireless, or to change IP address etc).

Ahh, sorry for not reading more carefully...

---

### Post by netz on 2008-10-18
System -> Preferences -> Network Configuration for settings or $nm-connection-editor in terminal.

---

### Post by andrewabc on 2008-10-24
The release candidate live cd works great.
Networking works, and no other problems so far. The networking option was moved to preferences menu.

---

