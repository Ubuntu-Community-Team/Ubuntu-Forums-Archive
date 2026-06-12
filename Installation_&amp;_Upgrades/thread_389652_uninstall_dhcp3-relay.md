---
title: "uninstall dhcp3-relay"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by leptogenesis on 2007-03-21
First of all, I've only been using Ubuntu for a few months, so I'm still relatively clueless...

I was trying to set my computer up as a DHCP server but accidentally installed the wrong package - "dhcp3-relay."  Realizing that it was the wrong package, I exited the setup, but it installed anyway.  Now, when I try to get rid of it, I get the error (from synaptic) "E: dhcp3-relay: subprocess pre-removal script returned error exit status 1".  As it is, I can't get the real DHCP server app to work.  Any ideas?

---

### Post by kidders on 2007-03-27
Hi there,

I just posted to your thread on remote command execution, and I noticed you've only made two posts ... I figured (since it's gone unanswered for 6 days!!) that I'd take a swing at this one too. :-P

Basically, what's probably happening is that one of the scripts designed to check & double-check everything the package manager does is fouling up, because you interrupted an installation at an inopportune moment. Finding the most convenient way to fix this depends on seeing more of the output of your package removal attempt.

As an example, consider you tried to uninstall Apache. Pretty much the first thing the package manager would probably try to do is shut down your web server, by executing **/etc/init.d/apache2 stop**. Now imagine you'd deleted that script, and that the package designers had failed to take account of that eventuality. The result would probably be exactly what you posted.

Unfortunately, "exit status 1" is returned in a wide variety of circumstances, so it doesn't give much away. Could you try the uninstallation again, and post the entire output? There may be a clue in there somewhere.

---

### Post by leptogenesis on 2007-03-28
I guess apt-get remove does give some better output:

```

user@laptop:~$ sudo apt-get remove dhcp3-relay
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dhcp3-relay dpatch
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  dhcp3-relay
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 303kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 138159 files and directories currently installed.)
Removing dhcp3-relay ...
/etc/default/dhcp3-relay does not exist! - Aborting...
Run 'dpkg-reconfigure dhcp3-relay' to fix the problem.
invoke-rc.d: initscript dhcp3-relay, action "stop" failed.
dpkg: error processing dhcp3-relay (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 dhcp3-relay
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Furthermore:

```

user@laptop:~$ sudo dpkg-reconfigure dhcp3-relay
/etc/default/dhcp3-relay does not exist! - Aborting...
Run 'dpkg-reconfigure dhcp3-relay' to fix the problem.
invoke-rc.d: initscript dhcp3-relay, action "stop" failed.

```

any help?

---

### Post by kidders on 2007-03-28
Hey again,

**Lots** of help, actually. :-) Thank you!

It seems like you have two options:

**I - Try to fool the uninstaller**
*I would try this, but only because I'm more familiar with Linux in general than I am with Debian-style package management.*

> /etc/default/dhcp3-relay does not exist! - Aborting...
You could give **sudo touch /etc/default/dhcp3-relay** a try (ie create the missing file), and see what the next error is. With luck, you would run out of errors pretty quickly, and the package removal would succeed.

**II - Follow apt's recommendation**
*If there turn out to be hundreds of problems with your half-installed application, this would be faster.*

> Run 'dpkg-reconfigure dhcp3-relay' to fix the problem.You'd need to do this as root (naturally, I suppose). In theory, the command should treat dhcp3-relay as broken, and reconfigure it, causing any files that were supposed to have been added *after* a successful installation to be rewritten.

---


> invoke-rc.d: initscript dhcp3-relay, action "stop" failed.
This means that an attempt to stop the DHCP service failed. This is done by executing **/etc/init.d/dhcp3-relay stop** as root, which the uninstaller couldn't do.

I hope this is of some help. Isn't it silly how amazingly easy it is to make a big mess sometimes!!

---

### Post by leptogenesis on 2007-03-28
> **kidders said:**
> 
**II - Follow apt's recommendation**
*If there turn out to be hundreds of problems with your half-installed application, this would be faster.*

You'd need to do this as root (naturally, I suppose). In theory, the command should treat dhcp3-relay as broken, and reconfigure it, causing any files that were supposed to have been added *after* a successful installation to be rewritten.

I actually had tried that...it didn't work.

> **kidders said:**
> 
**I - Try to fool the uninstaller**
*I would try this, but only because I'm more familiar with Linux in general than I am with Debian-style package management.*

You could give **sudo touch /etc/default/dhcp3-relay** a try (ie create the missing file), and see what the next error is. With luck, you would run out of errors pretty quickly, and the package removal would succeed.

This, however, did work.  I find it amazing...Thanks for the tip.

Unfortunately, the dhcp3-server still isn't working for some reason.  I set it up in accordance to the guide on [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy).  The server fails when I try to start it up, and /var/log/syslog contains the following information (where \*my.current.IP.address*\ is actually the address of my machine):

```

