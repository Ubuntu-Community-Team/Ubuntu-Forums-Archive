---
title: "Kubu 5.10 LAN install - can you help me?"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by Bigglez on 2005-11-25
Hello there.
I have always installed from a CD, but this time there is no CD. Let me describe my setup and then beg for some help. Please understand that I am a network nitwit, I used binary years ago to create sprites on my home computer, but netmasks and subnets all sound like so much fishing-tackle to me!

My main desktop box (DB) is Fedora 3. I know this is an Ubuntu forum, but it is Kubuntu that I want to install...

The box on the floor (BOF) is a donation for education in computer literacy. It's literally 10 years old and has never been opened, when I did, it was horrible; an even gray pelt of luxurious dust and hair on all the cards, wires, drives, the motherboard, everywhere. Scary. Needless to say, I don't want to try and plug a CD ROM drive into that mess. I can't risk disturbing the little eco-system balance thing that's going-on in there! Still, it boots and up comes Win95 - amazing.

The BOF has a network-card (and I had to clean the chips to discover it was a Realtek 8019AS.) and 64Mb Ram and a 2gig HDD (I hope these specs will handle Kubu 5.10, but that's another issue)

I fetched the etherboot image from the automated web-form (and I think I matched the network card properly). The BOF boots from the stiffy and starts looking for the network, so that seems good.

**My network is like this:**
Wireless aerial from my WISP. It has an ethernet cable that comes from the roof and into my little 5-port hub. (A box with flashing lights...) From the hub-a-dub I have cables going out. One to my DB, on to an Access Point for the XP-Home laptop that roams about. One to the BOF.

I connect to the WISP by VPN on ppp0 over eth0. I use "dhclient eth0" to get an IP address from the WISP.

*ifconfig* on my DB:
```

eth0      Link encap:Ethernet  HWaddr 00:20:ED:91:49:5D
          inet addr:172.0.10.255  Bcast:172.0.0.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3957 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4312828 (4.1 MiB)  TX bytes:467900 (456.9 KiB)
          Interrupt:11 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12005 (11.7 KiB)  TX bytes:12005 (11.7 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:192.168.15.226  P-t-P:192.168.8.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1496  Metric:1
          RX packets:3773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3021 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:3806677 (3.6 MiB)  TX bytes:246045 (240.2 KiB)

```
I hope that makes some sense.

Okay, so I am following the steps in the wiki:
[https://wiki.ubuntu.com/Installation/LocalNet]("https://wiki.ubuntu.com/Installation/LocalNet")

I have installed tftpd (which has differing directories to the ones described for Ubuntu, but that's not too bad).

I mount the kubuntu5.10.iso on a loop on /tftpboot/kubu

I have apache running, and I make a symlink in /var/www from to /tftpboot/kubu
PROBLEM 1: I can't seem to go into [http://localhost/kubu](http://localhost/kubu), but if I make the link inside /var/www/html then I can. Will this be a problem?

Then comes the great debacle - the DHCP-server. Hoo-boy am I up against my ignorance here! It's complete Greek. (Greek would make more sense ;)  - apologies to the Greeks out there!)

On Fedora, I installed "dhcp" (not "dhcp3" which was not available on yum). I then created an /etc/dhcp.conf as suggested in the wiki, (had to add a line at the end, hey - it told me to!).

But whatever numbers I use in 'subnet' and 'netmask' I just keep getting errors, even if I make them the same as the ifconfig readout.

Plus, I don't know what 'pxelinux.0' is, but I located it at the address you see below.

Example dhcp.conf file:
```

ping-check = 1;
filename = "/usr/lib/syslinux/pxelinux.0";
subnet 192.168.1.0 netmask 255.255.255.0
	{ 
		range 192.168.1.10 192.168.1.254;
	}
ddns-update-style ad-hoc;


```

Now, when I do a "service dhcpd restart" I get messages like this:
```

No subnet declaration for eth0 (172.0.10.255).
** Ignoring requests on eth0.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface eth0 is attached. **

Not configured to listen on any interfaces!


```

And when I change "subnet to 172.0.10.255 netmask 255.255.0.0" I get:
```

/etc/dhcpd.conf line 3: subnet 172.0.10.255 netmask 255.255.0.0: bad subnet number/mask combination.

^
Configuration file errors encountered -- exiting


```

Well, that's as far as I have gotten this thing. Can anyone enlighten me? Pretty please!

---

### Post by yesplease on 2005-11-25
I dont want to spoil your fun with the network, but I would just put the cdrom drive into the BOF.

Box on the Floor, lol, nice terminology.

Edit: I will edit this post because I cant help you with the network. Two remarks: this is really a network problem, so perhaps you can try in that section when you cant get the answers here. Ubuntu is more than 2 GB, but there are smaller versions. 

I loved the Blackadder series too :)

---

### Post by Bigglez on 2005-11-25
Yesplease - I would put a cdrom in, but I really mean it when I say that internally it's beyond dirty. I am worried that if I tinker with things (like moving the IDE cable aside to put the cdrom one in) that it (the cable or worse) will break from old age. 
This is a donation machine, and I ain't rich enough to repair it!

The other factor is that I actually have 2 donation machines, and I am trying to get more. I would like to have an easy way to simply *push* kubuntu onto any BOF that comes my way!

Like Baldric said; "I have a cunning plan..."
;)

C'mon the boffins!

---

### Post by Bigglez on 2005-11-28
bump - c'mon everybody!

---

### Post by Bigglez on 2005-12-06
Well, had net troubles - back to find no movement on this thread. Guess I'll head over to Fedora forums and try again...

Oh well.

:(

---

