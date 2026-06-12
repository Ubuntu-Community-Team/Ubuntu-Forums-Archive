---
title: "dhcp3 server wont install properly.  No files in dhcp directory?"
date: 2011-11-10
forum: Installation &amp; Upgrades
---

### Post by fredted40x on 2011-11-10
Hi,

Im just trying to install dhcp3-server into the lates ubuntu version using guides on the net which all say the same thing but in the dhcp3-server directory there are no files (including dhcpd.conf) and just a empty directory and there is no way to start the server.

It just refuses to install properly.

Anyone know whats happening?

Many thanks.

Fred

---

### Post by papibe on 2011-11-10
I recently learned that dhcp3-server became obsolete (now it's called transitional package). Install this instead:
```
sudo apt-get install isc-dhcp-server
```
Regards.

---

### Post by fredted40x on 2011-11-10
That would explain it.

isc-dhcp-server looks ideal thanks.  Have found a guide on failover as well.  Will give it a go ina  bit.

Thanks again.

---

### Post by fredted40x on 2011-11-10
Where would the config file be for this server?  It seems to have added the program into init.d directory which is further than i got before but im now unsure of which config file to change?  There isnt one in /etc

Sorry im a real beginner.  How do you start the server? every site i look at for isc-dhcp-server is still using dhcp3.  Is DHCP sinstall on ubuntu already?  Why do i need to install a seperate server if this is already installed?  What is the plain dhcp package?  Everything seems to relate back to isc's server but they are different packages?

Sorry about all the questions.

---

### Post by papibe on 2011-11-10
The main file to configure is:
```
/etc/dhcp3/dhcpd.conf
```
Check this [tutorial]("https://help.ubuntu.com/community/dhcp3-server"), it's a bit old (it references dhcp3-server), but it is still a good basic guide.

Hope it helps,
Regards.

---

### Post by fredted40x on 2011-11-11
Brilliant.

Manged to get it up and running and it seems to work really well.

Is it possible to get it to hand out the proxy as well?

Thanks again for your help.

---

