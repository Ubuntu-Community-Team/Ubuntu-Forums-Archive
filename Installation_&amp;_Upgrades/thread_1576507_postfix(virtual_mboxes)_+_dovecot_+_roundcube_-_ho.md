---
title: "postfix(virtual mboxes) + dovecot + roundcube - how to stick it all together?"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by SkyHiRider on 2010-09-17
I've set up a postfix+dovecot+roundcube server.

Postfix is set to store incoming mails in /home/vmail/domain.xx/%login

How can I set the mail directory in dovecot so that it would fit. I plan on setting multiple domains so the domain name in the link should be some kind of variable, tied the variables noted in the dovecot config but they dont seem to work.

I want to be able to set two unix users on the server that will have access to several mailboxes and aliases, and also be able to add or remove and alias from an user if needed. What would be the best course of action to achieve this result?

---

