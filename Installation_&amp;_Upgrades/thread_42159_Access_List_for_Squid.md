---
title: "Access List for Squid"
date: 2005-06-16
forum: Installation &amp; Upgrades
---

### Post by iyanski on 2005-06-16
[FONT=Verdana]I'm new to linux and bene playing for a few days. I'd like to ask if it's possible for squid to have it's ACL on another file? How would that be?

I'm planning to have my Squid to give access only to users I allow.[/FONT]


 :-)

---

### Post by desdinova on 2005-06-16
[QUOTE=iyanski][font=Verdana]I'm new to linux and bene playing for a few days. I'd like to ask if it's possible for squid to have it's ACL on another file? How would that be?

I'm planning to have my Squid to give access only to users I allow.[/font]


 :-)[/QUOTE]

Any particular reason why you want to move the squid config to another file - if you go to the squid website there's a full and detailed howto on its setup

---

### Post by iyanski on 2005-06-16
coz what im planning to do is to allow access only to users who have accounts in the Active directory. 

Extract the list of users from the Active Directory(selected users)
Write it in a file
Then have squid lookup to the list

Is there any existing implementation of this setup.

My goal is to limit access to sites to those who are entitled to have access.

---

### Post by desdinova on 2005-06-16
Have a look at squidguard - installable via Synaptic

---