Mar 28 20:38:17 leptogenesis-laptop dhcpd: Internet Systems Consortium DHCP Server V3.0.4
Mar 28 20:38:17 leptogenesis-laptop dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Mar 28 20:38:17 leptogenesis-laptop dhcpd: All rights reserved.
Mar 28 20:38:17 leptogenesis-laptop dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Mar 28 20:38:17 leptogenesis-laptop dhcpd: Internet Systems Consortium DHCP Server V3.0.4
Mar 28 20:38:17 leptogenesis-laptop dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Mar 28 20:38:17 leptogenesis-laptop dhcpd: All rights reserved.
Mar 28 20:38:17 leptogenesis-laptop dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Mar 28 20:38:19 leptogenesis-laptop dhcpd: Internet Systems Consortium DHCP Server V3.0.4
Mar 28 20:38:19 leptogenesis-laptop dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Mar 28 20:38:19 leptogenesis-laptop dhcpd: All rights reserved.
Mar 28 20:38:19 leptogenesis-laptop dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Mar 28 20:38:19 leptogenesis-laptop dhcpd: Internet Systems Consortium DHCP Server V3.0.4
Mar 28 20:38:19 leptogenesis-laptop dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Mar 28 20:38:19 leptogenesis-laptop dhcpd: All rights reserved.
Mar 28 20:38:19 leptogenesis-laptop dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Mar 28 20:38:19 leptogenesis-laptop dhcpd: Internet Systems Consortium DHCP Server V3.0.4
Mar 28 20:38:19 leptogenesis-laptop dhcpd: Copyright 2004-2006 Internet Systems Consortium.
Mar 28 20:38:19 leptogenesis-laptop dhcpd: All rights reserved.
Mar 28 20:38:19 leptogenesis-laptop dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Mar 28 20:38:19 leptogenesis-laptop dhcpd: Wrote 0 leases to leases file.
Mar 28 20:38:19 leptogenesis-laptop dhcpd:
Mar 28 20:38:19 leptogenesis-laptop dhcpd: No subnet declaration for eth0 (\*my.current.IP.address*\).
Mar 28 20:38:19 leptogenesis-laptop dhcpd: ** Ignoring requests on eth0.  If this is not what
Mar 28 20:38:19 leptogenesis-laptop dhcpd:    you want, please write a subnet declaration
Mar 28 20:38:19 leptogenesis-laptop dhcpd:    in your dhcpd.conf file for the network segment
Mar 28 20:38:19 leptogenesis-laptop dhcpd:    to which interface eth0 is attached. **
Mar 28 20:38:19 leptogenesis-laptop dhcpd:
Mar 28 20:38:19 leptogenesis-laptop dhcpd:
Mar 28 20:38:19 leptogenesis-laptop dhcpd: Not configured to listen on any interfaces!

