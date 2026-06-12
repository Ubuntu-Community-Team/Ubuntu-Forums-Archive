---
title: "Netboot using tftp by Windows"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by vdit on 2010-03-01
I have been trying to install Ubuntu by network booting, I used tftp in Windows in another pc, and the target boots successfully but fails to download from any archive mirror, I'm not sure what goes wrong.

Well, I'm trying to do is, my friend's HP-mini fails to boot to Windows, and BIOS also gives error-messages, the thing is that my friend has important data on his netbook, it has only one drive, no cd-rom, and it doesn't support USB-booting, so I was thinking if I get to access an Ubuntu, I will be able to backup his data and install Windows, I would use anything that would let me copy files.

Any other ideas?

---

### Post by dstew on 2010-03-01
> the target boots successfully but fails to download from any archive mirrorI assume the target is the netbook, and that another PC is acting as the tftp server for the installer initrd and kernel.

Do you get the Ubuntu install menu when you netboot? Is the target PC connected to the internet? It gets the Ubuntu system from the internet itself, not from the netboot server.

---

### Post by vdit on 2010-03-01
The target is the netbook, netbook is connected to the router so it's connected to internet.
I get the Installation menu, it fails to configure the network with DHCP, so I configure it myself like 

```

IP : 192.168.1.2 (<-- same IP the tftp server transfers files to)
subnet: 255.255.255.0
gateway: 192.168.1.1

```

And yes I understand that it gets the Ubuntu system from the internet itself.

---

### Post by dstew on 2010-03-02
My (limited) understanding of netboot is that the tftp server is also a DHCP server. The netbook PXE BIOS broadcasts a request for a network IP address when it boots, and also for a netboot kernel if the DHCP server can provide one. The netboot server should provide the netbook with the IP address, and then the tftp transfer of the kernel takes place. I don't think tftp can work if the client does not have an IP address. Is that how you set it up? Sometimes, you have to turn off the router's DHCP server if it has one, so the netboot server can take control. In that case, you set up the netboot server with a static IP address, and then make it a DHCP server. That is how I have done it before. Maybe there is some conflict between two DHCP servers, but I really can't say for sure.

---

### Post by vdit on 2010-03-08
Okay well, I tried some stuff, I wanted to boot the iso itself but I couldn't get it work. I thought what I told my friend to get HP to help him instead.
I had my router's DHCP server disabled but it didn't work.
Anyway thanks dstew, and I apologize for replying a week later.

---

### Post by Mr_Durden on 2010-03-08
I guess you are using the alternate install for ubuntu?

The text based.

When you have reached the auto dhcp config in the installation,
you turn back dhcp from the router.

This will not crash your installation.

Then you simply wait awhile till the router has started sending out dhcp again, and your installation that searches for ethernet configuration and dhcp will get it, and you will be able to continue.

---

