---
title: "Upgrading from 5.04 to 5.10"
date: 2005-09-17
forum: Installation &amp; Upgrades
---

### Post by Indigo2 on 2005-09-17
Hi, I have Ubuntu 5.04 Installed on my primary HD and it's the only OS installed on that HD.  I'm trying to use Ubuntu as my primary OS.  But I have very important questions regarding upgrading.  When 5.10 is released should I upgrade by using the CD or just use the Ubuntu Update manager to upgrade the OS? Secondly, I'm wondering if anyone has upgraded Ubuntu before because I would like to know if you lose any data files, settings, configurations, etc.? Is it a hassle to upgrade and would you just recommend to do a clean install?

Thanks.

---

### Post by John.Michael.Kane on 2005-09-17
[QUOTE=Indigo2]Hi, I have Ubuntu 5.04 Installed on my primary HD and it's the only OS installed on that HD.  I'm trying to use Ubuntu as my primary OS.  But I have very important questions regarding upgrading.  When 5.10 is released should I upgrade by using the CD or just use the Ubuntu Update manager to upgrade the OS? Secondly, I'm wondering if anyone has upgraded Ubuntu before because I would like to know if you lose any data files, settings, configurations, etc.? Is it a hassle to upgrade and would you just recommend to do a clean install?

Thanks.[/QUOTE]
 Yes you should be able to upgrade when 5.10 is relased. there should be no lost of files ect. if you do a clean install then you will have to back up all data that you need

---

### Post by Indigo2 on 2005-09-18
[QUOTE=SD-Plissken]Yes you should be able to upgrade when 5.10 is relased. there should be no lost of files ect. if you do a clean install then you will have to back up all data that you need[/QUOTE]


Thanks, but what is the best method through the update manager or through the CD?

---

### Post by seethru on 2005-09-18
[QUOTE=Indigo2]Thanks, but what is the best method through the update manager or through the CD?[/QUOTE]
 when the final is released, you'll update the same way people are updating to breezy now. Change all the references in sources.list from hoary to breezy, then apt-get update and then apt-get dist-upgrade.

---

