---
title: "Barry via ppa (karmic)"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ShizzlePDX503 on 2009-10-12
hello I am wanting to install Barry for Karmic (9.10). I have successfully added the ppa to my software sources. I just want to know where do I go from this point. Preferably console steps to take cause I am still learning linux

the link to the ppa that I added is: [https://launchpad.net/~doctormo/+archive/barry-snapshot]("https://launchpad.net/%7Edoctormo/+archive/barry-snapshot") 

it is barry for karmic 9.10 so I wanted to try it out.

Thanks!

btw I am using 64bit version of ubuntu karmic 9.10

---

### Post by ShizzlePDX503 on 2009-10-12
Oh I just figured it out. I ended up using the Synaptic Package Manager. Though if anyone knows how I would do this with just using the console that would be great.

Thanks

---

### Post by timgood on 2009-10-13
Once you have the PPA installed, the key imported and the sources updated, simply open a console and type: sudo apt-get install barry

Enter your password when prompted.

Job done!

---

### Post by ShizzlePDX503 on 2009-10-13
I actually used these commands to install the source and the key instead of doing it all separately:

```
sudo add-apt-repository ppa:/doctormo/barry-snapshot
```

then I just did

```
sudo apt-get update
```

then

```
sudo apt-get install barry
```

Thanks

---

### Post by DoctorMO on 2009-10-13
I didn't think it was called 'barry' in the packages. I thought it was libbarry0 opensync-barry etc etc.

---

### Post by ShizzlePDX503 on 2009-10-15
> **DoctorMO said:**
> I didn't think it was called 'barry' in the packages. I thought it was libbarry0 opensync-barry etc etc.

yes that is correct! my bad!

---

### Post by dforstmann on 2009-10-21
I have installed barry in Karmic from ppa but it isn't working.   "pppd call barry-verizon" results in the following:

No device selected
Script /usr/sbin/chat -f /etc/chatscripts/barry-verizon.chat finished (pid 10071), status = 0x2
Connect script failed
Script /usr/sbin/pppob finished (pid 10070), status = 0x1
dean@dean-laptop:~$ sudo pppd call barry-verizon
Script /usr/sbin/chat -f /etc/chatscripts/barry-verizon.chat finished (pid 10102), status = 0x0
Serial connection established.
using channel 2
Using interface ppp1
Connect: ppp1 <--> /dev/pts/5
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x68132d0c> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <mru 1500> <asyncmap 0x0> <magic 0xf3948ea3> <pcomp> <accomp>]
sent [LCP ConfAck id=0x0 <mru 1500> <asyncmap 0x0> <magic 0xf3948ea3> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x68132d0c> <pcomp> <accomp>]
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [LCP DiscReq id=0x1 magic=0xf3948ea3]
rcvd [IPCP ConfReq id=0x0 <addr 66.174.121.64>]
sent [IPCP ConfAck id=0x0 <addr 66.174.121.64>]
rcvd [LCP ProtRej id=0x2 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [IPCP ConfNak id=0x1 <addr 97.13.61.127> <ms-dns1 66.174.95.44> <ms-dns2 66.174.92.14>]
sent [IPCP ConfReq id=0x2 <addr 97.13.61.127> <ms-dns1 66.174.95.44> <ms-dns2 66.174.92.14>]
rcvd [IPCP ConfAck id=0x2 <addr 97.13.61.127> <ms-dns1 66.174.95.44> <ms-dns2 66.174.92.14>]
Cannot determine ethernet address for proxy ARP
local  IP address 97.13.61.127
remote IP address 66.174.121.64
primary   DNS address 66.174.95.44
secondary DNS address 66.174.92.14
Script /etc/ppp/ip-up started (pid 10107)
Script /etc/ppp/ip-up finished (pid 10107), status = 0x0

Anyone know what the problem is?

---

### Post by ShizzlePDX503 on 2009-10-21
I am still a newbie to the whole linux stuff but does your blackberry show up when you do lsusb in terminal? if it doesn't then unplug it then plug it back in and then see if it shows up.

---

