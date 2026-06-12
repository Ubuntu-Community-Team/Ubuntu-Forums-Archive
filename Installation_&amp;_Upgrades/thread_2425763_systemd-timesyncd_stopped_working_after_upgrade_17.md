---
title: "systemd-timesyncd stopped working after upgrade 17-Jun-2019"
date: 2019-08-29
forum: Installation &amp; Upgrades
---

### Post by joeinwap on 2019-08-29
Problem: Local clock differs significantly from ntp servers.  Started after [FONT=courier new]apt upgrade[/FONT] on 17-Jun-2019.
Symptom: [FONT=courier new]systemctl status systemd-timesyncd[/FONT] shows [FONT=courier new]Fail, (code=exited, status=238/STATE_DIRECTORY)[/FONT].
[HR][/HR]Diagnosis: /var/lib/private is mode 0755 and/or some entries therein have unknown user.  Red Hat forums mention this permissions problem.
Cure: [FONT=courier new]chmod 0700 /var/lib/private; rm -rf /var/lib/private/*; systemctl start systemd-timesyncd; timedatectl

[/FONT]

---

### Post by Skaperen on 2019-08-29
do you see any ntp server queries in **[COLOR=#0000ff][FONT=courier new]tcpdump -llni any port 53[/FONT][/COLOR]**?  where do they go? are there any answers?

---

### Post by Skaperen on 2019-08-30
i found on one of my servers running ntp that it is doing DNS lookups to 127.0.0.1.  that server does not run systemd.  /etc/resolv.conf points to 2 ISP DNS servers which are working fine.  but ntp is getting no answers to the DNS requests and repeats sending them every minute.  i cannot find any file that is possibly telling it query 127.0.0.1.  i don't know what is going on with it.  i cannot find when or even if i upgraded ntp there (it's an old Slackware box).

---

