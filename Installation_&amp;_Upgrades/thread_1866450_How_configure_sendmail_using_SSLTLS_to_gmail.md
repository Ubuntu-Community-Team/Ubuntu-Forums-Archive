---
title: "How configure sendmail using SSL/TLS to gmail"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by securitysupplies on 2011-10-21
Hi friends, 

I want to set up the Sendmail on Ubuntu 10 to use Googlemail server as my relay host. You know Googlemail is using SSL/TLS that seems to me not supported by Sendmail by default.

I've searched around and find a lot of doc (not Ubuntu specific) all talking about Sendmail plus openssl and Cyrus-SASL package.

I've apt-get Sendmail. Openssl is also installed original. However, I find no Cyrus-SASL, I tried 

apt-get install cyrus-sasl2

not found.

I am confused.
- is the above way the correct procedure for Ubuntu
- is that still the only way to set up for SSL/TLS
- or the name for SASL package is not cyrus-sasl2

Hope someone could give me a helping hand.

Thanks in advance.

Rgds
Den

---

### Post by jjcv on 2011-10-22
I suggest you try using postfix instead of sendmail (outdated really).

There are lots of howto available on configuring postfix to use gmail.  Do a little googling.

---

### Post by m3bik on 2011-10-22
I've set up net_smtp before using php to send mail through googlemail. Also made a script to send mail via the command line.. Never any luck with sendmail

---

### Post by securitysupplies on 2011-10-22
if so, i think i really move in a wrong direction, i'll explore those few suggestions and it'll be my pleasure to update you further experience.

many thanks.

---

### Post by securitysupplies on 2011-10-23
I eventually have the Postfix with SSL/TLS setup for using Gmail. Yeah, there are much more material for this setup and believe it's much closer to my problem solved.

However, I'm still in trouble. See if more gentlemen could help.

Now I installed Postfix & Cyrus-SASL2. I use

sendmail -bv [email]a_user@gmail.com[/email]

mailq see mail still in queue, unable to go!
connect to smtp.googlemail.com:25: Connection timed out

- I wonder why Postfix looks to me still using port 25
- actually should i use smtp.gmail.com:587 or smtp.googlemail.com:465?

See if you'll have any idea.

Thanks in advance.


Rgds,
Dennis

---

