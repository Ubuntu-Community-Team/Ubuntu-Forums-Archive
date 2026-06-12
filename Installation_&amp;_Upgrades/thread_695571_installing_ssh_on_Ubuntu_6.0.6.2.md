---
title: "installing ssh on Ubuntu 6.0.6.2"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by zakaio on 2008-02-13
i have installed both the openssh-server and client on ubuntu 6.0.6. 2 server however when i tried and connect remotely using putty it wont allow me to connect.

i tried to run tail -f /var/log/syslog to see if i can get an indication of where the error is coming from but it wont show anything at all which now makes me wonder where the ssh log files are stored.

please need some pointers so that i can complete the deployment of Ubunutu. 


cheers:

---

### Post by stmurray on 2008-02-13
If you are having authentication problems they would show in /var/log/auth.log.  You didn't really say what problem(s) you are seeing.  Are you getting couldn't connect (connection refused) errors or authentication problems, RSA signature?  when you ssh, are you using the standard id you use when you log into the console?

---

### Post by zakaio on 2008-02-13
sean

I managed to look at the log under auth.log and its shows that I missed a : after ALL so is fine now.

many thanks for your help


cheers

zakaio p manoa

---

### Post by zakaio on 2008-02-13
it worked for a while then it just came up with Network error ...connection refused

i am checking the logs to see what causes it but would appreciate if you provide some pointers

cheers

zakaio

---

### Post by lespaul_rentals on 2008-02-13
Do you have a static IP address?  Is there any firewall or something similar that might be causing this problem?  Any typographical errors in iptables?

---

