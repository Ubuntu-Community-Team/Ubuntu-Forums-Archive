---
title: "Just installed Ubuntu, Evolution dont work."
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by mrchaos101 on 2007-12-30
Just got this installed.

I am trying to get Evolution to work but it wont.

I get:

Unable to connect to POP server mail.xxxxxxx.com.
Error sending password: -ERR UserName or Password is incorrect

Please enter the POP password for [email]x.xxxxx@xxxxxxx.com[/email] on host mail.xxxxx.com

It works on my windows box with XP

---

### Post by Ekeluo on 2007-12-30
Have you configured your accounts? You probably did it on windows, have to specify your pop addresses and maybe ports, also check if your details are correct and that the authentication system selected is correct.

---

### Post by mrchaos101 on 2007-12-30
> **Ekeluo said:**
> Have you configured your accounts? You probably did it on windows, have to specify your pop addresses and maybe ports, also check if your details are correct and that the authentication system selected is correct.


I setup the user name and password and the name of the pop3 and smtp server.

I dont see any where to check for port.

As for authentication I assume it is password.

If it helps, the company that is hosting he email is host-my-site.com

---

### Post by forestpixie on 2007-12-30
to use a specific port in either receiving or sending - put it after a colon

eg
imap.uk.aol.com:993

---

### Post by ChadMMc on 2007-12-30
When I had first installed Ubuntu a few years back, I had had the same problem that you had.

I had called my ISP Tech support and we had discussed it. 

The solution was where in the account setups, the field where you put username (both receiving mail and sending mail), put the whole email address in there instead of just the username itself.

It worked for me.

Hope this helps.

---

### Post by J.Wilson on 2008-01-01
Mine has been doing this also, Only, though, when I first start Evolution. Once it is running, the Send/Receive works just fine. My settings worked for a while and then it just started messing up.

---

### Post by ugm6hr on 2008-01-01
Maybe use Thunderbird instead?  Works with multiple POP accounts for me.

---

### Post by J.Wilson on 2008-01-01
> **ugm6hr said:**
> Maybe use Thunderbird instead?  Works with multiple POP accounts for me.

I like evolution though. It worked fine for a while, but just recently started acting  up. It works fine once it is up and running. It only errors when it tries to Send/Receive on startup. :confused:

---

