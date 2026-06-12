---
title: "Install two NICs (one network one iSCSI)"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by mebunto on 2010-05-10
Is it possible to install two NICs during an installation from CD?  I tried and failed yesterday.
The eth0 would have a static ip address 192.168.0.11 and would be used for Internet/network whereas eth1 would have a static ip address of 192.168.2.81 and would be used for connection to the ISCSI system (DROBOPRO).  Oh yes, it's Ubuntu 10.04 Server version.
Install asks me to choose one of the two devices for configuration - I tried to be clever and set up one then the other but it didn't work, although the ISCSI subsystem was clearly working when I set up eth1 because the DROBO kicked into life as soon as I entered the IP address - communication was taking place.
Thinking that my fudge had worked, I continued to complete the installation only to find that neither network interface worked on reboot.

Thanks

---

### Post by darkod on 2010-05-10
There shouldn't be any problem using two NICs. Have you tried actually skipping setting up during install and set up both later?

I have no much experience with server version but can't see a reason why it wouldn't allow you to do that. I might be wrong though. :)

PS. Having said that, what you tried should have worked too. Set up one during install and the other manually later.

---

### Post by mebunto on 2010-05-10
I could do that however I am trying to install from CD/Internet as much as possible so that everything is automatic including the iSCSI installation.  It avoids having to download packages and configure network/iSCSI manually.

---

### Post by darkod on 2010-05-10
Correct me if I'm wrong, but with both cards designated for static IPs there is not really an "automated" process. That would be DHCP.

At some point you need to type in the static settings. Does it matter whether it's during install or later?

Of course, I might be not understanding your process. :)

The drivers from the CD should be installed when the hardware is detected anyway. As for entering static IP settings, doesn't matter when, it needs to be manual.

---

### Post by mebunto on 2010-05-10
OK.  Blow by blow.

[LIST=1]
[*]The installation prompts to set up the network
[*]I am presented with a choice of two network interfaces
[*]I select the first and I can either set that one up with DHCP or a static IP address that connects the computer to the Internet so that the installation can download packages as it requires
[*]The installation then prompts me to continue, but I do not get the opportunity to set up the second network interface
[*]Therefore I cannot configure the iSCSI subsystem during installation (through the second network interface) - which I'd really like to do
[*]So I tried to be clever and went back to the network interface choice and selected the second choice
[*]I set that up with a static IP address for connection to the iSCSI subsystem
[*]I then go through the iSCSI setup and the DROBO sparks into life - good news
[*]Then I complete the installation until I am asked to reboot
[*]All seems well, the DROBO is still running (it does not run if it does not have a network to talk on)
[*]I reboot the system
[*]The system boots up but it seems to loop showing network errors and the DROBO does not start up
[*]I assume that the network has not configured itself properly during installation
[/LIST]
I'm think that steps 2 - 6 may have resulted in my losing the eth0 setting so I am trying to find out if there is a legitimate way to set both network configurations during installation, rather than post-installation.
Thanks

---

### Post by mebunto on 2010-05-10
ok does this help?  The boot message is:

ipconfig: eth0: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
/scripts/local-top/iscsi: .: line 421 can't open /tmp/net-eth0.conf
IP-Config: eth1 hardware address 00:30:48:n:n:n mtu 1500 DHCP RARP


etc etc.

Machine not booting.  I assume that it's trying to boot from iSCSI device on eth0 ??

Can anyone help please?

---

### Post by mebunto on 2010-05-10
OK, I guess I'm on my own.

It seems logical that I should be able to set up two ethernet connections eth0 and eth1 during installation - I don't see how anyone using iSCSI is going to be able to set up the iSCSI subsystem on installation unless they can.  If you can only set up eth0 then you will not see the iSCSI system unless it's on that network and that kind of defeats the object of having iSCSI.
If I could set up two nics then the iSCSI installation would be automatic.

I'm going to try and just use eth0 then set up iSCSI later.

---

### Post by mebunto on 2010-05-11
Bump - can anyone help?  I've now done an install then tried to set up iSCSI after and the aptitude install open-iscsi is timing out for some reason.

---

### Post by mebunto on 2010-05-13
hello, anyone out there that can help?
It's a real annoyance.... I have tried to install around ten times now  and I can't fathom what can be done about this.
My latest attempt was to try specifying fixed ip addresses in the cd  boot options however that seems to cause a non-working Internet  connection.  I even tried preseed but I can find no information about  multiple nics in the documentation for that.

---

### Post by mebunto on 2011-05-03
It looks like this is not possible so I'm closing the thread.  I just configure the second nic after installation.

---

