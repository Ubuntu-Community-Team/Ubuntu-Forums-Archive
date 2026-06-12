---
title: "what is ubuntu-minimal"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by reychun on 2010-10-10
When I was trying to upgrade my ubuntu from 10.04 to 10.10, I got this message:

[IMG]http://img203.imageshack.us/img203/801/screenshot1wh.png[/IMG]

WHAT SHOULD I DO NOW?!!! :confused:

---

### Post by sveterv on 2010-10-10
> **reychun said:**
> When I was trying to upgrade my ubuntu from 10.04 to 10.10, I got this message:

WHAT SHOULD I DO NOW?!!! :confused:


Probably you've lost connection to the update server (my guess), and this package could not be fetched to your system. This package is one really important as it provides information about basic system setup which is required for Ubuntu to work properly. On my 10.10 this package exists, so it should be available on your system also, and it is not, we can only guess what was wrong. Today all the update servers will be very busy (overloaded), so you can try to make an upgrade later, or use other methods, like there:
[https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades)
Go to section with "Upgrading Using the Alternate CD/DVD"
It requires downloading other .iso file than you have probably downloaded, but with this method most of the packages will be fetched from CD, and even without network connection upgrade should be possible (if installer will ask you, if you want any updates to be downloaded when upgrading tell NO).

If you want you can post there logs from /var/log/dist-upgrade, or if there is too many of them, try to look at them, usually at their end, there is a information telling what exactly went wrong, so instead posting all the log, post few lines from end of it.

That's what I can help you right now, I hope other people will still try to help you.

PS. Oh and at the end, if it was connection loss as I guess, than you can simply try to make an upgrade the way you were doing now again, it may stop again telling you something could not be found, but this time, it should not be a ubuntu-minimal package, so even if upgrade fails you will now know, that it is not related to that package, what can mean that it is due to overloaded servers that disconnects you. If that is the case, and you don't want to wait those few days, when servers will operate normally try alternate CD method from link I have posted to you in this post or change mirror you are using with Synaptic (Settings->Repositories->Source) to some other country (Netherlands is small country with fast connections so even if they are pretty far away from you, you can try that mirrors).

---

### Post by reychun on 2010-10-10
thanks! I will try the first way... because I checked those bug reports before me but I don't think the problem is solved yet. So if nothing works, I guess I will go for the alternate CD thing. Thanks! :)

---

### Post by freesitebuilder on 2010-10-11
Several bug reports for this, including [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/631426](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/631426)
India seems particularly hit, but I'm having this problem from UK. Haven't had a chance to try other mirrors yet.

---

