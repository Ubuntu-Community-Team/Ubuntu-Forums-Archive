---
title: "[resolved] Where should I put iptables file?"
date: 2004-12-21
forum: Installation &amp; Upgrades
---

### Post by richpri on 2004-12-21
I have created an iptables file for my ubuntu server but I can't figgure out where it goes!  For RedHat it would go in /etc/sysconfig/iptables.  Where does it go under ubuntu?

---

### Post by richpri on 2004-12-24
My research so far indicates that iptables is not even started when the system boots!

This fact [allong with some other problems with things like writing CD's]
Has caused me to decide that using UBUNTU for my server is a bad idea.

Since I am shifting to another distribution I am closing this question.

Thanks for all the help!  Goodby  ;-)>

---

### Post by AhhGeez on 2004-12-24
Try this(to load iptables):
#!/bin/sh
# This is the script to load our iptables rules for  blocking access
# to the computer. It is based on "Rusty's Really Quick Guide to Packet
# Filtering," from the Packet Filtering HOWTO.
# This file should be placed in /etc/ppp/ip-up.d
# Flush out all the rules in the chain;
# Create the chain which blocks new connections, except those coming from my side of the netork.
# Establish the rules

if [ -x /sbin/iptables ]; then

iptables -F
iptables -N block
iptables -A block -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A block -m state --state NEW -i ! ppp0 -j ACCEPT
iptables -A block -j DROP

## Jump to that chain from INPUT and FORWARD chains.
iptables -A INPUT -j block
iptables -A FORWARD -j block

fi

This script will run iptables as soon as your PPP connection is established.

## This will verify that the file loaded correctly:

## Type 'run-parts --test /etc/ppp/ip-up' and press the Enter key
## to get past any non-iptables error messages. Then (as root) type the
## command iptables -L and you should see your rules listed.


And this to unload iptables:

#!/bin/sh
# This is the script to remove our iptables rules for  blocking access
# to the computer. It is based on "Rusty's Really Quick Guide to Packet
# Filtering," from the Packet Filtering HOWTO.
# This file should be placed in /etc/ppp/ip-down.d

## Flush all the chains ansd remove the "block" chain.

if [ -x /sbin/iptables ]; then

iptables -F
iptables -X block

fi

Hope this helps


AhhGeez

---

