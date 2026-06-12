---
title: "x86 server help"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by leetcharmer on 2006-06-05
Hello, I've been toying around with the server install CD and I've got an idea for a server that I want to build. Here's my system specs:

AMD Athlon 2100+
1GB RAM
3 HDDs: 2/80GB IDE; 1/250GB RAID
D-Link DI-624 Router w/ Wireless setup.

Pre-Question:
1) Is it alright to plug my server straight into the router and let it control DHCP? Or should I really invest in a second ethernet card and go Internet -> Server -> Router -> Thin Clients / PCs?
2) I want to keep LTSP in mind so I've formatted the first 80GB HDD as / (and swap) and then second as /home. I want to turn the 250GB into a storage center -- like a NAS or SAN server; how should I format this and what should it be mounted as? Can you verify that my formatting scheme is appropriate -- for webservers, I find that sometimes they like to build a partition separate for /var; what are your thoughts?

Alright, here's the plan -- I want to build a server to host my website ([www.crossfirenow.com](www.crossfirenow.com) via LAMP); host my Counter-Strike: Source Server (easy to setup and run); LTSP host for 4 thin clients (home network). With my current hardware, does this sound doable? I'm running on a Fiber Optic connection at home (15Mbps down/1.5Mbps up).

First on my list -- webserver:
I've seen some tutorials online with setting up web servers and what-not -- when they speak of domains, they always have server.example.com as their domain, would I change this to server.crossfirenow.com?? Right now, that site is being hosted by 1and1.com -- I would like to experiment with the server I built using that domain name which I have registered through them. How can I get a DNS setup to switch hosting to my box? :/ I always have problems setting up MySQL after installation, but I'll deal with that later.

Since I know how to do the Counter-Strike server I'll skip that in this post.
Third: LTSP -- could anyone hook me up with resources to get started?

Fourth: Should I have anything else in my server? Ideas?

Thanks for any replies :D!

---

