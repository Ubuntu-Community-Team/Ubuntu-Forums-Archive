---
title: "Feisty freezing"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by gewitty on 2007-04-23
Has anyone else experienced their machine freezing after upgrading to Feisty? My system is working OK, but after periods of inactivity, ranging from ten to thirty minutes, I find that the mouse and keyboard have become inactive. I'm not sure if this is a problem with the MS wireless mouse/keyboard that I'm using, or if it's a wider issue that is causing the problem. The only way I can fix things at the moment is by doing a power-down and restart.

---

### Post by beeman69 on 2007-04-24
Any luck finding a solution?  I did read a post about changing the BIOS settings for disable/enable for USB, but I don't have USB, only PS/2.  I have this same issue, just wondering.

---

### Post by gewitty on 2007-04-25
No joy yet, although the problem is infrequent, so it's difficult to associate with any particular event. The only thing I can say is that it has never happened whilst the machine is in use, only when idle.

The USB mention is interesting as I do have an external USB HD hooked up. Can you recall where you saw the post about changing BIOS settings?

---

### Post by gewitty on 2007-04-26
There have been no freezes all day today, right up until a few minutes ago. I had left the machine for around fifteen minutes and came back to check email (Thunderbird). I had read one message and then went to click on the next, but found that the system had locked up for no apparent reason.

I rebooted and checked the syslog and error logs. The output for the relevant time was as follows:
[B]
SYSLOG (the last five minutes before the crash)
[/B]
Apr 26 16:50:06 dave-desktop dhclient: No DHCPOFFERS received.
Apr 26 16:50:06 dave-desktop dhclient: No working leases in persistent database - sleeping.
Apr 26 16:50:28 dave-desktop kernel: [33763.347158] Unknown OutputIN= OUT=eth0 SRC=169.254.4.48 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Apr 26 16:50:28 dave-desktop kernel: [33763.347454] Outbound IN= OUT=wlan0 SRC=192.168.1.100 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Apr 26 16:50:38 dave-desktop kernel: [33773.349545] Unknown OutputIN= OUT=eth0 SRC=169.254.4.48 DST=169.254.255.255 LEN=264 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=244 
Apr 26 16:54:35 dave-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 26 16:54:43 dave-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr 26 16:54:52 dave-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 26 16:54:59 dave-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 26 16:55:06 dave-desktop dhclient: No DHCPOFFERS received.
Apr 26 16:55:06 dave-desktop dhclient: No working leases in persistent database - sleeping.
Apr 26 16:55:28 dave-desktop kernel: [34063.306406] Unknown OutputIN= OUT=eth0 SRC=169.254.4.48 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Apr 26 16:55:28 dave-desktop kernel: [34063.306724] Outbound IN= OUT=wlan0 SRC=192.168.1.100 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58

**ERROR LOG (immediately after the crash - nothing before)**

E [26/Apr/2007:16:59:41 +0100] Creating missing directory "/var/run/cups/certs"
E [26/Apr/2007:16:59:42 +0100] Unable to find IP address for server name "dave-desktop"! 

I don't know if that gives anyone a clue as to what happened.

---

