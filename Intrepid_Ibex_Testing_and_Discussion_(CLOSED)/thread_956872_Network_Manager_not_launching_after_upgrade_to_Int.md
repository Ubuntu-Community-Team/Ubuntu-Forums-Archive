---
title: "Network Manager not launching after upgrade to Intrepid"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by elcman on 2008-10-23
Ok, I've been living without this for a while, but I'm really getting tired of doing all my networking manually when Network Manager worked just fine on Hardy.

First thing's first:
I have been able to use Ethernet without a problem, but after a recent update, my Ethernet will no longer start up and pick up an IP address. I've been having Wireless woes similar to this for a while and since the NM-Applet wasn't launching, I couldn't easily figure out what was going on. Only after some research today, I've found that I have been using **ifconfig** and **iwconfig** correctly, but never ran **dhclient** to pick up an IP address.

Now that I've been able to get everything upgraded and am now to the latest, I find that Network Manager is still giving me grief. (Again, not knowing Network-Manager-Gnome was **nm-applet** until today to find the source of my problems.)

I have a Broadcom 43xx (using **b43legacy**) which I thought was part of the problem, but using **iwconfig** I have easily connected to my base station. (Just never ran **dhclient** to pick up an IP address.)

Now, to where I'm at. When I run nm-applet:
```

** (nm-applet:8090): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service.
  Message: 'Connection ":1.27" is not allowed to own the service "org.freedesktop.NetworkManagerUserSettings" due to security policies in the configuration file'


(nm-applet:8090): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

Tacking **--sm-disable** on this does not help. Running it with **sudo** does something a little different:

```

** (nm-applet:9220): WARNING **: No connections defined

```

I just checked my Interface (since I figure that's what it is looking for:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

Easy peasy. Everything is where it is supposed to be, but the applet doesn't show up on my computer and it is driving me nuts.

I even changed the dbus file to *allow* in **/etc/dbus.1/system.d/NetworkManager.conf** as said by another post to allow the nm-applet to be run without **sudo**.

I also fiddled with the **/etc/NetworkManager/nm-system-settings.conf** and put *Managed=True* in there after reading some suggestions.

I can't get the Network Manager applet icon to appear! I did get it to work once, but then I killed it to allow it to run again.

I did the basics, uninstalled, reinstalled... I'm really annoyed with this thing right now. So far **iwconfig** and **ifconfig** are the only things working... and all of my searches point to old bugs that happened months ago or simpler problems than what I'm having.

Any ideas? I'd really appreciate it!

---

### Post by Gina on 2008-10-23
I have it running fine on a bcm4306 rev.3 using the b43 driver.  Fresh install a few days ago on my laptop and the various updates applied since.

I suggest trying a fresh install (reformatting the partition for /) - problems can be carried over from earlier.  Even keeping the /home partition can cause problems with older settings which are saved in the hidden files in the home directory tree.

---

### Post by Slug71 on 2008-10-23
Yeh you may just wanna try a fresh install as what Gina said could be true. There shouldnt be any probs at this stage. I have a broadcom BC4312 and have a driver with the Kernel and a restricted driver not in use.

---

### Post by bash on 2008-10-23
If that doesn't help or just in general, have you filed a bug about it yet? 

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by elcman on 2008-10-24
Surprisingly enough, after all of my manhandling of the configuration files, I decided to put everything back to the way it was and turn it off to "let it heal" as I often do when I get annoyed with something.

This morning, the laptop came up without an issue and I can see that it is displaying the network manager applet icon, picking up an Ethernet address and *most importantly* showing me all detected wireless access points in the area.

Seriously, I have no idea which of my changes worked? I had rebooted multiple times before that... But, now I can say that all is well!

Thank goodness.

---

