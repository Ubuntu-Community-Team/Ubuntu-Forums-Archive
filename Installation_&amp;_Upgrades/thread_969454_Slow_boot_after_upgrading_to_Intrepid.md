---
title: "Slow boot after upgrading to Intrepid"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by Poilar on 2008-11-03
Ever since I upgraded to Intrepid my boot has been very slow.

I looked at the text while booting and it basically slows down when it's dealing with network stuff. It takes maybe 5-8 seconds on "Configuring network interfaces," and then sits on "Starting NTP server ntpd" for a good 30 seconds or so. 

Any ideas?

I've attached a bootchart, in case that's helpful at all.

Thanks!

EDIT:

So I did some more research (disabled ntpd) and it's sitting at "Configuring network interfaces" and not at ntpd.

I use both wired and wireless connectivity depending on where my computer is (it's a laptop). My /etc/network/interfaces file simply reads:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

This is the same file that worked perfectly under gutsy. If I'm plugged into an ethernet cable, it appears that my computer stalls looking for a wireless network to connect to. If I remove the portion dealing with eth1 (my wireless interface) then that stalling goes away, but then my wireless capabilities are disabled. If I'm not plugged into an ethernet cable, then my computer stalls looking for an ethernet connection which I presumably could get around by removing the portion dealing with eth0, but then I'd just have no Internet capabilities at all.

More Edits:

I had uninstalled network-manager, which is why my interfaces file had content other than the loopback. I tried clearing out eth0 and eth1 and reinstalling network-manager and now my computer boots quickly again. I'm not sure why Ubuntu was suddenly unable to deal with not having network-manager when it worked fine under both Hardy and Gutsy, but this at least is a partial solution.

---

### Post by bwhite82 on 2008-11-03
There are several things you can do just by looking at your bootchart but at a price. Actually, it depends on if you need certain things. For instance, you can:

-Get rid of 'dhclient' if you set yourself a static IP

-ntpudate keeps your clock in sync with internet time servers, if you trust your hardware with this you can get rid of this too. Actually, you can just prevent it from running as a daemon at startup and just use it from CLI whenever you deem it necessary

-moblock is gruelingly slow during boot, perhaps reconsider if you really need this

-Do you need printing support? If not get rid of cups.

-Do you use ssh/openssh? If not, get rid of them.

-I don't need 'avahi' on my machine, but perhaps you do

Basically, start googling things you see in your bootchart, you can trim what you don't need. There are several apps to help you with runtime editing, rcconf for instance. Actually, it is better to completely uninstall certain apps via Synaptic.

Do so at your own risk and with care.

---

### Post by JamieKitson on 2008-11-05
Looks like a problem with your network setup. I would have a look in /etc/network/interface and remove anything that you don't use. eg, if you use wireless but not wired then remove eth0 references.

---

### Post by Poilar on 2008-11-05
So I did some more research (disabled ntpd) and it's definitely sitting at "Configuring network interfaces" and not at ntpd.

I use both wired and wireless connectivity depending on where my computer is (it's a laptop). My /etc/network/interfaces file simply reads:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

This is the same file that worked perfectly under gutsy. If I'm plugged into an ethernet cable, it appears that my computer stalls looking for a wireless network to connect to. If I remove the portion dealing with eth1 (my wireless interface) then that stalling goes away, but then my wireless capabilities are disabled. If I'm not plugged into an ethernet cable, then my computer stalls looking for an ethernet connection which I presumably could get around by removing the portion dealing with eth0, but then I'd just have no Internet capabilities at all.

---

### Post by m.h.shams on 2008-11-06
I have same problem too,

after upgrading to 8.10, it take about 1min during loading network interface.

my startup in 8.04 was really fast with this configuration. i didn't change anything i just upgrad to 8.10

---

### Post by mbeccaria on 2008-11-09
confirm same problem. Only upgrade from hardy to intrepid, no change in the network config. Boot is now embarassing slow.

---

### Post by edyeeh on 2008-11-13
It has something to do with /etc/network/interfaces/ 

when I switched from wicd to network manager, network manager configured it for me, and the slow boot disappeared. I think with wicd, ubuntu tries to connect during boot executing dhcp which is very slow. Network manager edited out the process and tries to connect at the desktop which is more sensible for me.

---

### Post by vikeshraj on 2008-12-24
interfaces tagged with auto are tried to brought up during boot time

If you want Network Manger to bring up your interfaces, you may want to comment out the lines for eth0 and eth1 and give it a try.

I had faced the same issue and it works fine after that.

---

### Post by m.h.shams on 2008-12-25
Hi All,

I just install ubuntu 8.10 again. i mean a fresh installation not update.

and i have no boot time speed problem right now. :D


thanks all.
shams

---

### Post by romanyiv on 2009-04-20
> **vikeshraj said:**
> interfaces tagged with auto are tried to brought up during boot time

If you want Network Manger to bring up your interfaces, you may want to comment out the lines for eth0 and eth1 and give it a try.

I had faced the same issue and it works fine after that.

The solution above worked for me - very annoying long boot up time.  This is on 8.10 Ubuntu Studio - new install - and finding out how to get rid of that splash screen so I could see the boot up messages was a pain also.  But very fast now...

---

### Post by romanyiv on 2009-04-20
> **romanyiv said:**
> The solution above worked for me - very annoying long boot up time.  This is on 8.10 Ubuntu Studio - new install - and finding out how to get rid of that splash screen so I could see the boot up messages was a pain also.  But very fast now...

I should also add I'm running WICD - - and that disabling the splash screen is an edit of the grub file....

---

