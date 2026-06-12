---
title: "Evolution and Google Mail"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by Tourdog on 2009-12-26
I'm using an Acer Aspire One and boot Ubuntu 9.10 Netbook Remix from a USB flash drive.  I can write Evolution emails and send them via Google Mail (SMTP).  It works well.  But, I cannot get the problem solved on "receiving" emails via IMAP.  
How do you get Google Mail (Evolution is not on their preferred supported list) to allow Evolution to receive those emails.  I've made various changes in Edit, Preferences, etc but to no avail.  IMAP at my Google Mail Account is very simple..................   sending email works perfectly.  I just can't get configured to receive any!

Any help would be appreciated!   TIA!   :)

---

### Post by Spinx on 2009-12-26
Tourdog, I'm not an expert but I set up using POP rather than IMAP.

Under Account Editor use

Server type: "POP"

Server:  "pop.gmail.com"

That said, I have found Mozilla Thunderbird meets my needs and I nolonger use Evolution.

---

### Post by Tourdog on 2009-12-27
Spinx,
Good deal!  I've completed POP and it sends and receives my Google mails perfectly!
Thank You!   :)

---

### Post by stew721 on 2009-12-28
They have "Other" listed for e-mail clients.  You didn't select it, why?  The IMAP settings can be found [here]("http://mail.google.com/support/bin/answer.py?answer=78799").

One other thing you may want to take note of:  Google automatically saves a copy of all sent mail in the Sent folder/label.  Therefore, in Evolution (or any other client for that matter), select the trash folder as the location to save sent mail or don't save sent mail at all; Google does it for you when it's passed through their SMTP server.

---

