---
title: "Upstart trouble after upgrade 10.4 -&gt; 12.4"
date: 2013-05-30
forum: Installation &amp; Upgrades
---

### Post by mennopieters on 2013-05-30
Hi,

First of all, I've gone through the first fixed messages about upgrade trouble. I didn't find the solution there.

I have a virtual server (Linux vServer) at Alvotech (alvotech.de). It used to run Ubuntu server 10.04. I have upgraded it to 12.04, which seemed to go fine. The server has NO console access, but can be restarted through a web interface if necessary. I also have no control over the kernel and grub parameters.

After upgrading my server stays in runlevel 1, with just ssh and rsyslog running. So I can login and type "init 2" to get the rest going. The default runlevel is set to 2, so I would expect it to move on automatically.

I've also noticed that upstart has some trouble starting processes. rsyslog for example starts at boot time, but logrotate (for zimbra) restarts rsyslog and then it just hangs. I cannot stop rsyslog through upstart, but only by killing rsyslog manually and then killing the upstart processes. Or perhaps, as suggested on some articles I found, I'm inpatient and should wait for like an hour. None of the articles I found had the solution.

I assume both problems are upstart related. Any suggestions how to debug the problem and get my system back to normal again would be highly appreciated.

Regards,

Menno

---

