---
title: "dialup error - LCP: timeout sending Config-Requests"
date: 2005-05-19
forum: Installation &amp; Upgrades
---

### Post by motiv8d on 2005-05-19
I have configured an external modem (Diamond Voice EX560LK which I believe has a lucent venus chipset) on Ubuntu 5.04 and cannot get it to finalize a connection with anything. I cannot tell if it is getting passed username password stage etc, but it certainly doesnt get to the stage of giving me a ppp0 in ifconfig.
Could someone please let me know what it going wrong, or what else (eg other logs) that I can check to narrow down the problem. I get the same problem trying to connect to an ISP as I do trying to connect to a windows RAS server.

Heres the /var/log/message output

May 19 20:18:05 localhost chat[7860]: ^M
May 19 20:18:05 localhost chat[7860]: AT&FH0L3^M^M
May 19 20:18:05 localhost chat[7860]: OK^M
May 19 20:18:41 localhost chat[7860]: ATDT96761924^M^M
May 19 20:18:41 localhost chat[7860]: CONNECT
May 19 20:18:41 localhost chat[7860]:  -- got it
May 19 20:18:41 localhost pppd[7859]: Serial connection established.
May 19 20:18:41 localhost pppd[7859]: Using interface ppp0
May 19 20:18:41 localhost pppd[7859]: Connect: ppp0 <--> /dev/ttyS0
May 19 20:19:12 localhost pppd[7859]: LCP: timeout sending Config-Requests
May 19 20:19:22 localhost pppd[7859]: Hangup (SIGHUP)
May 19 20:19:22 localhost pppd[7859]: Modem hangup
May 19 20:19:22 localhost pppd[7859]: Connection terminated.
May 19 20:19:23 localhost pppd[7859]: Exit.

I have since also tried setting up wvdial.
I get:
CONNECT 46666 V42bis
Carrier Detected. Waiting for prompt.
Don't know what to do. Starting pppd and hoping for the best.
Starting pppd at Fri...
pid of pppd: 6478
Using interface ppp0
Disconnecting at Fri...
The ppp daemon has died. PPP negotiation has failed (exit code = 10)

man pppd says of exit code 10
The ppp negotiation failed. That is it didn't reach the point where at least one network protocol (e.g.: IP) was running.

Thanks in advance.

---