```

Any ideas?

---

### Post by kidders on 2007-03-28
> **leptogenesis said:**
> I actually had tried that...it didn't work.Hehe sorry... I suspected you would have, but I thought I would make the obvious suggestion anyway, just in case.

> **leptogenesis said:**
> This, however, did work.Excellent. :-) I hope you didn't have to keep **touch**-ing files for too long though! For future reference, try to think of package operations as atomic actions. They're not designed to be interrupted, so on many distros (Ubuntu included) cleaning up the mess can be quite irritating.

> **leptogenesis said:**
> Mar 28 20:38:19 leptogenesis-laptop dhcpd: No subnet declaration for eth0 (\*my.current.IP.address*\).
> **leptogenesis said:**
> Mar 28 20:38:19 leptogenesis-laptop dhcpd: Not configured to listen on any interfaces!Strictly speaking, I suppose this belongs in a separate thread, but let's try anyway. (Thanks again for the detailed error message by the way.)

The most important thing here is to make sure (assuming the IP you removed is a _public_ one) that the message about no subnet being assigned to that interface continues to appear in your logs. It would not be a good thing to expose a DHCP server to the outside world.

The real error message is the last line. Basically, you are trying to start a DHCP server, but you haven't told it to do anything, so it just dies.

I'm going to make a few assumptions, so be sure to tell me if any of them is wrong:

[LIST=1]
[*]You are planning to run a DHCP server on your Ubuntu box to make network configuration more straightforward for the rest of your LAN.
[*]Your Ubuntu box has direct access to the internet, but nothing else on your LAN does.
[*]Your Ubuntu box has two network cards, one connected to the world, and the other to your network.
[*]The one connected to your network has a manually configured static IP.
[*]You are running a firewall on your Ubuntu box.
[/LIST]

If all this is true, make sure your DHCP server config file contains a section like this...

```
subnet 192.168.8.0 netmask 255.255.255.0 {
     ...
     ...
}
```... where the subnet and netmask correspond to those you assigned manually to your internal network interface. Then, use **ifconfig** to check that the interface is actually alive. Provided there are no further errors, your DHCP server should start for you.

If any of the assumptions I made is wrong, getting your DHCP server up and running may be slightly more complicated, but that's okay.

---

### Post by leptogenesis on 2007-03-28
> **kidders said:**
> (assuming the IP you removed is a _public_ one)

It is.

> **kidders said:**
> 
[LIST=1]
[*]You are planning to run a DHCP server on your Ubuntu box to make network configuration more straightforward for the rest of your LAN.
[*]Your Ubuntu box has direct access to the internet, but nothing else on your LAN does.
[*]Your Ubuntu box has two network cards, one connected to the world, and the other to your network.
[*]The one connected to your network has a manually configured static IP.
[*]You are running a firewall on your Ubuntu box.
[/LIST]


Not quite.  Here's the story: I have two network cards; one works with wireless, and the other is wired.  Under normal circumstances, I don't have a LAN - I keep my wireless interface (eth1) unconfigured and I have my wired (eth0) connected to the internet.  On occasion, when I don't have access to wired internet, I'll use the wireless.

However, very often I want to send large files to other random computers.  It would make my life a lot easier if I could just plug another computer into my own and have them connect automatically with DHCP (I have a lightweight server application already installed).  Most often, I don't have my wireless interface configured when I'm doing this, but sometimes I do.  

Not quite sure what computer you're referring to with the static IP...My computer doesn't, and the idea is that I won't have to mess around with the other computers connecting to me very much.  I'm pretty sure my ISP has a static IP address, though...

As for the firewall, I have iptables, which I haven't changed since I installed Ubuntu.  

Just in case it helps, here's my /etc/dhcp3/dhcpd.conf file:

```

#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
#option domain-name "example.org";
#option domain-name-servers ns1.example.org, ns2.example.org;

#default-lease-time 600;
#max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
subnet 192.168.0.0 netmask 255.255.255.0 {
 range 192.168.0.100 192.168.0.200;
 option domain-name-servers 202.188.0.133, 202.188.1.5;
 option domain-name "tm.net.my";
 option routers 192.168.0.1;
 option broadcast-address 192.168.0.255;
 default-lease-time 600;
 max-lease-time 7200;
}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}


```

Come to think of it, I guess an internal subnet doesn't really make much sense in my case...

---

### Post by kidders on 2007-03-28
It's sounding like you haven't gotten your wireless network working yet (even with manual configuration). If that's true, DHCP is a little bit down the track yet.

Either way, here's a little bit of background...

> **leptogenesis said:**
> Come to think of it, I guess an internal subnet doesn't really make much sense in my case.Actually, it does. Even though your network is small (one to two devices), you still need to think of it as though it had hundreds of computers in it.

[LIST]
[*]You need to pick yourself a subnet. You seem to have chosen 192.168.0.0/24.
[*]You need to set your wireless LAN card to master mode, disable any DHCP *client* functionality and manually assign it an IP in your subnet.
[*]Then, assuming you'll want your cliient computer to have access to the internet through your Ubuntu box, you'll need to configure IP packet forwarding and set up masquerading.
[*]The wireless interface needs to be up before the DHCP server starts.
[/LIST]

Next comes the DHCP configuration. The config file you posted is rudimentary (I've posted it back with all the comments taken out, so you can get a better picture of it), but it may well work as is. One of the things you may need to check is that DNS is (a) deliberately misconfigured in the event you *don't* want to provide DHCP clients with internet access, to address a minor privacy issue, or (b) configured correctly, in the event you *do*.

```
ddns-update-style none;
log-facility local7;

