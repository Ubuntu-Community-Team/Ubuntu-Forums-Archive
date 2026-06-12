---
title: "(Simple) Local mail on Edubuntu LTS"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by RoDiesel on 2012-11-27
Hello
I'he just installed edubuntu 12.04 LTS and I have a few questions regarding the mail between users (local mail only). 
First of all, the background story: I need this setup for a classroom of max 10 users (no Internet access). The server is working fine with all the users (zero clients) connected. The local users need to communicate (locally) by mail using their usernames. When I create a new user, he/she must be able to send/receive local mail using Thundirbird.
Any ideas?
Thanks

---

### Post by darkod on 2012-11-27
You will have to install Postfix to do the mail sending/receiving, and Dovecot which is the interface with the email client (Thunderbird).

[https://help.ubuntu.com/12.04/serverguide/email-services.html](https://help.ubuntu.com/12.04/serverguide/email-services.html)

---

### Post by RoDiesel on 2012-11-29
Thank you darkod for your answer. I have managed to install postfix and dovecot and everything is working just fine. I'll try to find some other posts regarding the configuration of edubuntu (group users, block different programs or desktops for groups etc.). The whole purpose is to set up a small network that has to be managed (add/delete users etc.) by someone who is not very familiar with linux.
regards

---

