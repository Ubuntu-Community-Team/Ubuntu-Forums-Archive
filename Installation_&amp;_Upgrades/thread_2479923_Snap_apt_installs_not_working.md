---
title: "Snap apt installs not working"
date: 2022-10-13
forum: Installation &amp; Upgrades
---

### Post by sahil-thinkpad on 2022-10-13
While installing packages with apt, it results in hash mismatch and similarly with snap it says "tls: bad record MAC". What to do ??[IMG]https://easyupload.io/jnf0cz[/IMG]

---

### Post by TenPlus1 on 2022-10-13
This may help: [https://www.zabbix.com/forum/zabbix-troubleshooting-and-problems/400926-error-tls-read-fatal-alert-bad-record-mac-on-agent](https://www.zabbix.com/forum/zabbix-troubleshooting-and-problems/400926-error-tls-read-fatal-alert-bad-record-mac-on-agent)

---

### Post by sahil-thinkpad on 2022-10-15
Other laptops on the same network with same ubuntu versions work fine. Also reinstalled the os, got the same issue again so downgraded from 22.04 to 20.04.5 and its working fine for now, probably issue with the network card driver or something.

---

### Post by TheFu on 2022-10-15
I've seen onboard NICs in a failing system corrupt files.  We never figured out if the problem was with the NIC or the motherboard.  The system causing the corruption was a software developer's. Every time he'd check in code to the central repo and any other develop got an updated version of that code, it was corrupted.  That's how we were able to trace the issue to 1 person's hardware quickly.

If you have more than 1 computer, you could try copying files around along with some sha256sums of those files to check for differences.

Of course, it could be a failing HDD, failing SSD, failing switch/router or just a failing port in any of the connected devices.  Simplify and test until the smallest possible component is isolated. This is standard troubleshooting practice.

---

