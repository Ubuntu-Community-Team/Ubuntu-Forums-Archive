---
title: "apt-get messing proxy-string up?"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by Rigoletto on 2010-12-10
Hi,

sorry for this apt/proxy post, i see a lot but dont find my problem.

I freshly installed 10.10 server with openssh-server during install, and filled the proxy question with our correct proxy xxx:8080. 
ssh is working without do anything after install :)

If i take a look at apt.conf its looks correct with:
```
Acquire::http::Proxy "xxx:8080";
```But if i try a
```
sudo apt-get update
```the connection cannot build up:

```
Verbindung mit 8080:80 kann nicht aufgebaut werden (0.0.31.144). - connect (22: Invalid argument)
```The ip is missing and something added an extra :80 to the port.
How to solve this?

ping into internet are working, names are sloved, www-browser isnt working.

greetz
Rigoletto

---

### Post by Rigoletto on 2010-12-10
:redface: I should more playing around, specially as linux noob :)

With adding a "http://" infront of the ip:
Acquire::http:: Proxy "http://xxx:8080";

it works.

What about checking the user input´s during installation ;)

greetzs
Rigoletto

How could i mark a post as sloved?

---

### Post by sikander3786 on 2010-12-10
Yes, you needed to specify the protocol HTTP there ;-)

Glad to know that you figured it out yourself :-)

Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

