---
title: "[SOLVED] (Kubuntu) I can see my network, but I can't connect"
date: 2008-08-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by beartard on 2008-08-21
Just checking to see if any kubuntu users have the same problem before I post a bug.  
 
After the updates on 20 August, my wireless stopped connecting.
 
Knetworkmanager recognizes the adapter.  It shows my router (with great signal strength), but will not attempt to connect.  When I click on the router to connect, the GUI does nothing.  It doesn't give any errors either.  When I check iwconfig, my adapter is associated with my router, but dhclient will not work either.
 
I installed from alpha-4, got hit by the pam bug, fixed that, and updated to my current situation.  I had been planning a fresh install anyway, so I did that.  Got everything installed and did an upgrade this afternoon.  Same story.  
 
The adapter is a Linksys WUSB54GC, bought because it worked out of the box with Ubuntu.

---

### Post by sonofusion82 on 2008-08-21
i have the same wireless adapter and also using kubuntu but i don't have any problem connecting to my wireless router.
are you using any protection (WEP/WPA)?
perhaps you can check your /var/log/syslog to get some idea what went wrong?

---

### Post by Duf_Sh on 2008-08-21
Got the exact same problem with an intel awl4965 802.11AGN, was thinking about the driver since purging/reinstalling network-manager or using iwconfig with or without edition to the /etc/network/interfaces file doesn't work, but it seems the problem comes from elsewhere since the probleme is reported with a linksys adapter (I don't believe it's the same wireless chipset, isn't it?)

edit: using WEP here

re-edit: relevant /var/log/syslog:
Aug 21 23:22:02 Top NetworkManager: <WARN>  nm_spawn_process(): could not spawn process '/usr/sbin/nscd -i hosts': Failed to execute child process "/usr/sbin/nscd" (No such file or directory)
Aug 21 23:23:15 Top NetworkManager: <WARN>  wait_for_connection_expired(): Connection (2) /org/freedesktop/NetworkManagerSettings/Connection/0 failed to activate (timeout): (0) Connection was not provided by any settings service

re-re-edit:
No success after installing missing package nscd

---

### Post by beartard on 2008-08-22
> **sonofusion82 said:**
> i have the same wireless adapter and also using kubuntu but i don't have any problem connecting to my wireless router.
are you using any protection (WEP/WPA)?
perhaps you can check your /var/log/syslog to get some idea what went wrong?
I wonder if we have different chipsets.  I just remember buying this particular version because it worked out of the box.
 
My router is as open as can be.  There's not much need for big security in the area I live.  But I could re-install from the alpha cd now and be fine, but as soon as I dist-upgrade and reboot, I run into the problems I have.  I'll check the logs soon and see what I can find.  I was just hoping this is a bug that will be fixed soon or that there's some command I'm missing that'll make it all better. ;)

---

### Post by mblakele on 2008-08-22
[https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/259278]("https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/259278")

Workaround: install network-manager-gnome and launch nm-applet

---

### Post by beartard on 2008-08-22
Thanks for the link.  I wasn't sure it was knetworkmanager's fault since dhclient won't work from the command line either.  I've just moved to a wired network to keep me out of vista for the time being.

---

### Post by hardhu on 2008-08-27
Here's a copy of the comment I have added to bug 259278:

"I have a similar problem here with intrepid. With knetworkmanager I can see my wireless network (and those of my neighbors too...) but when I try to associate nothing happens, regardless of the fact I am using authentication or not. It is also worth to mention that when knetwormanager is running, I cannot even connect to my wireless network using iwconfig: what I get is that my wireless card keeps on disassociating from the ap with error 'disassociate(reason=3)' when I force the association with iwconfig. If instead I quit knetworkmanager (be careful: I exactly mean 'quit', not switching on offline mode) then I can manually associate to the ap without problems and I can run dhclient with no problems."


I remember I have never been completely successful in using knetworkmanager to manage my network connections in kubuntu, while I got no problems with opensuse 11 that I have been testing for while, so I wonder what is different between the two distro that makes so complicated to have it working on kubuntu

---

