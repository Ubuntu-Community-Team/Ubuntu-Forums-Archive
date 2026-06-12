---
title: "Ubuntu 5.04 installation DHCP server failure (but server is there!)"
date: 2005-09-01
forum: Installation &amp; Upgrades
---

### Post by barrel on 2005-09-01
Hi all,

I recently installed Ubuntu 5.04 on my laptop and am absolutely satisfied. On my PC I used to have Mandrake 10.1 and decided to install Ubuntu (same version) on this machine as well.

Now the problem is that during installation, a message something similar to 
'No DHCP server found on your network or your server is very slow' occured, basically leaving me wihtout internet connection.

I know that the DHCP server works, because my laptop (installed with a connection to the same router) properly receives an ip address from it.I am using it at this very moment ;-)
Perhaps it might be the cable so I did a cable switch. Same message.
DHCP worked fine on Mandrake so I guess there is no problem with my network card and I find it hard to believe that my network card crashes exaclty during this small 15 minutes of rebooting and repartitioning...

Any help appreciated
Barry

---

### Post by barrel on 2005-09-01
Some more information:

I let the installation finish, system comes up clean.

As root: dhclient eth0:
<skip isc intro message>

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/... (mac address is shown)
Sending on LPF/eth0///..... etc

where I see some different intervals being tried and then 

No DHCPOFFERS received
No working leases in persistent database - sleeping


Hmmm.....

---

### Post by barrel on 2005-09-01
Tried to install Breezy as well (can't hurt, my PC is useles at the moment ;-); same problem.

I did notice the following in my kern.log:

IPv6 over IPv4 tunneling driver
eth0: no IPv6 routers present

---

### Post by barrel on 2005-09-02
Guess I have to reinstall Mandrake?

---

### Post by fat_larry on 2005-09-02
Hi Barrel,

Unfortunately I don't have an answer to your problem, but I thought I would mention that I have the same problem so you're not alone!  During install, my wireless network card (Texas TNET1130 based) is detected, but Ubuntu does not manage to start it up, so cannot connect to the DHCP server. This is confusing and frustrating! So close but so far...  I have to manually configure the card using Ndiswrapper.

Perhaps the same thing is happening for you?

---

### Post by barrel on 2005-09-02
[QUOTE=fat_larry]Hi Barrel,

Unfortunately I don't have an answer to your problem, but I thought I would mention that I have the same problem so you're not alone!  During install, my wireless network card (Texas TNET1130 based) is detected, but Ubuntu does not manage to start it up, so cannot connect to the DHCP server. This is confusing and frustrating! So close but so far...  I have to manually configure the card using Ndiswrapper.

Perhaps the same thing is happening for you?[/QUOTE]

Well.. My card is not wireless... I have searched a lot and found a lot of problems with wireless cards so I guess that there is another issue there. 

I cannot get my connection working even after installation. :-(

I did notice one thing though... In my modules.conf, I replaced a reference from ipv6 to ipv6 and did not get the very first strange error message ( sit0: unknown hardware address type 776 ) anymore, but still no DHCP.

---

### Post by mlomker on 2005-09-02
What kind of card is it?  Is the driver being loaded?  Have you tried a static address?

Look at the output of:

ifconfig
dmesg
lsmod

Post the output relating to your network card and we might have something to suggest.  I had a similar problem with my wireless card--a module was being loaded but it didn't work right.  I downloaded the latest source from sourceforge.net and it worked fine when recompiled.  Maybe you have a similar issue that could be resolved by newer code?

---

### Post by barrel on 2005-09-05
[QUOTE=mlomker]What kind of card is it?  Is the driver being loaded?  Have you tried a static address?

Look at the output of:

ifconfig
dmesg
lsmod

Post the output relating to your network card and we might have something to suggest.  I had a similar problem with my wireless card--a module was being loaded but it didn't work right.  I downloaded the latest source from sourceforge.net and it worked fine when recompiled.  Maybe you have a similar issue that could be resolved by newer code?[/QUOTE]

Hi,

Thanks for your reply. I did look at dmesg, lsmod (nothing special to see) and used ifconfig quite a lot (made me feel a bit nostalgic ;-). The card comes up when I assign a static ip address but keeps giving me the message that the network is not available. 
The card itself is a simple ethernet 10/100 card, approx 4 years old. No rocket science.

I really think that it is related to the ipv6 but in the mean time, I installed SuSE 9.3 and it my computer is making small happy buzzing sounds again ;-) Too bad, but no Ubuntu on my home PC (it is still installed on my portable ;-)

Barry

---

### Post by alpha232 on 2005-10-08
I also have the same issue, except that I see the DHCPDISCOVER, DHCPOFFER from my server but it never accepts.

My network card is working fine, it is a 3c905 compatable.

When looking at the ifconfig, it shows an IPv6 address bound to eth0. This keeps on happening with the liveCD and also when i installed. I did get the LiveCD to work on the network ONCE, by manually adding a dhcp line in interfaces config and doing ifup eth0. That worked once, so i figured that was the fix, and after a 2 hour install, didn't work.

So any help would be great.

---

