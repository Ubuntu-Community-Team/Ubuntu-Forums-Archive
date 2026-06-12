---
title: "Connection delays following hard crash and upgrades"
date: 2017-07-01
forum: Installation &amp; Upgrades
---

### Post by msapiro on 2017-07-01
Ubuntu 16.04.

The server had a power interruption. Following restart, auto updates upgraded linux from 4.4.0-79-generic to 4.4.0-81-generic and libnss3 to 2:3.28.4-0ubuntu0.16.04.2.

Since that time there are delays of 5 to 10 seconds or more in TCP connects to Postfix port 25 and 587. These delays also affect connects on the loopback interface from localhost to localhost (127.0.0.1) port 25.

http and https connects seem to be unaffected.

There seem to also be new issues with fail2ban, but these are not of as much concern as the connection delays which affect remote clients sending SASL authenticated mail and local processes sending multiple messages with a new SMTP connect per message.

I tried reverting to linux 4.4.0-79-generic, but that didn't help and I am now on 4.4.0-83-generic.

Does anyone have any clues/advice?

---

### Post by Autodave on 2017-07-01
If it was doing an update when the power failed, there is no telling what might have been screwed up. No power backup on the server?  I assume that you have tried rebooting the server to see if that helps?

---

### Post by msapiro on 2017-07-01
It was not doing any updates at the time of the failure. Auto update ran after it was restarted. And yes, the server has been subsequently rebooted multiple times. And yes, it is in a colo with UPS backup, but maybe once every five years or so, something goes wrong and power is interrupted.

---

### Post by msapiro on 2017-07-07
I don't actually know what the solution was, but the problem seems to be resolved. 'libc-bin:amd64 2.23-0ubuntu7' was one of the things installed after the server restarted and 'libc-bin:amd64 2.23-0ubuntu9' and 'libgcrypt20:amd64 1.6.5-2ubuntu0.3' were the only things recently installed before the server started working normally. Thus, the issue was possibly caused by 'libc-bin:amd64 2.23-0ubuntu7'.

---

