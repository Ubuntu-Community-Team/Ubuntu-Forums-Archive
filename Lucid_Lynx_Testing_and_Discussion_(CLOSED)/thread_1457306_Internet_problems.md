---
title: "Internet problems"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by FiskFisk33 on 2010-04-18
I cant seem to get the wired network to work properly.
The strange thing is, i connect the cable, it says its connected, it has obtained an adress from the router, but i cant connect to the internet with for example firefox or synaptic. However, i CAN ping stuff, anything i ping seem to respond.
I have tried ignoring ipv6 as suggested in another thread but my problem seems to be a different one.

By the way, when i click the ping tab on "Network Tools" it crashes it. so i used terminal to ping.

---

### Post by FiskFisk33 on 2010-04-18
No one?

---

### Post by rtalcott on 2010-04-18
I have the same problem...machine worked fine with 9.10...OpenSolaris...no problem...but Lucid...does not work...I appear to have a valid IP from my router and my ISP dns IP's...but I cannot connect via firefox or synaptic...and I cannot ping and get a reply...I have had this problem with daily builds for weeks.
rt

---

### Post by FiskFisk33 on 2010-04-19
I gave up on the beta and installed a release instead (the latest Linux Mint)

Internet worked, well, better.
But the thing is some programs still couldnt access the internet, reason being my router answering 1.0.0.0 to all dns requests.
Reason for that is that aptitude (for example) is very prone to request AAAA records (ipv6 type), which mine and many others modems doesn't like, while firefox did the A type.

[https://bugs.launchpad.net/ubuntu/+bug/81057](https://bugs.launchpad.net/ubuntu/+bug/81057)

look at answer #19 through #21, that did the trick for me, in mint that is. i am just guessing this is whats happening in lucid

---

### Post by rtalcott on 2010-04-19
THANK YOU!

I'll give it a try!
rt

---

### Post by rtalcott on 2010-04-19
What's weird is that I have 4 machines running 10.04....all through the same router..a Linksys wrt54g...and they all work...hard to believe my issue is a router/dns issue.
rt

---

