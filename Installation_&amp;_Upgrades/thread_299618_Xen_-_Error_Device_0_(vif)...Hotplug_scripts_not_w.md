---
title: "Xen - Error: Device 0 (vif)...Hotplug scripts not working."
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by genibot on 2006-11-14
I've loaded Edgy with Xen following the guide at [XenOnUbuntuEdgy]("https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy").  However, I get "Error: Device 0 (vif) could not be connected. Hotplug scripts not working." anytime it try to create a DomU for "edgy-guest" or "vmx-guest". I've tried the /udev/rules.d/XX-xend-backend.rules noted in some of the Xen on Dapper post to no avail.  If I change the "vif = [ 'bridge=xenbr0' ]" in the edgy-guest.cfg to "vif = []", the domU guest will come up (without networking of course).  Has anyone solved this on Edgy?

Thanks!

---

### Post by nvilloutreix on 2006-11-25
I do have the same problem : ubuntu 6.10, used this tutorial : [http://www.howtoforge.com/xen_3.0_ubuntu_dapper_drake](http://www.howtoforge.com/xen_3.0_ubuntu_dapper_drake), did the trick on renaming xen-backend.rules.
I used xen-tools to create my lvm image with the debootstrap method.

Still get Error: Device 0 (vif) could not be connected. Hotplug scripts not working.

Same error with vif = [].

Anyone can help, give tips, pointers to documentation explaining what hotplug scripts are, why they don't work. Is it specific to the 6.10 version?
Why the trick with xen-backend.rules worked with 6.06?

Thank you!

---

### Post by noobaholic on 2006-11-26
I found this IRC log:

[http://www.linode.com/xen/irc/logs/xen.log-2006-11-09](http://www.linode.com/xen/irc/logs/xen.log-2006-11-09)

> 03:45 < fabien> hello
03:50 < fabien> I have trouble booting a guest. xm create reports "Hotplug script not working" and in xen-hotplug.log I see a lot of "trap 53: bad trap" error
03:50 < fabien> Anyone have this problem or advice to solve it (xen-3.03, ubuntu edgy, amd64)
03:50 < fabien> ?
04:33 < buggs> fabien, have you installed bridge-utils etc. ?
04:33 < fabien> yes
04:34 < fabien> I finally find the issues on a forum: scripts in /etc/xen/scripts use #!/bin/sh
04:34 < fabien> I replace this by #!/bin/bash and it works fine

I'm having the same issue, with the same trap 53 error, so I wrote a little script to correct the scripts he mentions. Apparently it worked for him, but it didn't change anything for me :(

Anyway, I'm attaching the script in case anyone else wants to give it a shot. You need to run it in /etc/xen/scripts. Also, if you have a more eloquent way to script this, I'd be happy to see it :)

---

### Post by falchionsteve on 2006-12-01
Here's a slightly more elegant method...

perl -pi.bak 's?/bin/sh?/bin/bash?g' *

which will leave the originals with the .bak suffix


I've got a similar problem, but for me the domain starts the first time, but a second time, it fails with the "hotplug not working" message.

I had noticed with a slightly earlier version of 3.0.3 that I'd lose the xend daemon (xm list would show no domains, not even 0).  Restarting it would seem to clear the problem, but the domain still wouldn't start.

I've upgraded to the latest 3.0.3 source tree (nov 12) and xend doesn't seem to die now, but still a problem with hotplug on the second create of the same domain (haven't tried multiple domains)

If anyone has some thoughts, please let me know...

STeve

---

### Post by sprucio on 2006-12-05
I am having the same problem as you guys after using the command ```
xm create guest.cfg
```

Can anyone tell me what processes should be running for xen to work?

---

### Post by rprotteveel on 2006-12-13
Hello guys and girls,

I changed the standard configuration file for the Domain on this part:

##
# To bridge network traffic, like this:
#
# dom0: fake eth0 -> vif0.0 -+
#                            |
#                          bridge -> real eth0 -> the network
#                            |
# domU: fake eth0 -> vifN.0 -+
#
# use
#
(network-script network-bridge)
#
# Your default ethernet device is used as the outgoing interface, by default.
# To use a different one (e.g. eth1) use
#
# (network-script 'network-bridge netdev=eth1')
#
# The bridge is named xenbr0, by default.  To rename the bridge, use
#
# (network-script 'network-bridge bridge=<name>')
#
# It is possible to use the network-bridge script in more complicated
# scenarios, such as having two outgoing interfaces, with two bridges, and
# two fake interfaces per guest domain.  To do things like this, write
# yourself a wrapper script, and call network-bridge from it, as appropriate.
#
#(network-script network-dummy)

Standard, the last line (network-script network-dummy) is uncommented. You need to comment this line out and uncomment:
(network-script network-bridge)

Now it works like a charm!

Cheers,

Ronald

---

### Post by noobaholic on 2006-12-16
Thanks for the perl falchionsteve.

As for the above solution, I've already tried that and unfortunately it didn't change the problem :(

---

