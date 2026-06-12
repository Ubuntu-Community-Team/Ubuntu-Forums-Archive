---
title: "Urgent help after update!"
date: 2005-03-26
forum: Installation &amp; Upgrades
---

### Post by sunscape on 2005-03-26
Can't get onto the internet (past my router) using ubuntu. I can login to my router and browse the LAN, etc... But anything beyond that is impossible. It seems like some kind of wacky firewall was installed during the last updated. I don't know....

But anyway, all my iwconfig settings check out fine. I just can't do anything beyond connect to my router.

NICE UPGRADE BTW... disable all internet access. hmm

anyone? 

P.S. i'm using windows to type this message.

---

### Post by az on 2005-03-26
From the console, can you ping outside addesses?

If this does not work, 
ping [www.yahoo.ca](www.yahoo.ca)

try:

ping 216.109.112.135
PING 216.109.112.135 (216.109.112.135) 56(84) bytes of data.
64 bytes from 216.109.112.135: icmp_seq=1 ttl=53 time=24.3 ms
64 bytes from 216.109.112.135: icmp_seq=2 ttl=53 time=22.8 ms
64 bytes from 216.109.112.135: icmp_seq=3 ttl=53 time=22.8 ms

--- 216.109.112.135 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 22.802/23.328/24.372/0.748 ms


It may be a dns problem.  Are you connecting to your router through dhcp or a static connection?
DHCP should be setting your resolv.conf properly each time.  Otherwise, you need to add nameservers by hand to your 
/etc/resolv.conf

nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

---

### Post by arctic on 2005-03-26
i answered the very same thing here. give it a look. too lazy to type it once again :P
[http://www.ubuntuforums.org/showthread.php?t=22198](http://www.ubuntuforums.org/showthread.php?t=22198)

---

### Post by sunscape on 2005-03-26
Neither of those helped. I have really no idea what is wrong. I should mention that this is effecting both wireless and wired access. I have just confirmed this one two computers that were broken by last nights update. So, what can i copy past here to help solve this problem?

I can ping my router without a problem, but i can not get past my router. Before the update everything was working fine. What could have changed?

---

### Post by arctic on 2005-03-26
i found this on the net. maybe it helps you:
> When I ran "sudo ifdown eth0; sudo ifup eth0", I got a very helpful
error message telling me the problem:

sit0: unknown hardware address type 776
/etc/dhcp3/dhclient.conf line 21: expecting semicolon.
netbios-name-servers, netbios-scope interface-mtu;
^

Adding a comma between netbios-scope and interface-mtu fixed it. (I used
a comma, contrary to the error message that says "semicolon", since all
the other entries on this line are already separated with commas -
probably an error in the error message "

---

### Post by Spacecaptain on 2005-03-26
[QUOTE=arctic]i found this on the net. maybe it helps you:[/QUOTE]

thanx alot arctic! that worked fine for me!
now, it's crazy to say, but i was *lucky* enough to have left a w2k partition on my PC to be able to connect to the internet and find this forum-thread to fix the problem.
thing is, now i can't find those friends online that i convinced to swap over to Ubuntu... i suppose they are having the same trouble i had before reading this.

thanx for helping me convince them that Ubuntu is a reliable alternative (this is sarcasm yes).
now, i wonder why some update crazed people felt compelled to experiment with something as basic to Ubuntu as it's capacity to connect to the internet...
i know we are not machines and mistakes are human, but then, please: less precipitation!
if something works, don't change it! unless you are sure it works better...

---

### Post by arctic on 2005-03-26
hehehe... things tend to break on testing distributions from time to time, although i must admit that the comma stuff is a little bit laughable. :D

---

