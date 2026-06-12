---
title: "POSTFIX Problem with system mail name"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by fbesser on 2010-07-17
Hello everybody

i installed a mail server with postfix and some other stuff. Everything works great, but there is a big flaw:
My FQDN is static.183.101.46.78.clients.your-server.de (system mail name)
My domains are timefight.de and egliundbesser.ch (sites are in german, so...)

If I now send a mail from [EMAIL="admin@timefight.de"]admin@timefight.de[/EMAIL] to [EMAIL="my_address@hotmail.com"]my_address@hotmail.com[/EMAIL], then the mail gets through, but it comes from [EMAIL="admin@static.183.101.46.78.clients.your-server.de"]admin@static.183.101.46.78.clients.your-server.de[/EMAIL]
(so the domain timefight.de gets replaced by the FQDN)

It is however not a bug: If i use telnet localhost 25 and send a mail from there, i can enter
"mail from:<admin@timefight.de>" and it is also received as [EMAIL="admin@timefight.de"]admin@timefight.de[/EMAIL]

Can you guys help me out in WHICH CONFIGURATION FILE there is a specification to exchange the domain with the FQDN of it?

Thanks in advance
fbesser



EDIT: SOLVED!

I used squirrelmail, a webmailer. Since there were multiple domains squirrelmail didn't know which one to use, so it completely messed up. Used Mail (Mac OS) and an iPad, both worked flawlessly.
Damn, 4 hours for NOTHING!

---

