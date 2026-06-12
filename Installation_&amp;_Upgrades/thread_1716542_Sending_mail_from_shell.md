---
title: "Sending mail from shell"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by pr0fess0r on 2011-03-28
Hi Guys

I have a backup script on my Ubuntu 10.10 box which sits in my home business and connects to a PC and Mac via a LAN. I just want the "mail" command to work so I get notifications from the backup script etc. I've installed mailutils and postfix using the instructions here: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) but I stopped before the "Configure Postfix to do SMTP AUTH using SASL (saslauthd):" step because I don't need my box to be a fully fledged SMTP server, I just want to be able to use the mail command to send messages.
I setup Evolution and if I send mail to my company email address either from the shell or Evolution it "goes" i.e. there are no errors and the mailq is empty, but it's not delivered. I'm obviously making a newbie error but I can't find any site that explains just how to get "mail" going without the complexity of postfix - can anyone offer suggestions?

Cheers

---

