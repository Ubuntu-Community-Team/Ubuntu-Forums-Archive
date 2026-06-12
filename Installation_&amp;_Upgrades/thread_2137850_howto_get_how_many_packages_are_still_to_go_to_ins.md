---
title: "howto get how many packages are still to go to install within apt-get dist- upgrade"
date: 2013-04-22
forum: Installation &amp; Upgrades
---

### Post by masuch on 2013-04-22
Hi,

I am interesting in to find out how many packages, within running installation process, are still have to be installed and / or upgraded, in terminal  ?
if is running apt-get upgrade or apt-get dist-upgrade I would like to know how many packages are still going to be installed and / or upgraded or have been installed / upgraded ?
Is it possible to count it by some command or somebody have some hint - (in man apt-get I did not find some) ?
(It does not have to be counted precisely, just approximately - lets say plus/minus ten packages in tolerance in that specific moment of progress.)

thank you,
kind regards,
M.

---

### Post by dino99 on 2013-04-22
when "apt-get upgrade" is ran, the details are shown, like: x package(s) will be installed, y packages will upgraded, z packages will be left back, ....

(but i'm sure you already knows that, so that question seems quite confusing)

---

### Post by masuch on 2013-04-23
well, those information is written before you start upgrade  - you get overview what you said.
I am talking about when you are already in installation process and during that process how to count it. Information within present continuous action, not before, not after action.

within the installation process you have no idea how many packages have been installed/configured Or how many packages are still going to be installed/configured. That's my question.

case:
The point of it is when the customer wants to know when the dist-upgrade is going to be finished - I can say - when it starts at 9 clock pm it will be tomorrow done - but when he came back to computer and it is still running than what can I say to customer ? He has to wait for another couple of hours if something did not break during the night upgrade or later on. So , I have no idea what to tell to customers how long is he going to have to wait - not even with hours precision - to be honest - customer is upset and I cannot say anything accurate to explain- just wait dear customer when it is done.

---

