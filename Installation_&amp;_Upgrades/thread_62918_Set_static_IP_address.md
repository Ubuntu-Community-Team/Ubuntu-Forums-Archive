---
title: "Set static IP address"
date: 2005-09-06
forum: Installation &amp; Upgrades
---

### Post by n!x on 2005-09-06
I'm running an Ubuntu server and want it to always have the LAN IP address 10.0.0.2, even if it is restartet - how do I do that?

---

### Post by xy77 on 2005-09-06
Quick and dirty hack:

```

#!/bin/bash
# not tested, no warranty!
# sets ip for eth0 to 10.0.0.2
/sbin/ifconfig eth0 up
/sbin/ifconfig eth0 10.0.0.2

```

save this as e.g. eth0_default_ip.sh and add this filename to /etc/rcS.d/S55bootmisc.sh (you could add these lines there directly).

Perhaps anyone else can point you to the correct files that have to be changed in order to do it the correct way :)

If you have X installed (yeah, I know some of you wouldn't install it on a server, but there are reasons for it), you can change the settings for network via System -> Configuration -> Networking (from memory, so it may differ).

- David (xy77)

---

### Post by n!x on 2005-09-06
Hmmm, I haven't installed X cause haven't got a display to attach. 

Isn't there a cleaner way to do it - like a .conf file or something?

---

### Post by fortytwo on 2005-09-06
[QUOTE=n!x]Hmmm, I haven't installed X cause haven't got a display to attach. 

Isn't there a cleaner way to do it - like a .conf file or something?[/QUOTE]
 I've been trying to do this same thing (although on Kubuntu).  I believe in the networking setup you can turn off DHCP and set an address manually, but I'm still having trouble getting it to be able to access the internet after making that change...I've tried adding the router lan ip as the DNS server, but still no luck.  Any ideas?

---

### Post by n!x on 2005-09-07
Yes, there are a place where you can set the DHCP - but how do I set it to static IP. And again, I'm headless   :-?

---

### Post by lol on 2005-09-07
have a look at 'man interfaces'

basically, all you have to do is to edit /etc/network/interfaces to have something looking more or less like this:
-------------------
auto lo eth0

iface lo inet loopback

iface eth0 inet static
        address 10.0.0.2
        netmask 255.255.255.0
        broadcast 10.0.0.255
        gateway 10.0.0.1
--------------------

alternatively, you can also use the gnome graphical tool (somewhere in preferences->networking I guess).

---

### Post by n!x on 2005-09-07
Thanks alot!!!

Editing the /etc/network/interfaces with:
```
iface eth0 inet static
address 10.0.0.2
netmask 255.255.255.0
broadcast 10.0.0.255
gateway 10.0.0.1
``` 

worked as it should....

Thanks again!

---

