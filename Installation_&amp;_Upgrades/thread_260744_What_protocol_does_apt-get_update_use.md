---
title: "What protocol does apt-get update use?"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by rif on 2006-09-19
From many networks, such as my office and the hotel I'm currently at, updating ubuntu (such as apt-get update) consistently seems to hang and fail.  For instance, right now I'm looking at:

0% [Waiting for headers] [Waiting for headers]

and I've been looking at this for quite a few minutes.  Web and ssh seem to work fine from this network.  My repositories are mostly coming from archive.ubuntu.com.

It really seems like somehow the network isn't allowing these connections, but I'm not sure what would cause that or what my alternatives are.  It is quite frustrating, since I have encountered this difficulty on two different networks recently.

---

### Post by whizbaby on 2006-09-19
Sometimes the server is unreachable (if stars alligned). You could try other servers by adding some country-code, e.g.
... [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) ...
... [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) ...
... [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) ...
in all entries and then [B]sudo apt-get update
[/B]

---

### Post by rif on 2006-09-19
Tried de, fr, and dk repositories.  Exactly the same behavior.  Copied my /etc/apt/sources.list (which is just the default suggested ones I found elsewhere in this forum) to a different machine on a different network, and that at least partially worked (got a bunch of repos before hanging).  On this network, I've yet to see anything except 

0% [Waiting for headers] [Waiting for headers]

I don't really understand.  It's just http as far as I know, and certainly I can surf the web no problem, but updates aren't coming through at all.  The exact same /etc/apt/sources.list works on Network B but not Network A, making me suspect a network problem rather than a repo problem.

---

### Post by tjvdberg on 2006-09-19
Try replacing the http:// with ftp://
Than do a sudo apt-get update and see if it works.
The problem might be a virus or content scanner, witch checks all http based connections, it might not do it for ftp.

---

### Post by rif on 2006-09-19
I just wanted to update on the full situation here, because I'm very confused.  I have two machines, on network A and network B.  They have the SAME /etc/apt/sources.list file.  On network B, an apt-get update works in a couple minutes.  On network A, it almost never shows anything except

0% [waiting for headers] [waiting for headers]

although sometimes it will show part of a file.

I looked a bit at the network traffic with tcpdump.  On the hotel (nonworking) network, I see a lot of packets like:


12:53:25.722476 IP 10.67.142.6.60234 > 212.58.240.132.80: . ack 1709 win 2412 <nop,nop,timestamp 929643 1053850158>
12:53:25.900474 IP 212.58.240.132.80 > 10.67.142.6.60234: . 1709:3077(1368) ack 826 win 32419 <nop,nop,timestamp 1053850168 929639>
12:53:25.900507 IP 10.67.142.6.60234 > 212.58.240.132.80: . ack 3077 win 3096 <nop,nop,timestamp 929688 1053850168>
12:53:25.911464 IP 212.58.240.132.80 > 10.67.142.6.60234: P 3077:4445(1368) ack 826 win 32419 <nop,nop,timestamp 1053850168 929639>
12:53:25.911488 IP 10.67.142.6.60234 > 212.58.240.132.80: . ack 4445 win 3780 <nop,nop,timestamp 929690 1053850168>
12:53:25.927828 IP 212.58.240.132.80 > 10.67.142.6.60234: . 4445:5813(1368) ack 826 win 32419 <nop,nop,timestamp 1053850171 929643>
12:53:25.927850 IP 10.67.142.6.60234 > 212.58.240.132.80: . ack 5813 win 4464 <nop,nop,timestamp 929694 1053850171>
12:53:25.938956 IP 212.58.240.132.80 > 10.67.142.6.60234: P 5813:7181(1368) ack 826 win 32419 <nop,nop,timestamp 1053850171 929643>

On the working network, none of the ack's have that <nop,nop,timestamp ###> bit.

Anyways, I'm totally nonplussed here.  I DON'T think the problem is unreachable repos, because I can update from another machine with the same /etc/apt/sources.list.

---

### Post by rif on 2006-09-19
Just tried switching from http to ftp.  That does work.  So the explanation is "virus scanner in the firewall that passes some but not all http"?

---

### Post by tjvdberg on 2006-09-19
I don't what kind of firewall/router you office uses. I know for example, Astraro products can show this kind of behavior. I had the same problem. But I don't know al that much about firewall/routers/viruscanners etc. :)
But I'am glad this solutions works for you.

---

