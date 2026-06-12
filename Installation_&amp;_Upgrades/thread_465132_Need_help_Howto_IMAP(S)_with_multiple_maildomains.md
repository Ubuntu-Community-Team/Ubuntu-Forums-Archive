---
title: "Need help: Howto IMAP(S) with multiple maildomains?"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by zakhooi on 2007-06-05
Hi,

Currently I'm using kerio mailserver as IMAPS mailserver but I'd like to change to one of the free mailservers like courier, cyrus or uw.
At this moment kerio handles mail of multiple users on multiple maildomains.
So: the server runs on domain1.com but kerio handles [email]user1@domain2.com[/email], [email]user2@domain2.com[/email], [email]user3@domain3.com[/email], [email]user4@domain3.com[/email] (it fetches mail from pop3.domain2.com and pop3.domain3.com).

Now I'd like to do exactly the same on courier, cyrus or uw or maybe another IMAP(S) maildaemon.

I really need advice on this. This is about a huge amount of emails kept from over 6 years that I like to transfer into the new set up.

Can someone please advice me WHICH IMAP(S) maildeamon to use and preferably a step-to-step install/configuration guide and a step-to-step conversion guide to transfer the emails from kerio into the new mailserver.


Please advice, I cannot afford to let this fail.

Thanks in advance

---

### Post by zakhooi on 2007-06-07
bump

---

### Post by esavato on 2007-06-07
The Linux Reality podcast just covered this topic in detail.  He explained how to download all of your pop mail and then use IMAP to serve all of those accounts.  This involves creating different users for each mailbox and such.  Here is a link to the show and details...
[http://www.linuxreality.com/podcast/episode-61-home-servers-part-7-simple-email-server/](http://www.linuxreality.com/podcast/episode-61-home-servers-part-7-simple-email-server/)

---

### Post by zakhooi on 2007-06-09
Thanks esavato,

However, this tutor is not what I was looking for since I miss the following:
Apart from the functionailty I mentioned in the startpost I also need to be able to

- Send mail to a specefic smtp host which is depending on the from-address
  e.g.  a mail send from [email]user2@domain2.com[/email] needs to be send to smtp.domain2.com with from-address [email]user2@domain2.com[/email]
  but a mail send from [email]user3@domain3.com[/email] needs to be send to smtp.domain3.com with from-address [email]user3@domain3.com[/email]
  etc etc etc

- have separate inboxes for each mailaccount. In your example all mail is delivered to one inbox.
  Therefore a login mechanism should make sure which inbox to use.

again, I'm looking for an alternative to kerio-mailserver which provides the same working environment as kerio does. Otherwise it's nog worth for me to migrate

Any more ideas?

---

### Post by zakhooi on 2007-06-19
bump

---