subnet 192.168.0.0 netmask 255.255.255.0 {
 range 192.168.0.100 192.168.0.200;
 option domain-name-servers 202.188.0.133, 202.188.1.5;
 option domain-name "tm.net.my";
 option routers 192.168.0.1;
 option broadcast-address 192.168.0.255;
 default-lease-time 600;
 max-lease-time 7200;
}
```

So, I guess my first question is how far you have gotten with the underlying network configuration so far, DHCP aside.

---

### Post by leptogenesis on 2007-03-28
> **kidders said:**
> It's sounding like you haven't gotten your wireless network working yet (even with manual configuration). If that's true, DHCP is a little bit down the track yet.

It's not that I can't configure it...Right now I'm living at Carnegie Mellon University - and so there's some things to take into consideration when using the internet:

First, I have access to wireless pretty much everywhere, and wired connections are available in some places.  I have bandwidth quotas, which are larger for wired connections, so I try to use wired whenever I can.

Second, Carnegie Mellon says it is its own ISP...I think that means that, if I'm connected to the Carnegie Mellon network, it means my IP address on the Carnegie Mellon network is the same as my IP address on the world wide web.  But also, I've tried connecting to the Carnegie Mellon network with both interfaces at the same time.  It doesn't work.  I can do one or the other, but not both (at least, not on dapper...haven't tried it with edgy yet).  I think it has something to do with the way the IP standards are set up, that you can't have multiple connections to the same network with one address.

> **kidders said:**
> 
So, I guess my first question is how far you have gotten with the underlying network configuration so far, DHCP aside.

I'm not really sure how to answer that question.  Right now, there is no LAN and I don't want one...it's just my computer connected to Carnegie Mellon's network.  However, when I do want one (that is, I want to send files to some other random computer), thus far I've just been doing it with static IP addresses (configure both computers to use a static IP address, hook them together, and if all goes well, they can communicate).

---

### Post by kidders on 2007-03-29
Ah I see. So are you using an ad hoc network, or is one of your cards in master mode? The best way to get DHCP up and running quickly kinda depends on the specifics of your current configuration.

Now that I know more about what you're doing, I should be able to be a bit more precise with my setup suggestions. Try this...

[LIST=1]
[*]Shut down all networking on your Ubuntu box (just to keep things simple for the moment, in case something goes funny).
[*]Manually bring up your wireless card, and assign an IP manually as you normally would.
[*]Make sure your wireless network settings and your DHCP server configuration agree on what your subnet & netmask is.
[*]Try to start the DHCP server. Assuming it stays up, see if another computer will talk to it.
[/LIST]

If that much works with your current configuration the way it is, we're in luck. The only remaining task would be to find a way to turn the server on and off easily, in a way that doesn't conflict with other things you might like to do with your Ubuntu box's wireless card.

> **leptogenesis said:**
> But also, I've tried connecting to the Carnegie Mellon network with both interfaces at the same time.  It doesn't work.That's odd. I can't think of a reasonable explanation for that one!

**Edit:** An alternative strategy that might work would be to connect both machines to your university LAN, and share files that way. Is there a reason you haven't gone for that option?

---

### Post by leptogenesis on 2007-03-29
> **kidders said:**
> Ah I see. So are you using an ad hoc network, or is one of your cards in master mode? The best way to get DHCP up and running quickly kinda depends on the specifics of your current configuration.

I don't think so...remember, I'm doing this over a wired connection. I'm just running an ethernet cable between the two boxes.

> **kidders said:**
> 
Now that I know more about what you're doing, I should be able to be a bit more precise with my setup suggestions. Try this...


I can't right now...hopefully I'll get to it tomorrow.  But I can tell you my questions, just so I'm clear on the procedure:

> **kidders said:**
> Shut down all networking on your Ubuntu box (just to keep things simple for the moment, in case something goes funny).

Is just going into System>Administration>Networking and unconfiguring all my connections enough, or is there something in particular?

> **kidders said:**
> Manually bring up your wireless card, and assign an IP manually as you normally would.

Does this mean I'll have to manually create a static IP address for my box each time I want to quickly set up a LAN?

> **kidders said:**
> Make sure your wireless network settings and your DHCP server configuration agree on what your subnet & netmask is.

How can I tell that the DHCP server has the same settings...i.e. which number should I be looking at in the config file?[/QUOTE]

> **kidders said:**
> That's odd. I can't think of a reasonable explanation for that one!

Actually, I just tried it again with edgy, and it seems to be working (although, as a side note, I'd kinda like to know which interface it's using by default...the bandwidth quotas are different for different connection methods)

> **kidders said:**
> **Edit:** An alternative strategy that might work would be to connect both machines to your university LAN, and share files that way. Is there a reason you haven't gone for that option?

Bandwidth quotas and logistics mostly...it works in some cases, but not usually.  Plus, sometimes when I do this I'm not at Carnegie Mellon.

btw...isn't it like 4 in the  morning in Dublin right now?  If so, then I have found gained another reason to admire you :D

---

### Post by kidders on 2007-03-29
> **leptogenesis said:**
> I'm doing this over a wired connection. I'm just running an ethernet cable between the two boxes.Oh hell... for some reason I had assumed you'd be using your wired connection to plug into your university LAN, and your wireless card to share data with your other machines. Oops... sorry. (Using wires makes life much more straightforward!)

> **leptogenesis said:**
> Is just going into System>Administration>Networking and unconfiguring all my connections enough, or is there something in particular?I'm not sure... whatever trick you know that has the effect of bringing interfaces down will do (**ifconfig** will tell you interface status). You should also kill any network managers that might fight with you when you start to reconfigure things.

> **leptogenesis said:**
> Does this mean I'll have to manually create a static IP address for my box each time I want to quickly set up a LAN?Yes. We should be able to find a quick & convenient way of doing it though, so don't worry.

First up might be to do a **sudo ifconfig eth0 192.168.0.100 netmask 255.255.255.0 up**, and then make sure that the DHCP server configuration matches that setup. The one you posted defines a subnet at 192.168.0.0/24, which *would* match.

What happens, you see, is that the DHCP server will only bind itself to network interfaces on subnets mentioned in the configuration file.

> **leptogenesis said:**
> btw...isn't it like 4 in the  morning in Dublin right now?  If so, then I have found gained another reason to admire you :DLol yes it was... unfortunately, I got sleepy and went to bed though... sorry.

---

### Post by leptogenesis on 2007-04-09
> **leptogenesis said:**
> I can't right now...hopefully I'll get to it tomorrow. 

A day...a week...same difference...

I finally got my act together and set it up, and it seems to be working for the most part: I used the following configuration: 

```

