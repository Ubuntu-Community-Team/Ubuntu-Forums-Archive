---
title: "Slow intranet transfer speeds"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phelin4 on 2008-09-26
Hi,

I have a PC connected to my cable modem/wireless access point with 100Mb/s full duplex. I also have a laptop connected to the access point with 54Mb/s using WPA-TKIP. I upgraded both from Hardy to Intrepid some time ago, when I had to change the motherboard of the PC. Previously I could move data from the laptop to the PC (or the other way round) with scp at the speeds of about 1,6Mb/s - 2,2Mb/s. Now, when I start a transfer, it starts from about 2,1Mb/s and goes down, until after 10s or so it is down to about 300kb/s, where it stays for the rest of the transfer.

I don't see any lost packets, retransmits or thing like that.

My previous motherboard was a Asrock 775Dual-VSTA with Via PHY VT6103 100Mb using Via Rhine driver. The current motherboard is Asus P5E-V HDMI, with Atheros L1 PCIe Gb using atl1 driver. The laptop has an Intel 3945ABG.

I found in the networking forum a thread on a similar matter, but since I am using Intrepid, I opened a new one here. Here is the other thread: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5472930](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5472930)

Could you please let me know what kind of transfer speeds you are getting in your internal networks?

---

### Post by phelin4 on 2008-10-06
Am I the only one seeing this? Do all of you have decent transfer speeds when copying with scp over a 802.11g network?

---

### Post by Delvien on 2008-10-06
Transferring over wireless for me has never been 2,1/s lol, more along the lines of 400 ish.

---

### Post by phelin4 on 2008-10-13
Well, there is a thread in Networking&Wireless section which mentions also 2MB/s with Hardy (although they complain _that_ being too slow...). Look here: [http://ubuntuforums.org/showthread.php?t=889649](http://ubuntuforums.org/showthread.php?t=889649)

Aren't there any people interested in wireless networking speed with Intrepid? All I am asking is that you post the speed you achieve when connecting through wireless to a source located on your own LAN (another PC, NAS, whatever). As a reference i can tell that if I use a wired connection from the same latptop to the same HTPC through the same access point, I get transfer speed of 11MB/s. That's a lot compared to the 300kB/s with wireless...

---

### Post by phelin4 on 2008-10-22
I need to update this, since I realized something: the slow speed of some 300 kBytes/s was only when sending from the laptop with Intel 3945ABG wlan towards the HTPC. When I do it the other way round, I get transfer speed of 1.6 MBytes/s - 2.2 MBytes/s, which is what I was expecting from previous experiences. Now I must admit that I don't recall if it was previously that about 2.0 MBytes/s in both directions, but whether it was or not, I am still a bit baffled on why there's such a deviation between sending and receiving on the laptop. Any ideas? 

Here are excerpts from the tests I made with iperf:

From laptop to the htpc:
```

# iperf -c 192.168.1.100 -f k -p 10001 -t 30 -i 5
------------------------------------------------------------
Client connecting to 192.168.1.100, TCP port 10001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.110 port 38542 connected with 192.168.1.100 port 10001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 5.0 sec  1968 KBytes    394 KBytes/sec
[  3]  5.0-10.0 sec  1480 KBytes    296 KBytes/sec
[  3] 10.0-15.0 sec  1568 KBytes    314 KBytes/sec

```

From htpc towards the laptop:
```

# iperf -c 192.168.1.110 -f K -p 10001 -t 30 -i 5
------------------------------------------------------------
Client connecting to 192.168.1.110, TCP port 10001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.100 port 57430 connected with 192.168.1.110 port 10001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 5.0 sec  9288 KBytes  1858 KBytes/sec
[  3]  5.0-10.0 sec  8904 KBytes  1781 KBytes/sec
[  3] 10.0-15.0 sec  9168 KBytes  1834 KBytes/sec

```

As you can see, transferring from the htpc to the laptop is a six times faster than from the laptop to the htpc.

---

