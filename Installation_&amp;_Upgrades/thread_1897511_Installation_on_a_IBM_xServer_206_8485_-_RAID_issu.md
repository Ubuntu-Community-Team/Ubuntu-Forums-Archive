---
title: "Installation on a IBM xServer 206 8485 - RAID issues"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by Michael_BoG on 2011-12-19
Hi guys,

I've recently swapped out Windows for Linux on my homeserver. The problem is that I cannot get the Ubuntu Server installation to get past the partitioning section. I get two choices, one is to load ATA drivers and proceed to some iSCSI setup where I have to enter an IP, the other one is to ignore the drivers and not load them, what happens then is that all the drives show up as individual drives, not one single disk (which it should because the disks are in RAID). If I install Ubuntu Desktop (which kind-off worked) it shows up as one unit, and everything works until it's installing the bootloader, then it fails.

How can I make the server-install work? I really need it.

Hope you guys can help me, thanks.

---

### Post by darkod on 2011-12-19
So what is the problem with entering the IP? A server would usually have static IP and it is asking you which to configure. You can also leave it as DHCP.

As for the grub install failing on ubuntu desktop install, you should use the alternate image when installing the desktop version to a RAID, not the standard image.

But stick to the server version as planned, configure the IP and let it finish the install. Even if you have no network cable connected at the moment, it doesn't mind that.

---

### Post by Michael_BoG on 2011-12-19
Well the thing is that I do not have any static IP, not any NICS in the server at all, actually. I have tried localhost and everything, doesn't work. Why can't I just choose the disk (raid) and partition it like I do in Windows, I don't even know what IP i should use for the iSCSI thing.

---

### Post by darkod on 2011-12-19
Is it asking you for IP of the iSCSI or in the networking part?

How come you have no network ports on a server, they have built-in ports since ages ago?

If it is the networking part, and you don't even plan to use it in the network, just put some private IP like:
IP: 10.0.0.10
Subnet mask: 255.255.255.0
Gateway: 10.0.0.1

Of course, that will not lead the server anywhere.

If it is asking for some kind of IP for the iSCSI bus, I have no idea about that.

---

### Post by Michael_BoG on 2011-12-19
I was kind of in a hurry when i wrote that. The server has got a nic, but it is not connected to anything, and it is not setup either. It's asking for "iSCSI target portal address". There must be another way to do this, it's stupid that i've got to enter some IP but not knowing what the IP is lol. The controller isn't a SCSI controller either, it's a SAS.

---

### Post by darkod on 2011-12-19
From what I could see in a short google search, it looks like the server was used earlier as a NAS. In that case it might have the IP allocated to the iSCSI. But not sure if this applies only to windows and why would it ask you for it during ubuntu server install.
Try to google more with that message, personally I have no idea what is this about.
One link for example:
[http://www.qnap.com/pro_application.asp?ap_id=135](http://www.qnap.com/pro_application.asp?ap_id=135)

---

