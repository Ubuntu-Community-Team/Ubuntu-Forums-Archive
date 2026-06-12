---
title: "Upgraded to 9.04. Wired Networking broken."
date: 2009-03-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by CyberPrime on 2009-03-09
Well, I just upgraded from 8.10 to 9.04 through update manager -d (or whatever it is), restarted and bam, no networking. It worked prior but not anymore, I am going to try "dhclient eth0" and see what that gives me. Any ideas?

Edit: that command gave me this:
Listening on lpf/eth0/00:04:4b:0a:0e:20
Sending on lpf/eth0/00:04:4b:0a:0e:20
Sending on socket/fallback
Dhcpdiscover on eth0 to 255.255.255.255 port 67 interval 6
Dhcpoffer of 192.168.1.2 from 192.168.1.1
Dhcprequest of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Dhcppack of 192.168.1.2 from 192.168.1.1
  *reloading /etc/samba/smb.conf smbd only
    ...done
Bound to 192.168.1.2 -- renewal in 37433 seconds

---

### Post by CyberPrime on 2009-03-10
Bump. I am surprised there's still no forum about the beta...

---

### Post by dodgers on 2009-03-10
Yes there is see here

[http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)

---

### Post by overdrank on 2009-03-10
Moved to Jaunty Jackalope Testing and Discussion

---

### Post by nanog on 2009-03-10
what does "infconfig" show?

if no ip address is indicated try:

[PHP]
sudo ifdown eth0
sudo ifup eth0
sudo /etc/init.d/network restart 
[/PHP]

if that does not work you should inspect /etc/network/interfaces

should look something like this (unless you have a static ip or an unusual manual set up):

[PHP]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
[/PHP]

what is the output of:

[PHP]sudo less /var/lib/dhcp3/dhclient.eth0.leases[/PHP]

"Bound to 192.168.1.2 -- renewal in 37433 seconds"

you *could* also have a conflict with an old lease. you can fix this by logging onto your old router or issuing:

[PHP] sudo dhclient -r[/PHP]

followed by 

[PHP]sudo dhclient[/PHP]

---

### Post by CyberPrime on 2009-03-12
Ok, none of that worked. The /etc/network/interfaces file was missing "auto eth0" so I put that in and rebooted but nothing. I am going to try and manually update and see if that helps any.

---

### Post by nanog on 2009-03-12
Check your dmesg to see if the driver for your nic is loaded.

---

### Post by CyberPrime on 2009-03-26
I got it working! Sorta... I needed the change the /etc/network/interfaces to the following:


# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

after a few reboots It was working. Sadly my updates and synaptic is giving me **** now. Whoopie.

---

