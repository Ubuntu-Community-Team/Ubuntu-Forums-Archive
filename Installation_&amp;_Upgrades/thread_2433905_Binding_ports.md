---
title: "Binding ports"
date: 2019-12-27
forum: Installation &amp; Upgrades
---

### Post by kdmiller45 on 2019-12-27
I nmap shows port 25 is bound to 127.0.0.1, localhost and not allowing outside traffic
how do I bind that port to 0.0.0.0 or * to accept public traffic

Keith

---

### Post by SeijiSensei on 2019-12-27
In postfix, look at the [inet_interfaces]("http://www.postfix.org/postconf.5.html") directive. For sendmail, remove the Addr field in the DAEMON_OPTIONS parameter in sendmail.mc then rebuild sendmail.cf.

This question can be answered by searching at Google or reading the documentation for the application. Try doing that first before posting here.

---

