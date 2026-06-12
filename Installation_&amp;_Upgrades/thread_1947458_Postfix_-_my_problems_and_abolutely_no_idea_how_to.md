---
title: "Postfix - my problems and abolutely no idea how to continue"
date: 2012-03-26
forum: Installation &amp; Upgrades
---

### Post by martinpe on 2012-03-26
Dear Ubuntu people,

I am a Drupal developer and I use Ubuntu as a VM for my dev neeeds. 

For a project, I need to work with sending mails. Simple mails which have to be sent out. On the production, that won't be a problem since everything is already set. My personal challenge is to set up mail locally to 

a) see if a mail is being genereted and sent and
b) how the mail looks in the end on a client such as thunderbird.

Right now my personal fear of not even being to install a mail server such as Postfix really has come true. After looking at this guide over and over and over again [https://help.ubuntu.com/11.10/serverguide/C/postfix.html](https://help.ubuntu.com/11.10/serverguide/C/postfix.html), I still couldn't make sense of it.

Using PHP's mail() function returns a success every time but where mails are being stored is beyond me. Using the configuration attached, I still cannot find the mails. Where are the mails stored? I don't see them anywhere :(

2ndly, if I wanna use the Thunderbird to check if the mails look allright, what configuration (host, mail address, etc.) do I have to use?

I would love to search within the forum IF i would just know what the problem is exactly. Unfortunately, having worked on Windows for so many years, I am still a very bloody beginner in Linux, which is why I still don't get some concepts.

I am running Ubuntu 11.10. inside a VM (using VM Player).
main.cf from postfix is attached.

Please help.

---

