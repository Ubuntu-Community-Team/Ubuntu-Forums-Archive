---
title: "OPENVPN help"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by moos3 on 2007-12-14
I can' get the daemon to run it gives this for a error:

moos3@tibby:~$ sudo /etc/init.d/openvpn start
Starting virtual private network daemon: client(FAILED) server(FAILED).
server.conf
```

# VPN Port
port 1194

# Local address
local 192.168.1.159

# Protocol for VPN
proto tcp

# Ethernet routing
dev tap0

# Key location
ca keys/ca.crt
cert keys/server.crt
key keys/server.key

# Diffie hellman Parameters
dh keys/dh2048.pem

# VPN DHCP Pool
server 10.8.1.0 255.255.255.0

# Gateway Push
push "route 192.168.1.0 255.255.255.0"

# VPN static IP address Pool
ifconfig-pool-persist client-ips.txt

# Keepalive
keepalive 10 120

# More cryptographic cipher options
cipher AES-128-CBC

# Compression
comp-lzo

# OpenVPN priv after init
user nobody
group nobody

presist-key
persist-tun

# Output a short status
status openvpn-status.log

# Logging information
log openvpn

verb 3
mute 20

```

client.conf(on server)
```


# Specify that we are a client and that we
# will be pulling certain config file directives
# from the server.
client

# Use the same setting as you are using on
# the server.
# On most systems, the VPN will not function
# unless you partially or fully disable
# the firewall for the TUN/TAP interface.
dev tap

# Windows needs the TAP-Win32 adapter name
# from the Network Connections panel
# if you have more than one.  On XP SP2,
# you may need to disable the firewall
# for the TAP adapter.
dev-node MyTap

# Are we connecting to a TCP or
# UDP server?  Use the same setting as
# on the server.
proto tcp

# Keep trying indefinitely to resolve the
# host name of the OpenVPN server.  Very useful
# on machines which are not permanently connected
# to the internet such as laptops.
resolv-retry infinite

# Most clients don't need to bind to
# a specific local port number.
nobind

# Try to preserve some state across restarts.
persist-key
persist-tun

# SSL/TLS parms.
# See the server config file for more
# description.  It's best to use
# a separate .crt/.key file pair
# for each client.  A single ca
# file can be used for all clients.
ca ca.crt
cert client.crt
key client.key

# Select a cryptographic cipher.
# If the cipher option is used on the server
# then you must also specify it here.
cipher aes-128-cbc

# Enable compression on the VPN link.
# Don't enable this unless it is also
# enabled in the server config file.
comp-lzo

# Set log file verbosity.
verb 3

# Silence repeating messages
mute 20

```

i have made all the keys and and they are located in /etc/openvpn/keys/   Any Ideas?

---

### Post by Deus42 on 2007-12-14
Hmm, could I get some more information on what is failing?

First, is this an openvpn server, or a client?

Next, to get more information, make sure that openvpn is not running (ps ax | grep openvpn), then run openvpn --config /path/to/server.conf --verb 3

this will run the server attached to your current console. Post the output here. 

I can also send you my config files if you want (we use openvpn extensively here).

---

### Post by moos3 on 2007-12-14
I figure it out to the point of Starting virtual private network daemon: client(OK) server(FAILED) Earlier is was the client.conf I believe its something to my server.conf runing those commands now will post results

---

### Post by moos3 on 2007-12-14
something to do with line 43: presist-key its not liking

---

### Post by moos3 on 2007-12-14
actucal error is this

Options error: Unrecognized option or missing parameter(s) in /etc/openvpn/server.conf:43: presist-key (2.0.9)
Use --help for more information.

---

### Post by moos3 on 2007-12-14
ok Now I just need to figure out this set of messages

moos3@tibby:/etc/openvpn/keys$ openvpn --config /etc/openvpn/server.conf --verb 3
Fri Dec 14 13:41:52 2007 Warning: Error redirecting stdout/stderr to --log file: openvpn: Permission denied (errno=13)
Fri Dec 14 13:41:52 2007 OpenVPN 2.0.9 i486-pc-linux-gnu [SSL] [LZO] [EPOLL] built on Mar  2 2007
Fri Dec 14 13:41:52 2007 Note: cannot open openvpn-status.log for WRITE
Fri Dec 14 13:41:52 2007 Note: cannot open client-ips.txt for READ/WRITE
Fri Dec 14 13:41:53 2007 Diffie-Hellman initialized with 2048 bit key
Fri Dec 14 13:41:53 2007 WARNING: file '/etc/openvpn/keys/server.key' is group or others accessible
Fri Dec 14 13:41:53 2007 TLS-Auth MTU parms [ L:1592 D:140 EF:40 EB:0 ET:0 EL:0 ]
Fri Dec 14 13:41:53 2007 Note: Cannot open TUN/TAP dev /dev/net/tun: Permission denied (errno=13)
Fri Dec 14 13:41:53 2007 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Fri Dec 14 13:41:53 2007 Cannot allocate TUN/TAP dev dynamically
Fri Dec 14 13:41:53 2007 Exiting
moos3@tibby:/etc/openvpn/keys$

---

### Post by Deus42 on 2008-01-04
It looks like you are not running it as root.

You need to launch openvpn as root so that it can create a new interface.

try adding a sudo in front of your openvpn line.

P.S. Sorry for the late response.

---

