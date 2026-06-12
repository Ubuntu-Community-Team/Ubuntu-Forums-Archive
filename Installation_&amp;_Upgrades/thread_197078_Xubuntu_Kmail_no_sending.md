---
title: "Xubuntu Kmail no sending"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by Dutch on 2006-06-15
Hi Xubuntu 6.06 problemn with Kmail.

Because Balsa does not work under 6.06 I've started with Kmail.
Getting mail is now working, but sending ....

I'm using port 25
And usernam and so is the same like Balsa.

But with sendingmail I get no signal that something is going wrong.
Kmail just lets the mail in the out box.

I can click on sending mail but nothing changes !

---

### Post by djdicbob on 2006-07-14
Have you tried connecting to the mail server with another client to rule out bad server config, or mail server being down?  With that being said some email providers..(BlueHOst in my case) Put the popmail server on the standard  port 25, but the smtp goes out on port 26...I have a sneaky feeling thats the case!

Hope I could help.....


Viva La Ubuntu:cool:

---

### Post by lbriner on 2007-06-30
I had the same problem and it was because I hadn't set my sending account to log onto the outgoing mail server (using plain encryption). I got no error messages either but once I told it to log on, it was fine.

---

