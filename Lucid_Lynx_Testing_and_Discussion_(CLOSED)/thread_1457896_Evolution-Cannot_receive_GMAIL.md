---
title: "Evolution-Cannot receive GMAIL"
date: 2010-04-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Rifester on 2010-04-19
Is anybody else having this problem?   I have set Evolution up in previous versions successfully.   I have followed the Ubuntu, Evolution, and Gmail guides.   I have even set the delete upon reading feature in Gmail.   And verified that after send/receive in Evolution that the emails were deleted from Gmail, but they never show up in Evolution (it even shows retrieving message 1 of 1).   Any ideas?  Sending email is working fine.  I am stumped.

---

### Post by UpSignal on 2010-04-19
i'm also experiencing that. to be honest, it retrieved the first mails, when i first configured it. but now...i was like 2 days without receiving any mail. i found that weird, so i went to my inbox with the browser, and then mails were there. the applet didn't warned me

---

### Post by linden940 on 2010-04-19
64bit here....able to GET mail from Gmail with evolution

---

### Post by Rifester on 2010-04-19
Linden940,
Could you please post your Receive Mail set up from properties in Evolution?
I am fairly certain mine is set up correctly but I want to confirm with somebody who is receiving their Gmail.
 
Thanks!

---

### Post by linden940 on 2010-04-19
in account editor for evolution for Gmail is as follows

Receiving email

  server type = Pop

  server = pop.gmail.com

  Security = SSL Encryption

Sending email

  Server Type = SMTP
  
  Server = smtp.gmail.com
 
   Security = SSL Encryption




everything else is default...

I DO have it set to remember my password but i dont think that is any here or there

---

### Post by linden940 on 2010-04-19
I hope that was helpful

---

### Post by espen77 on 2010-04-19
This setup works for me, also on 64-bit system.

Recieve:
Server Type: IMAP
Server: imap.gmail.com
Security: SSL
Authentication: PASSWORD

Send:
Server Type: SMTP
Server: smtp.gmail.com
Security: SSL
Authentication: Login

---

