---
title: "How to have DHCP set hostname?"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by NutMonkey on 2005-10-03
I'd like to have the hostname set to the IP name DHCP returns, automatically on boot-up.  Any ideas on the best way to do that?

---

### Post by mlomker on 2005-10-03
> Any ideas on the best way to do that?

Is this for a CD or diskless workstation boot or something unusual like that?  

The scripts for dhclient are in /etc/dhcp3.  There is a dhclient.conf file and the dhclient-script.  I see that there are options for a hostname in there and that some environment variables are set, based upon what is found.

---

### Post by NutMonkey on 2005-10-04
It's for my work PC, where I'm not technically supposed to be running Linux, and the hostnames are supposed to match a naming convention based on the IP address given by the DHCP server.

I had read the dhclient man pages but the only hostname-related options I found were to send the hostname to the DHCP server to get an IP based on the hostname.  Unless you've seen something I didn't?  Otherwise, the only way I can think of would be to create a bootscript that runs after the network script and modifies the hostname.

---

### Post by mlomker on 2005-10-04
> Otherwise, the only way I can think of would be to create a bootscript that runs after the network script and modifies the hostname.

Ah, I see.  I think you'd have to write your own script.  You could execute your script out of the dhclient-script, though, so it updates whenever your address does.  I'm not a shell scripting guru but it's just manipulating text so it can't be too bad.

---

### Post by michaelaoash on 2005-10-06
I have been struggling with this for several years on debian and now ubuntu systems using dhcp3-client.  On RedHat systems, which I believe use pump by default, hostname is set by DHCP.  (I thought about switching to pump, but the apt-get remove of dhcp3-client warns that ubuntu-minimal will be unstalled at the same time, and that doesn't sound good.)

I have several questions (Let me begin by noting that dhcp seems to be working fine in terms of giving a working internet connection and I can get my ip address from ifconfig.  But hostname --fqdn returns localhost.localdomain, hostname returns the text in /etc/hostname, and hostname -i returns 127.0.0.1.  My problem is fundamentally superficial, but I really would like the computer to look as if it is named what the dhcp server thinks it is named.)

1. Is it really impossible to tweak  /etc/dhcp3/dhclient.conf to set  hostname from the dhcp server?  

2. Would it make sense to write a script that does this manually?  What would such a script look like?

3. Would it be dangerous to uninstall dhcp3-client (remember the ubuntu-minimal problem above) and to replace it with pump?


Best,

Michael

---

### Post by NutMonkey on 2005-10-06
I removed dhcp3-client (yes ubuntu-minimal metapackage is safe to remove) and installed dhcpcd.  I uncommented the options SET_DNS, SET_DOMAIN and SET_HOSTNAME in the /etc/dhcpc/config file, rebooted, and it set my hostname correctly.  It seems to be a feature missing in dhcp3-client but existing in dhcpcd and pump.  I did find this information on modifying the dhclient-exit-hooks script to set the hostname:
[http://lugwash.org/linux-users/200312/0127.html](http://lugwash.org/linux-users/200312/0127.html)
But I'd rather just use dhcpcd which is what I'm used to anyway..

---

