---
title: "Broken upgrade..HELP"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by UbNewbie on 2006-06-16
Hi all,

Reading all the forums and finding the same problem with upgrading my machine from Breezy to Dapper Drake.
Only now I can go further with the upgrade because my networking part is not start anymore, so I don't have any Internet connections.

So I thought I will download the Dapper Drake DVD iso using my laptop and burn the DVD. Clean up the sources.list and refer only to the DVD. P.S. I also following the advise:
sudo apt-cdrom add
sudo apt-get update && apt-get dist-upgrade.

But this doesn't help also.

So which option do I have at this time? Installing Dapper Drake from scratch?

Any Advise from the forums........

Thanks in advance.

H2T

---

### Post by jchau on 2006-06-16
Do you know any reason why the network is no longer working? Driver problems? Network device not detected? Network devices down (try "sudo ifup eth0" or replace eth0 with the name of your network interface or "sudo ifup -a")?  What does ifconfig show?

---

### Post by UbNewbie on 2006-06-16
Jimmy,

The error message that I got when applying sudo ifup eth0:

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flasg: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device etc..

Then I tried to load the driver for the network card, but it is already loaded... and with lspci I see the card.

Looking further in the forum I found that someone had the same problem dus to lvm2 package. Do I deinstall lvm2 and the dist-upgrade running but after rebooting the system my network problem still there. I don't have any connections.

So I tried to install lvm2 again and got the error:

dpkg: error processing /cdrom//pool/main/l/lvm2/lvm2_2.02.02-1ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 10
Errors were encountered while processing:
 /cdrom//pool/main/l/lvm2/lvm2_2.02.02-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

.. Any suggestions???

Regards,

H2T

---

### Post by jchau on 2006-06-16
[QUOTE=UbNewbie]So I tried to install lvm2 again and got the error:

dpkg: error processing /cdrom//pool/main/l/lvm2/lvm2_2.02.02-1ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 10
[/QUOTE]


Did a window pop up saying what the error was? Well, nvm that. I just found your bug and there seems to be a fix.  See [https://launchpad.net/distros/ubuntu/+source/lvm2/+bug/47972](https://launchpad.net/distros/ubuntu/+source/lvm2/+bug/47972)

Hope that works!

---

### Post by UbNewbie on 2006-06-16
SO better to install Dapper from scratch than?

Lucky me that I don't upgrade my Laptop. Otherwise I have a big problem for my work.

Hmmm. somebody else has a good experience by upgrade from Breezy to Dapper drake than???


Regards,

H2T

---

