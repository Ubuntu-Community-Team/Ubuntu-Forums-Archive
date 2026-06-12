---
title: "[SOLVED] No network with Ubuntu Gutsy command line install"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by urukrama on 2007-12-27
I've done a command line installation of Ubuntu Gutsy on a Dell Inspiron 2500 laptop that has no ethernet port, but uses a PCI card (Realtek) to connect to broadband. During the installation I was told it could not configure the network with DHCP, so I skipped the network configuration (since I had no clue what else to do).

How can I get the networking to work on this laptop? I searched the forums and the internet but couldn't really find anything that made much sense to me.

A few things to keep in mind (to give you an idea of what I have tried, and perhaps to show my ignorance in this matter ;-):
[LIST]I don't have any graphical user interface, just a command line. Using the network manager or something similar,won't work, in other words.
[/LIST]
[LIST]There is nothing wrong with the card and the connection. I can use the connection on a different computer, and I've used both the card and the connection on that computer before. Strangely enough when I installed Fluxbuntu earlier, I had no problems whatsoever with the network. TinyMe also gave no problems.[/LIST]
[LIST]I can't ping or use aptitude to install anything from a normal repository.
[/LIST]
[LIST]Not sure if this is of any use, but when I plug the cable into the card, a green light goes on, but nothing else changes. Ifconfig only gives me the 'lo' settings (no eth0), as follows:
> lo       
[INDENT]Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:97584 (95.2 KB)  TX bytes:97584 (95.2 KB)
[/INDENT]
[/LIST]
[LIST]The Realtek card is listed in when I use the command "lspci" as > Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)[/LIST]
[LIST]Running sudo /etc/init.d/networking restart (or stop/start) doesn't do anything. Nothing is listed.
[/LIST]
[LIST]I get an error message when during the boot process it comes to the "starting network services" (or whatever is called), but I can't remember what it is.
[/LIST]

Any help is appreciated!

---

### Post by louieb on 2007-12-27
What happens when you run ?
```
sudo dhclient
```
If you have a wired connection that should work.
one more thing to try  if that doesn't work
```
sudo ifup eth0
```
or you may need to use eth1
```
sudo ifup eth1
```

---

### Post by urukrama on 2007-12-28
Thank you, the first command worked perfectly. Problem solved.

---

