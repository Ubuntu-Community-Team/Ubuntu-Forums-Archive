---
title: "Internet Slow 100Mbps to 1.5Mbps"
date: 2010-04-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Crunchy the Headcrab on 2010-04-20
I have fiber at my house.  For some reason the internet has been unbearably slow on my Linux machine.  It has gone from 100Mbps to 1.5Mbps!  Has anyone else been having these issues as a result of a recent update?

---

### Post by Dayofswords on 2010-04-20
you normally get 100mb/s?
you can only download as fast as the source server can go


(i lived with dial up until 3 months ago... so please consider yourself fortunate with your speed, "unbearably slow" it is not:))

---

### Post by Crunchy the Headcrab on 2010-04-20
Yeah, it's usually between 100-120Mbps down and 20Mbps up.  I won't be able to enjoy it for long though, because I'm moving soon and I doubt my new place will be wired with fiber.  I've done the dial-up also.  In fact I've only had broadband for the last couple of years.

Edit:  Just to clarify I'm not talking about the repositories or even any given website.  Everything is slow.  I did some speed tests even.  Something isn't right.  It seems to just be this machine.

---

### Post by bikeboy on 2010-04-20
Can you test LAN only file transfers to see if it's slow networking across the board?

---

### Post by aviramof on 2010-04-20
i too have noticed that my internet connection is slower in linux at least in terms of download speed  via transmission not surfing.

---

### Post by oobuntoo on 2010-04-20
> **Crunchy the Headcrab said:**
> Yeah, it's usually between 100-120Mbps down and 20Mbps up. ...

100-120Mbps down and 20Mbps up? That is damn fast! Where do you live and how much does it cost?

I pay $48/month for 7Mbps down/750Kbps up with Time Warner's RR.

---

### Post by Crunchy the Headcrab on 2010-04-21
> **oobuntoo said:**
> 100-120Mbps down and 20Mbps up? That is damn fast! Where do you live and how much does it cost?

I pay $48/month for 7Mbps down/750Kbps up with Time Warner's RR.
I live in Utah.  I don't know how much it costs because I share the bill with several other guys.  I think it comes out to about $50/month.

BTW my slow internet problem has been resolved.  I don't know what it was but things are peachy again in the world of Linux :)

---

### Post by QLee on 2010-04-21
> **Crunchy the Headcrab said:**
> I live in Utah.  I don't know how much it costs because I share the bill with several other guys.  I think it comes out to about $50/month.

BTW my slow internet problem has been resolved.  I don't know what it was but things are peachy again in the world of Linux :)

Well, there's some useful troubleshooting information, the connection is shared. Presumably you mean shared through a router not share a modem one-at-a-time. So one thing you might want to consider Crunchy is that whatever total bandwidth is possible on the connection will be shared and, if no means has been instituted for load balancing, it might be that one of the others was using a lot of bandwidth at the time you saw what you described. That would be my guess with the information I've seen here.

---

