---
title: "Error when installing VPN Book"
date: 2015-10-05
forum: Installation &amp; Upgrades
---

### Post by erikasland87 on 2015-10-05
I am attempting to install VPN Book and am hitting a wall. I have no idea what any of this code means and could use some help. Thank you!

```
alopex@alopex-TH55-HD:~/vpnbook$ openvpn --config vpnbook-euro1-tcp443.ovpn
Mon Oct  5 18:39:55 2015 OpenVPN 2.3.2 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Dec  1 2014
Enter Auth Username:vpnbook
Enter Auth Password:
Mon Oct  5 18:40:01 2015 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Mon Oct  5 18:40:01 2015 NOTE: --fast-io is disabled since we are not using UDP
Mon Oct  5 18:40:01 2015 Socket Buffers: R=[87380->131072] S=[16384->131072]
Mon Oct  5 18:40:01 2015 Attempting to establish TCP connection with [AF_INET]176.126.237.217:443 [nonblock]
Mon Oct  5 18:40:02 2015 TCP connection established with [AF_INET]176.126.237.217:443
Mon Oct  5 18:40:02 2015 TCPv4_CLIENT link local: [undef]
Mon Oct  5 18:40:02 2015 TCPv4_CLIENT link remote: [AF_INET]176.126.237.217:443
Mon Oct  5 18:40:02 2015 TLS: Initial packet from [AF_INET]176.126.237.217:443, sid=7498d2ac 6ae84210
Mon Oct  5 18:40:02 2015 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Mon Oct  5 18:40:06 2015 VERIFY OK: depth=1, C=CH, ST=Zurich, L=Zurich, O=vpnbook.com, OU=IT, CN=vpnbook.com, name=vpnbook.com, emailAddress=admin@vpnbook.com
Mon Oct  5 18:40:06 2015 VERIFY OK: depth=0, C=CH, ST=Zurich, L=Zurich, O=vpnbook.com, OU=IT, CN=vpnbook.com, name=vpnbook.com, emailAddress=admin@vpnbook.com
Mon Oct  5 18:40:09 2015 Data Channel Encrypt: Cipher 'AES-128-CBC' initialized with 128 bit key
Mon Oct  5 18:40:09 2015 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Oct  5 18:40:09 2015 Data Channel Decrypt: Cipher 'AES-128-CBC' initialized with 128 bit key
Mon Oct  5 18:40:09 2015 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Oct  5 18:40:09 2015 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Mon Oct  5 18:40:09 2015 [vpnbook.com] Peer Connection Initiated with [AF_INET]176.126.237.217:443
Mon Oct  5 18:40:11 2015 SENT CONTROL [vpnbook.com]: 'PUSH_REQUEST' (status=1)
Mon Oct  5 18:40:11 2015 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1,dhcp-option DNS  89.233.43.71,dhcp-option DNS  91.239.100.100,route 10.9.0.1,topology net30,ping 5,ping-restart 30,ifconfig 10.9.1.122 10.9.1.121'
Mon Oct  5 18:40:11 2015 OPTIONS IMPORT: timers and/or timeouts modified
Mon Oct  5 18:40:11 2015 OPTIONS IMPORT: --ifconfig/up options modified
Mon Oct  5 18:40:11 2015 OPTIONS IMPORT: route options modified
Mon Oct  5 18:40:11 2015 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Mon Oct  5 18:40:11 2015 ROUTE_GATEWAY 192.168.1.1/255.255.255.0 IFACE=eth0 HWADDR=00:30:67:57:76:b1
Mon Oct  5 18:40:11 2015 ERROR: Cannot ioctl TUNSETIFF tun1: Operation not permitted (errno=1)
Mon Oct  5 18:40:11 2015 Exiting due to fatal error
```

---

### Post by mitmag on 2016-04-09
I had the same problem! Use sudo command! You must be root!
But now I have a different problem! VPNBook is not updating my IP address!
What's up with that?

---

