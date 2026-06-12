---
title: "Configuring Evolution"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by swoosh on 2007-06-14
Hi guys,

I have set up ypop on my Ubuntu. POP at port 5110 and SMTP at port 5025.

My configuration for Evolution is 

Receive Server type: POP
Server: localhost:5110
Username: xxx
Security: No encryption
Authentication type: Password

Send Server type: SMTP
Server: localhost:5025
[X] Server requires authentication
Use Secure Connection: No encryption
Authentication Type: PLAIN
Username: xxx

However, when I tried to send and receive, I am getting "Could not connect to localhost: Connection refused" error from Evolution.

Have anyone managed to solve this before?

Thank you.

Jerry

---

