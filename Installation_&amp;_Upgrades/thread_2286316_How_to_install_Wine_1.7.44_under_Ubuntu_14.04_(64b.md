---
title: "How to install Wine 1.7.44 under Ubuntu 14.04 (64bit)"
date: 2015-07-11
forum: Installation &amp; Upgrades
---

### Post by mirkko22 on 2015-07-11
Hello

I would like install Pokerstar with Wine: [https://appdb.winehq.org/objectManager.php?sClass=application&iId=2029](https://appdb.winehq.org/objectManager.php?sClass=application&iId=2029)

So I installed Wine from de Ubuntu software center but is the version 1.6 which as been installed and Pokerstar need 1.7.44 at minimum for well work. I tried a bunch of things for update to 1.7.44 but without success.

The follow page [https://www.winehq.org/download/ubuntu](https://www.winehq.org/download/ubuntu) explain the step...but when I type "sudo add-apt-repository ppa:ubuntu-wine/ppa" I get always the message "Cannot add PPA: 'ppa:ubuntu-wine/ppa'....Please check that the PPA name or format is correct.".

I made a "sudo apt-get update" then "sudo apt-get dist-upgrade" fro check against dependencies but no change...

Any clue ?

---

### Post by Vladlenin5000 on 2015-07-11
Just tested and it worked for me (I didn't actually installed/upgrade WINE but could easily add the PPA). I'm using 15.04 but that shouldn't make a difference adding a PPA.
Are there no other errors when you run the update/upgrade/dist-upgrade (yes, you should follow this order)?

---

### Post by mirkko22 on 2015-07-11
Thanks for your reply... I posted my question in another forum and other people tell me the same... They have no problem... My install is new (freshly installed in a new laptop) reason why I don't understand. I checked if all Package options are well ticked (Universe, third party and others) ans is the case... No I don't have any error...only this:

> dotcom22@dotcom22:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
[sudo] password for dotcom22: 
Cannot add PPA: 'ppa:ubuntu-wine/ppa'.
Please check that the PPA name or format is correct.
dotcom22@dotcom22:~$ 


I found also this ans tried to install:

[https://launchpadlibrarian.net/208901755/wine1.7-amd64_1.7.44-0ubuntu1_amd64.deb](https://launchpadlibrarian.net/208901755/wine1.7-amd64_1.7.44-0ubuntu1_amd64.deb)

But I get this:

[[img]http://pix.tdct.org/upload/thumb/1436623654.png[/img]](http://pix.tdct.org/upload/original/1436623654.png)


Any more clue ??

---

### Post by dino99 on 2015-07-11
no problem to add that ppa via synaptic
[https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa)

---

### Post by mirkko22 on 2015-07-11
> **dino99 said:**
> no problem to add that ppa via synaptic
[https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa)

yes already tested and I get the error displayed on the screenshot in the post above..

---

### Post by Vladlenin5000 on 2015-07-11
[http://www.linuxandubuntu.com/home/wine-1-7-42-released-install-update-in-ubuntu-linux-mint](http://www.linuxandubuntu.com/home/wine-1-7-42-released-install-update-in-ubuntu-linux-mint)   <- They explicitly recommend purging the old version. The error message complains about that (yes, I can read and understand French perfectly, not so much speak...). So, I would do exactly that, then try again to add the PPA. If the symptom persists then I would try to install it directly with the .deb which should now work with the older version removed.

---

### Post by mirkko22 on 2015-07-11
I tried to purge but I get a message telling the command purge cannot be found.. ??

> dotcom22@dotcom22:~$ sudo apt-get remove &#8211;purge wine
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet &#8211;purge
dotcom22@dotcom22:~$ 


Nice if you know some french... ;-)

---

### Post by Vladlenin5000 on 2015-07-11
It should be a double hyphen as in ```
sudo apt-get remove --purge (...)
```

Reason:
```
apt-get remove packagename
``` removes the binaries but not its configuration or data files.
You want ```
apt-get remove --purge packagename
``` in order to start fresh because it removes the configuration or data files along with the binaries. Alternatively, ```
apt-get purge packagename
``` should work as well.

---

### Post by mirkko22 on 2015-07-11
Ok I was able to purge successfully but I got a message telling Wine was not installed so nothing has been removed... Anyway the problem remain... that crazy..! Any others suggestions please ?

---

### Post by Vladlenin5000 on 2015-07-11
Crazy indeed... And I'm out of suggestions :(:(:(

---

### Post by mirkko22 on 2015-07-11
Ok thank for helping... I will update this topic if I find a solution...Cheers

---

### Post by mirkko22 on 2015-07-11
well I solved the problem. I had a certificate issue and the fact to do this solved my problem:

> sudo apt-get install --reinstall ca-certificates

---

