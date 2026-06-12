---
title: "Error: acpid, acpi-support, ubuntu-desktop"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by igorzolnikov on 2006-10-30
apt-get upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@igorzolnikov:~# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up acpid (1.0.4-5ubuntu4) ...
 * Loading ACPI modules...                                                                [ ok ] 
 * Starting ACPI services...                                                                     invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

Plz, help me. How can i resolve this problem?

---

### Post by doncarlos on 2006-11-24
I have the same problem after I do an upgrade dapper to edgy!

It solved the problem for me:

> 
manatorg  
First Cup of Ubuntu
	 	Join Date: Apr 2006
Beans: 2

 Re: Edgy Upgrade Problem 
hm, 

maybe i posted to fast. just solved the problem:
a manual:
Code:
sudo /etc/init.d/acpid stop
worked.
after that
Code:
apt-get -f install
ran fine.

may acpid package does not stop acipd bevor starting it...?

---

### Post by gsiliceo on 2007-07-16
same problem, same solution, thank you!

---

### Post by chrisxp on 2007-09-16
thanks, solved my problems too! although when i reboot and ubuntu-desktop attempts to load all i get it a 2-colour-tone-bar across the top of my screen! possible a gfx card issue? using a dell gx150 with standard card (rage or something)

---

### Post by kurund on 2007-09-24
I also had same problem with gutsy. Thanx for the solution..

kurund

---

### Post by viper233 on 2007-10-02
Same problem with Gutsy too, just did stopped acpid manually

sudo /etc/init.d/acpid stop

---

### Post by Chaoticwhizz on 2007-10-09
The solution above worked for me as well when upgrading to Gutsy Beta. THanks!

---

### Post by loscotec on 2007-10-26
Damn!! It didn't work for me.. 

The most important error message seems to be : 

acpid: can't open /proc/acpi/event: Device or resource busy
invoke-rc.d: initscript acpid, action "start" failed.

but I don't know how to try freeing resources.. (recent ubuntu and linux user)

I was upgrading form feisty to Gutsy on a AMD Opteron !

---

