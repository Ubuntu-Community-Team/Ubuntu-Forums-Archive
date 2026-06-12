---
title: "Need walkthrough for Xubuntu install over local network via PXE boot"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by Objekt on 2010-01-13
I have a really old notebook I want to put Xubuntu 9.10 on, a Compaq Presario 710.  Its CD/DVDROM drive no longer works, and it is not capable of booting from a USB device.  It can boot over the network using PXE, however.  I previously got it to work & install the "alternate" version of Xubuntu, doing it from a Windows XP server.

Unfortunately, the Xubuntu install was the wrong one or corrupted, because I don't get a GUI.  I used the Xubuntu alternate install CD, because it was the only Xubuntu version I could find which had network booting files on it.  I would like to install the regular version of Xubuntu 9.10 instead.  I just can't get it to work with an Ubuntu server so far.

The hardware involved:

Ubuntu 9.10 desktop machine (server): This is the machine I want to use as the server for the Xubuntu install over the local network.  Its local IP address is 192.168.1.20.

Linksys BEFSX41 router: local IP address 192.168.1.1 (usual for a router).  Runs a DHCP server for the LAN.

Compaq Presario 710 (client): This is the machine I want to install Xubuntu on.  According to its PXE booting screen, it has a:
```
Realtek RTL8139(A/B/C)/RTL8130 PCI Fast Ethernet Controller v2.11
```
network adapter, with MAC 00:08:02:2C:70:7C.

All tutorials I've found so far for "netboot and install over a network" have been useless.  They are invariably outdated, confusing, incomplete, or all three.  They all recommend different dhcp programs, different tftp programs, and sometimes contradict each other.  I tried several in a row, and it's become a tangled mess.  I don't even know what services are running on my 9.10 machine any more.  Part of the solution will have to involve figuring out what DHCP/TFTP services are running on my server, & stopping them so they don't conflict with each other (for example, trying to assign an IP address that is already taken).

I almost got a PXE boot install started again, but not quite.  The client machine was assigned an IP by the DHCP program running on my Ubuntu 9.10 machine (server), but the next step failed.  I saw the following message:
```
PXE-E32: TFTP open timeout
```
several times.  Eventually the client gave up and booted off the hard drive.

I have googled this PXE error but found no fix.  It seems likely that, somehow, the client is unable to contact the tftp instance running on my Ubuntu 9.10 server.  I don't know why that would be, because I never set up any kind of firewall that should be blocking tftp.

I also need to know how to get the Xubuntu 9.10 desktop CD fed to the client over the network.  While I have a decent Internet connection, I DO NOT want to just download everything over the Internet.  I can mount the Xubuntu 9.10 *.iso for that.  I want to keep the traffic internal to my LAN until after the Xubuntu install, at which time I will connect the client to the Internet for updates.

Can someone please help me get regular old Xubuntu 9.10 32-bit installed on my old notebook?

Please remember to be very specific about any configuration files that need to be edited, where to find them, and how to do stuff like restart the tftp server (I have no idea how to do that, without restarting the server).

---

### Post by headvampyre@hotmail.co.uk on 2010-01-13
What packages have you installed for pxe-boot e.g ltsp ,dhcp and make sure you have an xubuntu netowork install image

---

### Post by Objekt on 2010-01-13
What do you mean by "Xubuntu network install image?"  I have two .iso's of the Xubuntu 9.10 Live CD, both the Desktop and Alternate versions.  
 
I also found references to a network install package tarball (something like netinstall.tar.gz) with a size around 11 MB.  Is that what you're talking about?  I downloaded the one for Xubuntu 9.10 & unpacked it.  However I'm not sure exactly what I'm supposed to do with the files contained therein.  

I assume there is a file in there that has to be served to the PXE client by the tftp process, but that does not seem to be happening.  I would guess that is why I get the TFTP error message on the client.  The client seems to be expecting something it is not getting.

I have installed at least the following on the server (Ubuntu 9.10 machine), because I kept trying another tutorial when one didn't work:

atftp
bootpd
dnsmasq
dhcp3-server

and probably some others I'm forgetting.

At one point I did get the client machine assigned an IP address (192.168.1.10), which is some progress.  So far I've been unable to get beyond that step.

---

### Post by Objekt on 2010-01-14
Come on, doesn't ANYBODY have any ideas??  I can't be the only person who's ever tried to do this!

So far I'm having more luck under Windows XP than under Ubuntu 9.10.  Using Tftp32 under Windows, the client machine starts right up.  But I don't want to do it under Windows, and anyway it starts downloading everything from the Internet.  That's going to take forever, at 6 Mbit/s from the repositories instead of 100 Mbit/s from a CD image over the local network.  

I don't understand why it won't work under Ubuntu 9.10.  How can I check that the right ports are open, etc.?

---

### Post by Objekt on 2010-01-22
Purely by mistake, I found that my router's DHCP server was somehow interfering with the net install process.  As soon as I turned it off, relying instead on a DHCP server running on my Ubuntu 9.10 server, I was able to proceed with installing over the network.  I'm marking this one "solved" accordingly.

---

