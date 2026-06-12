---
title: "Problem /etc/resolv.conf DNS settings being resetted on reboot"
date: 2005-06-24
forum: Installation &amp; Upgrades
---

### Post by frank_y on 2005-06-24
Every time I reboot I have to manually edit my resolv.conf DNS settings because the default ones don't work very well. It works well for the duration of the session but when I reboot, my changes are erased and the default DNS settings come back up. Is there an option to prevent this? Someone recommended that I remove root write privilages but that didn't work either.

Frank

---

### Post by elvis on 2005-06-24
A few questions:

1) Are you setting your IP information manually?  Or are you using DHCP?  If you are using DHCP on a LAN, then either fix the settings given by your DHCP server, or change to a static IP.

2) Do you have other packages like resolvconf (different to resolv.conf) installed?

(apt-cache showpkg resolvconf)

Sometimes these are installed along with Squid-cache and other packages.  Resolveconf can be configured to override/overwrite your resolve.conf

---

### Post by tonym on 2005-06-24
This can happen if you are using DHCP.  If so,  try editing dhcp-client.conf.  There is a list of options you want to receive from the DHCP server  -  remove the DNS server option from the list.

---

### Post by frank_y on 2005-06-24
I am setting these manually, not using DHCP. I don't have resolvconf installed either. I tried removing the domain-name-server item from the request in the dhclient.conf file, but that didn't work, and I'm a newbie to linux so I don't really know much of what else to try :/

---

### Post by stream303 on 2006-01-16
Edit your /etc/dhcp3/dhclient.conf

sudo gedit /etc/dhcp3/dhclient.conf

Before the **request** line, add this line with your known DNS server address

If you only know one DNS server:
[B]
supersede domain-name-servers 123.45.678.90;[/B]

If you know the primary and backup:

**supersede domain-name-servers 123.45.678.90, 234.56.789.01;**

Just separate with a comma and don't forget the semicolon at the end.

You could now reboot, or just get a new lease from the terminal:

sudo ifdown eth0
sudo ifup eth0

see if your new /etc/resolv.conf looks good!

---

