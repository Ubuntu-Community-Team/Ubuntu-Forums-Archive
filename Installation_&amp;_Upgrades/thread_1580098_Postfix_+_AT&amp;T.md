---
title: "Postfix + AT&amp;T"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by ekkis on 2010-09-22
I've been fed up with Time Warner for some time so recently I decided to get AT&T.  I run Postfix and generally laundered my mail through the TW mail servers.  in doing the switch I've had to reconfigure Postfix to do authentication since the old TW servers didn't require it.  Now I'm faced with a conundrum which I'm sure anyone in my situation would face and I'm hoping for a little light on the subject.

I have a couple of companies, and therefore a couple of e-mail addresses: [email]e@arix.com[/email] and [email]erick.calder@eligeregroup.com[/email].  In my mail client (which delivers to my postfix server) I have a couple of accounts (one for each address).  When postfix tries to deliver the message, it is denied with the following error:

[COLOR="Teal"]553 From address not verified[/COLOR]

here are the headers:

> Reporting-MTA: dns; mail.arix.com
X-Postfix-Queue-ID: B102B23EE5
X-Postfix-Sender: rfc822; [email]e@arix.com[/email]
Arrival-Date: Sat, 18 Sep 2010 16:59:52 -0700 (PDT)
Final-Recipient: rfc822; [email]erick.calder@tcw.com[/email]
Original-Recipient: rfc822;erick.calder@tcw.com
Action: failed
Status: 5.0.0
Remote-MTA: dns; smtp.att.yahoo.com
Diagnostic-Code: smtp; 553 From address not verified - see
   [http://help.yahoo.com/l/us/yahoo/mail/original/manage/sendfrom-07.html](http://help.yahoo.com/l/us/yahoo/mail/original/manage/sendfrom-07.html)
From: Erick Calder <e@arix.com>
Date: September 18, 2010 4:59:39 PM PDT
To: [email]erick.calder@tcw.com[/email]
Subject: verified 


after some testing I've determined the problem is that the AT&T server wants to see a @att.net address in the From: header... which means I cannot use it.  I've spend 1hr+ on the phone with the hopelessly useless support department and it's clear to me that if this is going to get solved, it isn't going to be with their help.  if I cannot make it work I'm going to cancel the service.

has anyone faced this issue?

thanks in advance,

- e

---

### Post by lisati on 2010-09-22
Err... that's Yahoo protesting, not AT&T. See [here]("http://help.yahoo.com/l/us/yahoo/mail/original/manage/sendfrom-07.html").

A stab in the dark here: Yahoo, together with ESPs that partner with them, sometimes like you to associate other email addresses you use with your main account before they let you use their servers to send email for that address.

---

### Post by ekkis on 2010-09-22
yeah, I did click on that link.  it leads me to a generic page that offers no relevant help.  I can log in but I'll just land in the Yahoo Member Center which also offers no choice for this needed "verification" of addresses.

additionally, I use plussed addresses so registering each address is not really feasible

---

### Post by efflandt on 2010-09-23
Do you have postfix properly configured to authenticate with the outgoing relay using your AT&T username/password?

I had something set up for that a long time ago. But that was when it was still SBC (using the Yahoo servers), but before they blocked outgoing port 25 (which you can get unblocked upon request), and before they switched to the secure ports.  Although, the outgoing Yahoo relay did require authentication at that time.

Do you have a block of static IPs or just a dynamic IP?

You might search the AT&T forums or ask at [http://www.dslreports.com/](http://www.dslreports.com/)

---

