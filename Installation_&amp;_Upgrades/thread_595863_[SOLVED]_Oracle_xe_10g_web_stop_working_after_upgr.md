---
title: "[SOLVED] Oracle xe 10g web stop working after upgrade to Gutsy"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by lape on 2007-10-29
I had a working Oracle 10g XE installation in Ubuntu 7.04 and after the upgrade to 7.10 (gutsy) the webinterface will not let me in, when trying to reach it with e.g  lynx 127.0.0.1:8080/apex I get this error:
"Looking up 127.0.0.1 first
Looking up 127.0.0.1:8080
Making HTTP connection to 127.0.0.1:8080
Sending HTTP request.
HTTP request sent; waiting for response.
Retrying as HTTP0 request.
Looking up 127.0.0.1:8080
Making HTTP connection to 127.0.0.1:8080
Sending HTTP request.
HTTP request sent; waiting for response.
Alert!: Unexpected network read error; connection aborted.
Can't Access `[http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex)'
Alert!: Unable to access document.

lynx: Can't access startfile"

I also tried to reinstall the whole package

Is there anyone out there who succeed to install it on gutsy

P.S The sqlplus command work ok, so the oracle itself seems to work Ok, but the webpage could not be reached with any browser.

---

### Post by lape on 2007-10-29
Solved:

After an strace on the process "tnslsnr" I found that it tried to go to the DNS server and translate the localhost to my external hostname.

Stopped the avahi-daemon and then it worked ok.

After further investigation I found that i had "hostname.domain.local" in my /etc/resolv.conf !

---

