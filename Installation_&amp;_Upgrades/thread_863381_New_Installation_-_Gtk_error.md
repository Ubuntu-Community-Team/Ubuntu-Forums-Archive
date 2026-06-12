---
title: "New Installation - Gtk error"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by rawlins02 on 2008-07-18
Just installed 7.10.  When I ran from CD things seemed OK, except for network access.

After the installation I restarted and was presented with login screen. Logged in with username and password I set up during installation and got error that looked like this:

(process:5677): Gtk - warning **: This process is currently running setuid or setgid. This is not supported use of GTK+.


Also, what's the password for su - ?

---

### Post by damis648 on 2008-07-18
Try downloading and installing 8.04.1, formatting and installing on the same partition. Also, root (accessed by su) has a randomly generated password. Issue root commands with "sudo".

---

### Post by rawlins02 on 2008-07-18
Error has been fixed. It was very likely due to old files in /home. I retained that partition from previous installation of Fedora Core 6. After deleting all dot files I've now got Gnome fired up. Turning now to wired and wireless networking and geting KDE (3.5) running. In FC6 I used NetworkManager to set IP, gateway, etc.  Suggestions for testing network in Ubuntu 7.10?  How about enabling KDE?

---

### Post by rawlins02 on 2008-07-18
Used the following commands in an attempt to established wired network connection.

> sudo ifconfig eth0 inet 137.79.160.80 netmask 0xffffff00 broadcast 137.79.160.255 up
> sudo route add default gw 137.79.160.1

Then netstat -n gave this:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
137.79.160.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         137.79.160.1    0.0.0.0         UG    0      0        0 eth0


Not clear to me that this is correct. I'm able to ping gateway and a nearby subnet 137.78.x.x, but no outside IPs. DNS not yet set.  Suggestions?  Oddly, I had similar problems with Fedora Core setup. Maybe firewall issue here at work.

---

