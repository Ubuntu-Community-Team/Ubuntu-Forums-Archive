---
title: "Firewall"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by Satendra.kohli on 2009-12-04
Which firewall best for ubuntu 9.10.

---

### Post by Soul-Sing on 2009-12-04
for a non server environment? Maybe GUFW.
But please take some time to read this: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by mkvnmtr on 2009-12-04
In my experience the firewall that is installed by default. You do not even have to think about it, It just works. When I tried to install apps to control the firewall it just brought me problems. I believe it is called IPtables if you wish to research it. I would recommend that you do not alter it if you do not have a very good reason and understand completely what you are doing.

---

### Post by dvlchd3 on 2009-12-04
iptables is the best firewall arguably for any linux machine.  However, it is extremely difficult to setup, but highly configurable and customizable.
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

If this is not your forte, try ufw (uncomplicated firewall) which uses iptables.  Or the gui version of this gfw.  Also, Firestarter is nice, however, kind of out of date and a dying project...  Firestarter also uses iptables, but makes it much easier on you to set it up.

Here's my firewall script for my laptop (using iptables).  It keeps you rather invisible on the network (cannot ping, only detectable by network activity and stealth scans, however, stealth scans take FOREVER...which is a good thing!)  This script should be placed in /etc/network/if-up.d/ folder and cannot have any '.' in the name. (you can just name it 'firewall' if you'd like)  Also, make sure you make it executable and preferably owned by root.
```

#!/bin/bash

## Firewall script for BRICKMAN using iptables
## This script meant to be executed from /etc/network/if-up.d/
############################################################
# Copyright (C) 2009 Dan Buhrman
#
#  Permission to use, copy, modify, and distribute this software and its
#  documentation for educational, research, private and non-profit purposes,
#  without fee, and without a written agreement is hereby granted. 
#  This software is provided as an example and basis for individual firewall
#  development.  This software is provided without warranty.
#
#  Any material furnished by Dan Buhrman is furnished on an 
#  "as is" basis.  He makes no warranties of any kind, either expressed 
#  or implied as to any matter including, but not limited to, warranty 
#  of fitness for a particular purpose, exclusivity or results obtained
#  from use of the material.
#
# This script is based off of Robert Ziegler's rc.firewall script
###########################################################

# Get IP address since we are dynamically assigned it.
# Change wlan0 to your network interface:
### Enable this if DHCP is screwed up by this script.
### Also enable last few lines of this script as well.
#IPADDR="`/sbin/ifconfig wlan0 | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`"

# Remove any existing rules from all chains
iptables --flush
iptables -t nat --flush
iptables -t mangle --flush

# Set the default filter table policy
iptables --policy INPUT DROP
iptables --policy OUTPUT ACCEPT
iptables --policy FORWARD DROP

# Remove any pre-existing user-defined chains
iptables --delete-chain
iptables -t nat --delete-chain
iptables -t mangle --delete-chain

# Unlimited traffic on the loopback interface
iptables -A INPUT -i lo -j ACCEPT

#############################################################
# Using Connection State to By-pass Rule Checking

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#############################################################

###########################################################
# DHCP test 
### Only enable if DHCP is screwed up by this script.
### Also enable line at beginning of script.
#
#iptables -A INPUT -p udp -s 0.0.0.0 --sport 67 \
#	-d 255.255.255.255 --dport 68 -j ACCEPT
#iptables -A INPUT -p udp -s 192.168.1.1 --sport 67 \
#	-d 255.255.255.255 --dport 68 -j ACCEPT
#iptables -A INPUT -p udp -s 192.168.1.1 --sport 67 \
#	--dport 68 -j ACCEPT
#iptables -A INPUT -p udp -s 192.168.1.1 --sport 67 \
#	-d $IPADDR --dport 68 -j ACCEPT
#
##########################################################

```

---

### Post by dvlchd3 on 2009-12-04
> **mkvnmtr said:**
> In my experience the firewall that is installed by default. You do not even have to think about it, It just works. When I tried to install apps to control the firewall it just brought me problems. I believe it is called IPtables if you wish to research it. I would recommend that you do not alter it if you do not have a very good reason and understand completely what you are doing.

Ubuntu technically has no firewall by default.  See the output of
```

sudo iptables -L

```
You will notice everything is wide-open.

The reason being this provides for the best possible functionality.  If you close all the ports by default, the user would have to open ports as needed when they install new software.

Information security: Security is inversely proportional to usability and functionality.  In other words, the more secure something is, typically the less usable or functional it is.  The most secure computer in the world is the one that is turned off, and unplug from the outlet.

---

### Post by paspantou on 2009-12-11
Hi Guys....!!!
Sorry for my english but i'm from greece so i don't speak(write?) english very well!!!
I had installed firestarter but for some reasons i uninstalled it, and since i did that every time i log-in ubuntu 9.10 i don't have access to the internet...!!
So i restore iptables to their first state whith some commands:

Chain INPUT (policy ACCEPT)
target prot opt source destination

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination

and then i save them with sudo iptables-save
# Generated by iptables-save v1.4.4 on Fri Dec 11 12:15:29 2009
*filter
:INPUT ACCEPT [6423:7463650]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [4841:722130]
COMMIT
# Completed on Fri Dec 11 12:15:29 2009

But after restart then problem returns and the iptables -L gives me other settings..not the one i saved....

Any Sugestions?????

---

