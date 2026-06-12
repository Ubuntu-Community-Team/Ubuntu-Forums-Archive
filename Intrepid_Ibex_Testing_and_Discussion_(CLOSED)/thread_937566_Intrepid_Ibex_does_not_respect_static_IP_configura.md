---
title: "Intrepid Ibex does not respect static IP configuration"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by brm on 2008-10-04
The boot sequence in Intrepid Ibex ignores the contents of /etc/network/interfaces and instead assigns an IP using DHCP.

This is my /etc/network/interfaces. It works as expected in Hardy Heron, but not in Intrepid:

```
bruce@Xenophon:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


# stanza added to configure Xenophon with static IP address, 20080602 1240
auto eth0
iface eth0 inet static
        address         192.168.111.2
        netmask         255.255.255.0
        network         192.168.111.0
        broadcast       192.168.111.255
        gateway         192.168.111.1
        dns-nameservers 64.71.255.198 208.67.222.222 208.67.220.220
bruce@Xenophon:~$
```

Running "sudo ifdown eth0" followed immediately by "sudo ifup eth0" brings up the correct IP address.

---

### Post by wgrant on 2008-10-04
[http://www.ubuntu.com/testing/intrepid/beta](http://www.ubuntu.com/testing/intrepid/beta). Third known issue.

We put release notes there for a reason, you know...

---

### Post by ntetreau on 2008-10-04
> **wgrant said:**
> [http://www.ubuntu.com/testing/intrepid/beta](http://www.ubuntu.com/testing/intrepid/beta). Third known issue.

We put release notes there for a reason, you know...

Thanks wgrant, I'm sure brm will appreciate the info and the links, especially coming directly from a developer.  Let me guess, you "put the release notes there for a reason", which is... to sound like my mom when I forget to wash my hands?  Wild guess!

---

### Post by illpig on 2008-10-04
hi all,

is there a fix out now? its beta and still not working.

cheers illpig

---

### Post by wgrant on 2008-10-04
> **illpig said:**
> hi all,

is there a fix out now? its beta and still not working.

cheers illpig

Note that the release notes **for the beta** say that it isn't working.

---

### Post by bash on 2008-10-04
Again in the list of the known issues there is a link to the bug report:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/256054](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/256054)

You can follow the further development from there. So far no fix.

---

### Post by ronacc on 2008-10-04
reading the release notes spoils the fun of finding the bugs yourself :lolflag:

---

### Post by brm on 2008-10-04
Thanks, wgrant, for the pointer to the release notes.

I had thought that networkmanager was a Gnome-related utility, but I was bitten with this problem early in the Intrepid Ibex cycle while I was still running pure Kubuntu and before I added Gnome. It would never have occurred to me to look at Gnome utilities for bugs affecting Kubuntu.

I now have Gnome installed as well, so that exposes me even worse :-(

And you were right, I do tend to head straight for the download pages, which, if I recall correctly, do not have links back to known issues.

At least I understand now why my bug, Bug #260733 filed on 2008-08-23, has attracted no attention, not even a duplicate tag.

May I add my voice to other experienced users (but not IT professionals, much less developers) who are driven crazy by graphical utilities which they didn't even know they had but ignore properly configured traditional plain text config files.

---

### Post by Robvdl on 2008-10-17
I noticed this bug in Network Manager 0.7 as early as 4-5 months ago, when a PPA for nm 0.7 was announced for Hardy, and it forced me to downgrade back to 0.6 because I could not use static IP with nm 0.7. It doesn't look good that this static ip bug is still not fixed now, only weeks before Intrepid's release. I fear this bug may not be fixed in time now, but only time will tell really.

Notice that this bug also happens if you do not manually edit your /etc/network/interfaces file, but instead go to "Edit Connections" in network manager's right click menu and either:

 - Edit the "Auto eth0" connection: no point doing this really, as network manager will reset this connection back to DHCP on reboot.

 - Disable "Auto eth0" from auto connecting, and create a new "Manual eth0" connection with static IP's and set that to auto connect. However, after a reboot, network manager also does not honour the auto connect tickbox on the manual eth0 connection and instead resets the "Auto eth0" connection again, putting the auto connect tickbox straight back in and connecting to the Auto eth0 connection again, using DHCP.

My workaround for now is as follows:

 - Leave auto eth0 as is, no point editing it as it gets reset after reboot

 - Create a manual eth0 connection set to static. After each reboot, switch to this profile (every time) to set static IP.

---

### Post by ntetreau on 2008-10-17
Am I the only one not having this issue?  I've been able to connect automatically to a wired network with fixed IP since Alpha 2 if I remember correctly.  All setings are kept over reboot as well.  Check the attached pic!

---

### Post by alphacrucis2 on 2008-10-17
> **ntetreau said:**
> Am I the only one not having this issue?  I've been able to connect automatically to a wired network with fixed IP since Alpha 2 if I remember correctly.  All setings are kept over reboot as well.  Check the attached pic!

I did originally have the problem at alpha 4 but at some point it started honouring the static configuration. I can't remember exactly what I did to get it to work. :confused:

---

### Post by issih on 2008-10-17
I can't get my static ip to be honoured after a reboot (using edit connections not /etc/network/interface) it also doesn't honour any changes made to connections after the first creation, and I had a hell of a job even creating an entry with all the details entered in it, it kept forgetting the default gateway, and then wouldn't save my edits.. the whole system appears to be somewhat buggy.

needs work I'm afraid

---

### Post by muzincs on 2008-10-17
I had the same problem at Alpha 6.  Remove the four packages that show as installed in synaptic when you search for "network manager."  After that, reboot and the problem will be gone.

---

### Post by brm on 2008-10-17
There has been much work on this problem since the beta was released. The network-manager packages now respect static IP configuration in /etc/network/interfaces. See Bug 256054 ([https://bugs.launchpad.net/bugs/256054](https://bugs.launchpad.net/bugs/256054)).

---

### Post by saltydog on 2008-10-27
.

---

### Post by khunphil on 2008-10-29
> **brm said:**
> There has been much work on this problem since the beta was released. The network-manager packages now respect static IP configuration in /etc/network/interfaces. See Bug 256054 ([https://bugs.launchpad.net/bugs/256054](https://bugs.launchpad.net/bugs/256054)).

The bug is still open. Marked Fix Released.
I am on Intrepid RC1.
Editing the Auto Etho connection to Manual does not work automatically. I have to Disable/Enable Eth0.
Then reboot, and back to DHCP.
Philippe

---

