---
title: "Modem connects but NO INTERNET?!?"
date: 2005-04-30
forum: Installation &amp; Upgrades
---

### Post by bigkahuna on 2005-04-30
Help?!?  I'm trying to get my external serial modem to work with Hoary.  I followed the "Dialup Modem Howto" in the Wiki (explains how to use pppconfig) and my modem connects, but when I launch Firefox I can't go to any webpages!  I tried the "network settings" and tried setting the network to "ppp0".  Now the modem connects when I boot up Ubuntu, but when I log in I still can't access the internet.

Any ideas?

Paul

---

### Post by Professor X on 2005-05-01
Sounds like you haven't configured your name server.  You need to edit the file /etc/resolv.conf and add an entry like this:

```
nameserver 198.6.1.150
``` 

You should be able to find out the IP address for your DNS from your ISP.  Most ISP will have two DNS addresses, so you can add both if you like.

---

### Post by bigkahuna on 2005-05-01
Didn't work and I'm getting pretty frustrated.  It was originally set for "dynamic" DNS setting which is what is recommended in the How To in the wiki.

I'm using Damn Small Linux right now to write this reply.  I was able to install the modem with Knoppix, Kanotix and Damn Small Linux in just a few minutes.  But Ubuntu is giving me a major headache   :mad: 

I can't figure out what's wrong.  The modem connects, the network shows that it's connected, yet when I launch Firefox it says it can't find a website...   :?

---

### Post by Nob on 2005-05-01
i doesnt have to with resolv.conf, just chmod it to 777
i suggest that yopu lookup for a driver over internet ;) 
what modem do you have?

---

### Post by bigkahuna on 2005-05-01
The modem is a Best Data 56SPX-2 external serial modem.  I'm able to use this same modem with Knoppix, Kanotix and Damn Small Linux (all Debian derivatives) and installation was very easy.  I bought this modem because it was very highly rated for use with Linux.

Last night I was able to get the modem to work with Hoary.  It appeared that part of the problem was related to the DNS settings.  I set it up to "dynamic DNS" with all the other distros and it worked, but not with Hoary.  With Hoary I had to manually enter the DNS settings.

 BUT I still have 2 problems:

1.  Throughput is EXTREMELY slow.  I ran a test and throughput was about 7 k/sec while using the exact same hardware but under Knoppix throughput was 37 k/sec.

2.  The modem connects when I boot up the system (?).  So connecting to the internet is in my boot script??

I'm becoming increasingly dissappointed with Hoary.  The hardware detection and configuration has been much worse than Warty.  Unfortunately, I installed Hoary on top of Warty, so in order to go back I'll have to do a fresh install....  and if I do that I don't think it will be Ubuntu.

I'm VERY unhappy with Hoary. :-(

---

