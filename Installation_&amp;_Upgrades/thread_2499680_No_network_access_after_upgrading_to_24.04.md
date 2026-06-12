---
title: "No network access after upgrading to 24.04"
date: 2024-08-06
forum: Installation &amp; Upgrades
---

### Post by kodingkoning on 2024-08-06
I recently upgraded to 24.04. However, now I am unable to access the Internet or the local network. When Googling the problem, I've found recommendations to flush iptables, but that didn't solve the issue.

When I follow [these instructions ]("https://unix.stackexchange.com/questions/43233/how-to-check-from-a-command-line-that-network-is-reachable")to check my local network, I find that I have a wlp4s0 connection listed, but when I ping the associated IP address, I get `ping: sendmsg: Operation not permitted` as well as `Destination Port Unreachable`.

I'm not finding useful information online about how to fix this, so I need other ideas. What else can I try?

---

### Post by currentshaft on 2024-08-06
.

---

### Post by kodingkoning on 2024-08-06
> **currentshaft said:**
> How is networking configured? Wired, wireless, dhcp, etc?

It's wireless. I tried Ethernet as well, but no difference.

---

### Post by currentshaft on 2024-08-06
.

---

