---
title: "firefox is not working"
date: 2005-08-07
forum: Installation &amp; Upgrades
---

### Post by heart_reaver on 2005-08-07
heeya,


By instaling ibc6 package from debian i got othere packages destorted. After getting update by Ubuntu Packet Manager for firefox at the time of install it give errror log as:

---------------------------------------------------------------------------------------------------------------------------------------
[B]E: /var/cache/apt/archives/mozilla-firefox_1.0.6-0ubuntu0.1_i386.deb: trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox

E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.6-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support[/B]

---------------------------------------------------------------------------------------------------------------------------------------



Then i try to uninstall it by symantic but the same log as above is coming.

I am know using galeon but i miss firefox :wink:

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
 i have Ff 1.0.6 installed as a stand alone program on the /home partition

it maybe worth while trying the download from Mozilla and see if that gives any improvement ...

---

### Post by greyhound4334 on 2005-08-07
Not sure I fully understand the problem you're having, but this might help:

You should be able to install firefox 1.06 from the standard ubuntu repositories with apt-get.

If you've messed around with your sources.list, you may want to restore it to the original one.  Then run apt-get update, then apt-get install mozilla-firefox.   And done!

If you've lost track of your sources.list, I think the only ones you'll need to get firefox are:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-security main restricted

Put these in a file called /etc/apt/sources.list, then run the commands above.

---

### Post by heart_reaver on 2005-08-08
[QUOTE=Gezzer]i have Ff 1.0.6 installed as a stand alone program on the /home partition

it maybe worth while trying the download from Mozilla and see if that gives any improvement ...[/QUOTE]
 Gezzer 

main problem is this know i am not able to install other packages after 
apt-get update

---

### Post by heart_reaver on 2005-08-08
greyhound4334


Well i have already included repositories in sourec.list but its of no use.

---

