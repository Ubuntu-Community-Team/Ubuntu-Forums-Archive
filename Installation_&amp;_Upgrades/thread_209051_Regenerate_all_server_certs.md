---
title: "Regenerate all server certs"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by fommil on 2006-07-04
Hi everyone,

I've finally managed to get all the servers I need up and running on the latest dapper: Apache2 with SSL, Postfix using TLS and SSL and Courier running SSL IMAP and SSL POP3.

When I was creating the certs, I was simply hitting enter all the time to speed things up... my server is not live yet and not using it's eventual domain name. Does anyone know an easy way to regenerate all the necessary certs? (or use the same one for all services, unless that's bad form) It would also be nice if I could place all the default machine details in the one place (e.g. Location, Company Name).

PS: many thanks to these two HOWTOs on how to set things up, especially the second which explains how to move the authentication processes into the Postfix chroot jail. A very messy way to set up SSL mail I must say, I was half expecting ubuntu would have made this easier, if not the default!
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p4](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p4)

---

### Post by DirtDart on 2006-07-04
Assuming you just want to generate a self signed certificate, and not a certificate request (you have to pay $$ to get a REAL certificate), check this link out:

[http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html](http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html)

---

### Post by fommil on 2006-07-04
[QUOTE=DirtDart]Assuming you just want to generate a self signed certificate, and not a certificate request (you have to pay $$ to get a REAL certificate), check this link out:

[http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html](http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html)[/QUOTE]

Thanks DirtDart, but I was already aware of this tool (it's needed to make the apache2 cert)... I was more asking if there was an easy way to regenerate *all* the certs on the system; i.e. for all the SSL servers I just mentioned, in one foul sweep. But I guess failing that, I'm sure I could resort back to using this tool to make them all.

---

### Post by DirtDart on 2007-04-13
Glad I answered this last July, as I just found my own post while looking on how to generate a self signed certificate for Apache!

---

