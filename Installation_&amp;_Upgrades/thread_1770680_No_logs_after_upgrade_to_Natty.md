---
title: "No logs after upgrade to Natty"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by ZioNemo on 2011-05-29
Hi,
I upgraded to Natty shortly after it became official.

Linux vmrunner 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

It seems to work ok... so I didn't notice till today I have *no* logs whatsoever.

e.g.:

-rw-r----- 1 syslog            adm        0 2011-05-08 07:53 messages
-rw-r----- 1 syslog            adm     1988 2011-05-01 17:59 messages.1
-rw-r----- 1 syslog            adm     1477 2011-05-01 07:50 messages.2.gz

mcon@vmrunner:~$ tail /var/log/messages.1
May  1 16:15:29 vmrunner kernel: [669999.027471] audit_printk_skb: 12 callbacks suppressed
May  1 16:15:29 vmrunner kernel: [669999.027477] type=1400 audit(1304259329.108:22): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=17056 comm="apparmor_parser"
May  1 16:15:29 vmrunner kernel: [669999.028262] type=1400 audit(1304259329.108:23): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=17056 comm="apparmor_parser"
May  1 16:17:04 vmrunner kernel: [670094.652530] type=1400 audit(1304259424.738:24): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=18486 comm="apparmor_parser"
May  1 16:17:04 vmrunner kernel: [670094.654349] type=1400 audit(1304259424.738:25): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=18486 comm="apparmor_parser"
May  1 16:54:31 vmrunner dkms_autoinstaller: vboxhost (4.0.6): Installing module on kernel 2.6.38-8-generic.
May  1 17:58:12 vmrunner kernel: [676161.965488] type=1400 audit(1304265492.048:26): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=4612 comm="apparmor_parser"
May  1 17:58:12 vmrunner kernel: [676161.965539] type=1400 audit(1304265492.048:27): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=4612 comm="apparmor_parser"
May  1 17:58:12 vmrunner kernel: [676161.965574] type=1400 audit(1304265492.048:28): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=4612 comm="apparmor_parser"
May  1 17:59:34 vmrunner kernel: Kernel logging (proc) stopped.
mcon@vmrunner:~$ 

Can someone suggest what should I check?

As said system seems to work correctly (I'm writing this using it), but no logs doesn't sound healthy!

TiA
ZioNemo

---

