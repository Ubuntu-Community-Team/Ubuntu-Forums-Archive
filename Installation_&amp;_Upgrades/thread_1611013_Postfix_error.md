---
title: "Postfix error"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by kiranpvsr on 2010-11-01
Hi,
I have installed Postfix.
I can send an email to gmail,yahoo etc.

But I get the following error when I send an email to a specific domain like the following :


Nov  1 16:12:12 localhost postfix/pickup[8453]: DAC7AED5B: uid=0 from=<root>
Nov  1 16:12:12 localhost postfix/cleanup[8459]: DAC7AED5B: message-id=<20101101161212.DAC7AED5B@li140-183.members.linode.com>
Nov  1 16:12:12 localhost postfix/qmgr[8454]: DAC7AED5B: from=<root@mail.ctr-internal.com>, size=422, nrcpt=1 (queue active)
Nov  1 16:12:13 localhost postfix/smtp[8461]: DAC7AED5B: to=<ravi.kiran@marketmanager2-0.com>, relay=mail.marketmanager2-0.com[79.170.40.26]:25, delay=0.29, delays=0.11/0/0.11/0.08, dsn=5.0.0, status=bounced (host mail.marketmanager2-0.com[79.170.40.26] said: 550-Verification failed for <root@mail.ctr-internal.com> 550-Unrouteable address 550 Sender verify failed (in reply to RCPT TO command))
Nov  1 16:12:13 localhost postfix/cleanup[8459]: 22333ED5C: message-id=<20101101161213.22333ED5C@li140-183.members.linode.com>
Nov  1 16:12:13 localhost postfix/bounce[8462]: DAC7AED5B: sender non-delivery notification: 22333ED5C
Nov  1 16:12:13 localhost postfix/qmgr[8454]: 22333ED5C: from=<>, size=2602, nrcpt=1 (queue active)
Nov  1 16:12:13 localhost postfix/qmgr[8454]: DAC7AED5B: removed
Nov  1 16:12:13 localhost postfix/smtp[8491]: 22333ED5C: to=<root@mail.ctr-internal.com>, relay=none, delay=0.04, delays=0.03/0/0/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=mail.ctr-internal.com type=A: Host not found)
Nov  1 16:12:13 localhost postfix/qmgr[8454]: 22333ED5C: removed

can someone please let me know where am I going wrong ?

---

