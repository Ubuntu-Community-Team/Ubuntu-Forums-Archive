---
title: "Network not working"
date: 2005-03-20
forum: Installation &amp; Upgrades
---

### Post by kgreiner on 2005-03-20
I decided to change distros from Debian sarge so i down loaded the install cd of hoary. Installed fine but once it came up after the reboot the network would not work.

In dmesg it shows the eth0 card loads the DaviComm 9xxx driver with the correct IRQ and MAC address.

when i try a ping i get a network unreachable.

I am usning DHCP and during the install it found my DHCP server with out problem. I did not have to enter anything and the correct IP address is listed in /etc/resolv.conf

After the first install i went through the process again this time I monitored my dhcp server and during the install before the ejection of the CD media and rebooting I was connected properly after that nothing would work.

What could be different between booting up and it works vs install? 

What could i do to help resolve this issue.

Thanks in advance

---

### Post by kleeman on 2005-03-20
Does ifconfig show the eth0 interface or only lo?
If the latter try executing "sudo ifup" and report messages.
If ifup works try ifconfig again

---

### Post by kgreiner on 2005-03-20
ifconfig shows eth0 along with my MAC address with out having to doing that.


If i try ifdown eth0 and then eth0 it tries to discover the DHCP then after 4 attempts it fails. NO DHCPOFFERS recieved.

---

### Post by kleeman on 2005-03-21
So I would guess ifconfig shows no ip address for eth0. From what you describe
the attempt to get the networking details from the dhcp server is unsuccesful not that your nic isn't working. I assume your dhcp comes from a router. You could try manually assigning the ip and gateway and dns servers using the gnome networking tool and see whether this works. You should know these details from the last time you had the networking going. I am not much of an expert on dhcp: you need a good howto from the net.

---

### Post by kgreiner on 2005-03-21
I set a static ip address and same issues. I can not ping anything but the IP address that I assigned my box to. I can not ping the router nor anyother system on my network.

Any more ideas?

---

### Post by kleeman on 2005-03-21
I replied to someone recently here with this problem and they checked their router and found MAC address filtering enabled and their box MAC wasn't there. This might explain why no dhcp servers are being found. Here's the thread:

[http://www.ubuntuforums.org/showthread.php?t=20529&page=2](http://www.ubuntuforums.org/showthread.php?t=20529&page=2)

This is a long shot I know  ;)

---

### Post by kgreiner on 2005-03-21
i am not sure what is going on. I gave up on Hoary and stepped back to Warty and choose the same options as before and on reboot my network works via DHCP. 

When i get a bit of time i may try installing Hoary on my second drive in that system and see if it comes up.

---

### Post by kleeman on 2005-03-22
OK that sounds like a bug in Hoary. I have a similar issue in that my nic doesn't work with hoary but does with warty. I suggest you lodge a bug report and help out the developers.

---

### Post by kgreiner on 2005-03-22
after i installed warty I decided to use apt-get to upgrade to hoary, one i did my network connection died as usual. 

where would i post for the developers?

---

### Post by kleeman on 2005-03-22
You have to register first at this site:
[https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/)

Be prepared to answer a bunch of questions  :)

---

### Post by ybloch on 2005-04-18
I'm experiencing a similar behaviour here with a Hoary Live CD. DHCP network works perfectly in Debian/sid, but under Hoary I can't ping anything but my NIC's address. However the IP address, default gateway and DNS servers are set up correctly by the DHCP client.

---

### Post by estm on 2006-05-14
I have had exactly the same problem doing a server (without GUI) install of Breezy Badger. Network appeared to work fine during install and was able to configure itself via DHCP, but after install and reboot there was no network connectivity. Trying to PING from the Ubuntu machine I got a "network unreachable" message. Picking up from a suggestion in this post, logged in as root and  tried "ifup eth0" (returned to prompt with no message) the "ifconfig eth0" returned the network card details with ip address. Pinging, and so networking, now all works.

---

