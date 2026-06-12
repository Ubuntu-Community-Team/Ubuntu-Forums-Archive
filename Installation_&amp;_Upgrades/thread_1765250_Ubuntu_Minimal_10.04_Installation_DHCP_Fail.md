---
title: "Ubuntu Minimal 10.04 Installation DHCP Fail"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by ruimarto on 2011-05-22
During the Ubuntu Minimal 10.04, 10.10 or XBMC Live (Ubuntu 10.04) I get a DHCP automatic configuration fail. If I change to manual and put the IP, gateway, mask and DNS servers, the installation goes fine but when I boot I don't have a connection.

Installing Ubuntu minimal 11.04 everything works.

What could be the problem?

My system is an Asus AT5IONT-i and it's connected by wire to my router. I've double checked the cable and the router and all seams fine.

---

### Post by linuxinstalledfromhdd on 2011-05-22
are you using the alternative installation disc for Ubuntu?

---

### Post by ruimarto on 2011-05-22
I'm using a USB pen with 64bit Ubuntu 10.04 Lucid Lynx minimal that I downloaded from here:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

During the install I get:

**Network autoconfiguration failed**
Your network is probably not using the DHCP protocol. Alternatively, the DHCP server may be slow or some network hardware is not working properly.

If I configure manually, installation goes well. When I then boot into the system, problem returns and there's no network connectivity. I tried to edit /etc/network/interfaces to static with IP, gateway and mask below, and no luck.

---

### Post by linuxinstalledfromhdd on 2011-05-22
what kind of protocol does the router use for this connection?

---

### Post by ruimarto on 2011-05-22
What do you mean? It's a regular router (DIR-825) so I guess it uses TCP/IP...

---

### Post by linuxinstalledfromhdd on 2011-05-22
Static IP?

---

### Post by ruimarto on 2011-05-22
Yes. I've fixed IPs for every machine in my network. But DHCP is on. And like I said, with 11.04 version, everything works fine.

I've done:
sudo ifdown eth0
sudo ifup eth0

And got a message saying OpenSSH was running. After reboot it went down again. And apt-get update not working either.

---

### Post by ruimarto on 2011-08-02
I've used the jumper on the board to clear the BIOS and looks like it's fixed.

---

### Post by dino99 on 2011-08-02
So now please use the "Thread Tools" on top to mark it as SOLVED

---

### Post by ruimarto on 2011-08-09
Done! :D sorry I forgot

---

