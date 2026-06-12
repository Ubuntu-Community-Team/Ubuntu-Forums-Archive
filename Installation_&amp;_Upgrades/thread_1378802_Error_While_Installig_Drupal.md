---
title: "Error While Installig Drupal"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by seenu_gadu on 2010-01-11
Hi All
Ubuntu is a very nice OS to work on :)
I installed Ubuntu using Wubi on Windows 7.
I got most of the initial help from Ubuntu docs n forum.
Thanks for maintaining such a useful information. So far I  managed to work on.

But I hav to take up a small project to build a website based on Drupal.
Based on the documentation in the link below
[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

LAMS Server has been installed sucessfully using
sudo tasksel install lamp-server
But while installing Drupal 6 I gave the following command
sudo apt-get install drupal6Then I got the following error got the following error.
[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx curl dbconfig-common exim4 exim4-base exim4-config exim4-daemon-light libdb4.6 libt1-5 mailx php5 php5-gd wwwconfig-common
Suggested packages:
  eximon4 exim4-doc-html exim4-doc-info libmail-spf-query-perl swaks postgresql-client apache apache-ssl
The following NEW packages will be installed:
  bsd-mailx curl dbconfig-common drupal6 exim4 exim4-base exim4-config exim4-daemon-light libdb4.6 libt1-5 mailx php5 php5-gd wwwconfig-common
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory[/I]
I am not sure how to proceed from here. 

Sorry if this thread has been posted earlier and if it has been posted plz direct me to that thread.

Looking forward to your help and thank you in advance.

---

### Post by shredder12 on 2010-01-12
> **seenu_gadu said:**
> Hi All

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory[/I]


All this means is that there is another installation application open preventing you to install anything or you are trying to install 2 things simultaneously. Closing that application(synaptic or update manager) should work.

---

### Post by kellemes on 2010-01-12
By the way.. You better don't install Drupal from the repositories.. that version is old and needs to be upgraded after install anyway.
So setup LAMP and [get Drupal here]("http://drupal.org/").

---

