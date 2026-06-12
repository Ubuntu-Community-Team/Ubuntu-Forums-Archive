---
title: "alternate upgrade requires network?"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by andres.ordonez on 2012-04-26
I have ubuntu 11.10 and want to upgrade to ubuntu 12.04 using the alternate install iso, however  after mounting it (directly or using a usb) the upgrade manager tells me that it failed to fetch the packages due to a problem with the network.

How can I upgrade without using the network?

---

### Post by nariub on 2012-04-26
you can use the alt iso as a package repo, 

when offered the upgrade change the repo location to use the CD..

It will only upgrade the repos it has on the CD and they will be as fresh as the day they were bundled.

---

### Post by andres.ordonez on 2012-04-27
Thanks for your answer nariub! It might be a silly question but, how do I change de repo location to use the CD (usb)?

---

### Post by Senior_Buckethead on 2012-04-27
Correct, if you use the alternate cd, it wont look for the network. Silly question, but have you downloaded, or obtained, the 12.04-alternate-i386.iso, or another iso?
See Ubuntu's notes on alternate installation here:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by darkod on 2012-04-27
I am not sure a cd upgrade needs any special mounting or booting with the cd.

Have you tried to boot your 11.10 and while it's running to insert the cd? Does an upgrade option pop up?

---

### Post by haresear on 2012-04-27
My experience upgrading with the alternate CD was that it offers the option of proceeding without a network connection, but then later ignores your choice and refuses to complete if it can't fetch updates from the internet.

---

