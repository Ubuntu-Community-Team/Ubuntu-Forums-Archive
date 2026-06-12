---
title: "can't send out email after installtion"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by pupulolee on 2005-07-23
I am using the DHCP.  My ethernet is working very well. However I can't send out the email by MUTT. I got this kind of message:


This is the Postfix program at host localhost.localdomain.

I'm sorry to have to inform you that your message could not be
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                        The Postfix program

Please help me.

---

### Post by nemin on 2005-07-25
[QUOTE=pupulolee]I am using the DHCP.  My ethernet is working very well. However I can't send out the email by MUTT. I got this kind of message:

[Postfix message]

Please help me.[/QUOTE]
You can check your logfiles to see what's going wrong with postfix. You could also set another SMTP server (like your ISP's one) in mutt and send your mail using that server.

---

