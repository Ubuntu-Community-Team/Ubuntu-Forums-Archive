---
title: "xserver crashes after upgrading to edgy"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by chomg on 2006-10-26
Hi, all,

My system just goes to halt after upgrading to edgy. I figured that out the problem occurs when xwindow is running. So, I removed gdm.

When I start x using 'startx', I got the following message.

> 
Message from syslogd@localhost at Thu Oct 26 17:16:32 2006 ...
localhost kernel: [17179790.268000] Uhhuh. NMI received. Dazed and confused, but trying to continue

Message from syslogd@localhost at Thu Oct 26 17:16:32 2006 ...
localhost kernel: [17179790.268000] You probably have a hardware problem with your RAM chips


Even though the message says RAM chips may be problematic, my machine worked just fine.

I was running dapper on DELL Dimension 9100 with ATI Radeon X300.
Also, I attached xorg.conf file.

Please give me any clue to fix the problem. Thanks a lot in advance.

---

