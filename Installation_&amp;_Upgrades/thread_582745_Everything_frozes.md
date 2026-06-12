---
title: "Everything frozes"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Yuliya on 2007-10-20
I have installed the latest Ubunti version on a new computer with no previous system (HP 530) and everything looks great but after about 5 minutes it ALWAYS "freezes". I can't keep using it and have to restart and the same happens again and again.

---

### Post by Arenlor on 2007-10-20
Please boot and do nothing and I mean nothing at all (go have a smoke or a cup of coffee or go do situps or something while waiting) and let us know if it still reboots.

---

### Post by Yuliya on 2007-10-20
Right after I wrote that message it stopped doing that, though If I put it on "hibernate" mode then the whole thing stops working and then there is no way of getting back so I have to restart. I have read the things about Evolution Email and followed step by step the things but it just doesn#t work with my google account (it says time out).

---

### Post by Jive Turkey on 2007-10-20
The hibernate issue gets me too, I think it has to do with my video driver but I'm not sure, try standby instead.  The evolution thing should be easy to fix.  Make sure you enable POP service at the google website (for each account)

from google:
To enable POP in your Gmail account(using a browser like firefox or opera):

   1. Log in to your Gmail account.
   2. Click Settings at the top of any Gmail page.
   3. Click Forwarding and POP.
 4. Select Enable POP for all mail or Enable POP for mail that arrives from now on.
 5. Choose the action you'd like your Gmail messages to take after they are accessed with POP. 

Use these settings to set up evoution:

[http://mail.google.com/support/bin/answer.py?answer=13287](http://mail.google.com/support/bin/answer.py?answer=13287)

At the first screen for servertype, select POP, I didn't have to specify any ports, use your full email address and not just the user part that evolution fills in.  I think you need to specify TLS authentication for the smtp server

---

### Post by Yuliya on 2007-10-20
I will try the standby option now.
As for the email, I read all the information and enabled the POP and did everything step by step but still it says "Server time out" (or something like that)

---

### Post by Yuliya on 2007-10-20
I just discovered I can send emails, all I cannot do is receive them - is it a problem with the way I've set it? Because I read and followed every step

---

### Post by Arenlor on 2007-10-20
It could be, what is your settings?

---

### Post by Yuliya on 2007-10-21
pop.googlemail.com
stmp.googlemail.com

 as for the rest I follow exactly what it says on the instruction section (the bit about my account and the password) and I did enable POP in my google account

isn't that how it's done?

---

### Post by Arenlor on 2007-10-21
So your username in your client for the gmail part is just username right? Not [email]username@gmail.com[/email]
I don't know why but [https://www.opendns.com/start?device=ubuntu#step1](https://www.opendns.com/start?device=ubuntu#step1) that seems to be helping a lot of people with their problems.

---

