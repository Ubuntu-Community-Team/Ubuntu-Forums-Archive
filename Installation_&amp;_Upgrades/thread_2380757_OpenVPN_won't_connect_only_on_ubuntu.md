---
title: "OpenVPN won't connect only on ubuntu"
date: 2017-12-21
forum: Installation &amp; Upgrades
---

### Post by seyahdoo on 2017-12-21
Hello,

I'm trying to connect to my OpenVPN server in cloud.

On my previous server I used this script to install [https://github.com/Angristan/OpenVPN-install ]("https://github.com/Angristan/OpenVPN-install")
and it did connected successfully on my Ubuntu 16.04 machine.


But i wanted to use docker, So i reinstalled it using [URL="https://github.com/kylemanna/docker-openvpn"]https://github.com/kylemanna/docker-openvpn
[/URL]
I can connect to new server with my android phone. But i cant connect to new server using my Ubuntu 16.04 machine.


Here is a log of openvpn connection. On Ubuntu 16.04 Machine

```
seyahdoo@yogalap:~/Documents/KEYS/openvpn-docker$ sudo openvpn svpn-yogalap.ovpn 
Thu Dec 21 20:39:53 2017 OpenVPN 2.3.10 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Jun 22 2017
Thu Dec 21 20:39:53 2017 library versions: OpenSSL 1.0.2g  1 Mar 2016, LZO 2.08
Thu Dec 21 20:39:53 2017 Control Channel Authentication: tls-auth using INLINE static key file
Thu Dec 21 20:39:53 2017 UDPv4 link local: [undef]
Thu Dec 21 20:39:53 2017 UDPv4 link remote: [AF_INET]35.158.125.0:1194
Thu Dec 21 20:39:53 2017 WARNING: this cipher's block size is less than 128 bit (64 bit).  Consider using a --cipher with a larger block size.
Thu Dec 21 20:39:53 2017 WARNING: this cipher's block size is less than 128 bit (64 bit).  Consider using a --cipher with a larger block size.
Thu Dec 21 20:39:53 2017 [vpn.seyahdoo.com] Peer Connection Initiated with [AF_INET]35.158.125.0:1194
Thu Dec 21 20:39:56 2017 Options error: Unrecognized option or missing parameter(s) in [PUSH-OPTIONS]:1: block-outside-dns (2.3.10)
Thu Dec 21 20:39:56 2017 TUN/TAP device tun0 opened
Thu Dec 21 20:39:56 2017 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Thu Dec 21 20:39:56 2017 /sbin/ip link set dev tun0 up mtu 1500
Thu Dec 21 20:39:56 2017 /sbin/ip addr add dev tun0 local 192.168.255.10 peer 192.168.255.9
Thu Dec 21 20:39:56 2017 Initialization Sequence Completed
```

What could have been going wrong?

---

### Post by TheFu on 2017-12-22
The error is there:
```
Options error: Unrecognized option or missing parameter(s) in [PUSH-OPTIONS]:1: block-outside-dns (2.3.10)
```

If you aren't actively using ipv6, it is recommended to disable it.  This is a known issue.

I would recommend NOT using 192.168.x.x subnets.  Though it shouldn't matter, the 10.x.x.x subnets are generally wide open and are much less likely to cause routing issues due to subnet collisions.  

If you want more help, post both the server-side config and the client-side config files.  Obviously, strip any private certs before posting.

---

### Post by seyahdoo on 2017-12-23
Thanks for help,

I deleted that the corresponding line from docker image config. And tried again after i restarted the container.

But no luck. The error you mentioned went away but i still wasn't able to connect to internet via VPN.

So i ditched the docker and installed using [this]("https://github.com/Nyr/openvpn-install") script.

It works fine now. Thanks for your help ^^

---

### Post by TheFu on 2017-12-24
Docker networking is something I've never dealt with. Sorry. I don't use docker. A quick look makes me think you just need to tell the container manager to pass the specific port needed through to the container.

---

