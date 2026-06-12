---
title: "Karmic RC seems to have broken my VPN"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by potatan on 2009-10-25
Hi - I've been running a Karmic beta on my Dell Mini 10 for a little while and my PPTP VPN connection has worked fine.  I downloaded the release candidate and did a clean install, now my VPN connection (over wireless) no longer works.

I get an error pop-up notification saying something like "VPN Connection Failed" when I try to connect - what log/file can I examine to try and discover why or where this is happening?

Sorry for being a bit vague, the problem occurs at college and I am back home right now.  I'll be down there again tomorrow to see if I can fix it, so any advance help would be appreciated.

Thanks in advance.

---

### Post by potatan on 2009-10-26
Bump - I'm off to college in an hour so any advice welcome

*edit* Ooops, sorry about the 11-hour bump, thought I posted the original question yesterday morning.

---

### Post by potatan on 2009-10-26
All fixed after lots of digging around.

I had to disable "EAP" in the list of protocols, and enable "MPPE" encryption.  All good now, posting this in case anyone has a similar problem.

---