ddns-update-style none;

subnet 192.168.1.0 netmask 255.255.255.0 {
 range 192.168.1.100 192.168.1.255;
 option domain-name-servers 202.188.0.133, 202.188.1.5;
 option domain-name "tm.net.my";
 option routers 192.168.1.1;
 option broadcast-address 192.168.1.255;
 default-lease-time 600;
 max-lease-time 7200;
}

```

Turned off my wireless card, restarted my wired card with ip address 192.168.1.201, and connected two computers.  The second computer found a dhcp server at 192.168.1.201 and was assigned an ip address.  Unfortunately, they didn't communicate - I have a tomcat server running on port 8080, but typing [http://192.168.1.201:8080/](http://192.168.1.201:8080/) into Firefox on the other computer got a server-not-found error.  I suspect it's a firewall issue; I have relatively little experience with iptables, so I can't be sure of what's going on.  I haven't changed any iptables configurations since I installed Ubuntu.

---

### Post by kidders on 2007-04-09
Hmm... that's odd. What happens if you try to **ping** & **nmap** 192.168.1.201? Have you verified that the tomcat server is, in fact running, and bound to the correct network interface?

---

### Post by leptogenesis on 2007-04-10
> **kidders said:**
> What happens if you try to **ping** & **nmap** 192.168.1.201?

The ping request times out...nmap isn't installed on the other box (it's Windows).  Does 'routers' maybe need to be specified?  Right now, 192.168.1.1 doesn't point to anything, nor does 192.168.1.255...

---

### Post by kidders on 2007-04-10
Yep. If 192.168.1.1 doesn't exist, then you should correct that.

If that doesn't change anything, it might be worth posting your iptables configuration ... just in case there's anything strange in there.

---

### Post by leptogenesis on 2007-04-10
> **kidders said:**
> Yep. If 192.168.1.1 doesn't exist, then you should correct that.

Changed my configuration to:

```

