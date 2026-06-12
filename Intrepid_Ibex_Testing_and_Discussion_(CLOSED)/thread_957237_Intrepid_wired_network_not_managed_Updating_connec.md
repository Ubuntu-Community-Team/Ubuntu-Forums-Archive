---
title: "Intrepid wired network not managed Updating connection failed: nm-ifupdown-connectio"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by aussiebuddha on 2008-10-24
Hi All.
a Few updates back my wired network stopped working, and everytime i try to edit via network manager it says

Updating connection failed: nm-ifupdown-connection.c.82 - connection update not supported (read-only)..

Does anyone know how to fix this?
I'm on a standard DHCP config, nothing fancy here.

Thanks!!!

---

### Post by Cirion75 on 2008-10-24
I have the exact same error...

---

### Post by yakyuwarrior on 2008-10-25
I am having the exact same problem, except with a manual (static IP) connection.  It worked until I unplugged the chord; when I plugged it back in, the connection no longer worked.  It appears to have lost any record of the DNS server; when I try to change any details, I get the same message as above.

I was able to create a new wired device, but this did not allow me to connect to the internet.

Also, when I click on the network manager icon in the upper right corner of the screen, it lists wireless networks, but under the wired networks section it says "device unmanaged."  Is this a related issue?

---

### Post by yakyuwarrior on 2008-10-27
Ok; now, after rebooting my computer, the network manager applet doesnt even show up.  Its listed under system processes, and I can edit the configuration under preferences, but I cannot get it to appear in the corner.  Trying to at least figure out a workaround that gives me internet access, so I can at least download the updates when they become available.

is there a relatively easy way to back track to Hardy until then?

---

### Post by aussiebuddha on 2008-10-28
is there a relatively easy way to back track to Hardy until then?[/QUOTE]
I dont think so mate.
Maybe try with wired internet if you have the chance to plug in?

Can anyone help?
still an issue

---

### Post by Graystonia on 2008-10-28
In the same boat... mine works great for DHCP (ifupdown (eth0)) but when I put in a static I get this address.  

On a side note I downloaded 8.10 and that is when I started having trouble.

I tried to delete the ifupdown but it won't let me, say's that it is read only.

---

### Post by aussiebuddha on 2008-10-28
guys. this bug is being tracked here.
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262)

I used one of the workarounds to delete the iface line for eth0 in /etc/network/interfaces and it work after a reboot.

give that a try, might do the trick for you as well

---

### Post by yakyuwarrior on 2008-10-28
OK, got it fixed.  I was able to fix the applet disappearing problem using a different thread.  To work around this connection issue, just altered my /etc/NetworkManager/nm-system-settings.conf file.  Here is what it read as originally:

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


I just changed it to this:

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true


That seemed to do the trick.  Note: I had to create a new wired network device under the edit connections tab.  The default one still remains read only.

Does this work for anyone else?

---

