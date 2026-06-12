---
title: "Howto Install 7.10 with bootpart"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by metramo on 2007-11-03
I installed Ubuntu with the objective of using boot.ini and adding a line using bootpart.

During the installation i checked "no boot manager" under advanced so that the installation program
would not overwrite the windows stuff.

I have windows installed on e and it boots from e.

I executed bootpart and partition 4 was identified as where ubuntu was installed.

Then I did bootpart 4 ubuntu7-10.boot ubuntu

This crated the file ubuntu7-10.boot under e:\
but no additional entry was created in boot.ini

So I added e:\ubuntu7-10.boot "Ubuntu 7.10" in boot.ini

When I boot I get the question
Windows
Ubuntu 7.10

But when I select Ubuntu it won't boot

Where did I go wrong?
- should I not have checked "no bootloader" during the installation ?
- should I have added the parameter lbasomething to bootpart 

Thanks in advance

[email]ragnar.moller@gmail.com[/email]

---