subnet 192.168.1.0 netmask 255.255.255.0 {
 range 192.168.1.100 192.168.1.255;
 option domain-name-servers 202.188.0.133, 202.188.1.5;
 option domain-name "tm.net.my";
 option routers 192.168.1.201;
 option broadcast-address 192.168.1.255;
 default-lease-time 600;
 max-lease-time 7200;
}

```

It didn't help - I'm still getting a timeout on the ping.  Not quite sure if that's what you meant by a correction, though - there's no router on this network.  Do I need software that will handle routing requests or something?

> **kidders said:**
> If that doesn't change anything, it might be worth posting your iptables configuration ... just in case there's anything strange in there.

I don't think I have an iptables configuration file...all I can give you is the output of iptables-save:

```

leptogenesis@leptogenesis-laptop:/etc$ sudo /sbin/iptables-save
# Generated by iptables-save v1.3.5 on Tue Apr 10 01:07:15 2007
*filter
:INPUT ACCEPT [68882:19605949]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [5819:1074245]
COMMIT
# Completed on Tue Apr 10 01:07:15 2007

```

---

### Post by kidders on 2007-04-10
That's a little better. :-) You should notice your DHCP clients' default route change. Also (but this isn't the cause of your problems) you should change **range 192.168.1.100 192.168.1.255** to **range 192.168.1.100 192.168.1.200**, so the DHCP server won't try to assign 192.168.1.201 or 192.168.1.255 to anyone.


> **leptogenesis said:**
> Do I need software that will handle routing requests or something?You don't need to worry about packet routing too much, unless you want DHCP clients to be able to access other computers through the server ... in which case, iptables is all you need.

What does **sudo iptables -L** have to say? (Perhaps not much.)

---

### Post by leptogenesis on 2007-04-10
> **kidders said:**
> Also (but this isn't the cause of your problems) you should change **range 192.168.1.100 192.168.1.255** to **range 192.168.1.100 192.168.1.200**, so the DHCP server won't try to assign 192.168.1.201 or 192.168.1.255 to anyone.

Actually, it might have been...the server was assigning 192.168.1.255 to the other computer.  I haven't tested it with the new configuration yet, though.

> **kidders said:**
> What does **sudo iptables -L** have to say? (Perhaps not much.)

```

leptogenesis@leptogenesis-laptop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    

```

---

### Post by kidders on 2007-04-10
> **leptogenesis said:**
> Actually, it might have been...the server was assigning 192.168.1.255 to the other computer. Ah. That would make a terrible mess!

---

### Post by leptogenesis on 2007-04-22
Alright - I finally got a chance to test it with that configuration, and everything seems to be working fine!  Now the only question is how to make it quick to switch between configurations (i.e. I'd like to boot in a mode such that I am connected to the internet with the DHCP server off, then I'd like to be able to unplug the wire and quickly turn my computer into a DHCP server, then change it back.)  I assume it'd be easiest to do this with a script.  So, unless you have any further recommendations for me, I guess I'll get coding.

Thanks for all your help!

---

### Post by kidders on 2007-04-22
Hey there,

> **leptogenesis said:**
> I assume it'd be easiest to do this with a script.  So, unless you have any further recommendations for me, I guess I'll get coding.Yep... that's the way to do it. It *may* be possible to inject a certain amount of automation into the switch-over though, by exploiting the scripts in places like /etc/network/ to trap certain events, like a network cable being unplugged.

The other approach would simply be to create something you can double-click, to make the switch happen at will.

In either case, don't forget to pay particular attention to the order in which things happen. As a simple example, the DHCP server shouldn't start until all your network interfaces are reconfigured ... and it should be among the first things that gets killed, when you're switching back again.

---

### Post by A$h X on 2007-08-21
[FONT="Tahoma"]Apologies for bumping an old thread and not starting my own, but the problem the OP had seems *sort of* similar to mine.
Bascially i'm dual-booting and have configured a static IP on win XP and have setup a home network with 2 other machines. It works fine in both XP and Ubuntu BUT once I reboot after using Ubuntu and go back into XP, "My network places" hangs, saying "mshome is not available" etc. I look in my LAN connection properties and it seems nothing has changed. I still have net access from XP but no home network. I figured out how to solve the problem in XP:

From command prompt type-
netsh winsock reset
then
netsh int ip reset resetip.txt

After a reboot straight into XP the home network re-appears and everything's fine. UNTIL I boot into Ubuntu.

I suspect that Ubuntu isn't configured to use a static IP is using DHCP instead, which might cause a conflict via changing my NIC settings. Any suggestions or comments?[/FONT]

---

