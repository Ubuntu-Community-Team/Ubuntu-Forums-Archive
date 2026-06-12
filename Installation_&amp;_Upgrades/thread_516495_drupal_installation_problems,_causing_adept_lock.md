---
title: "drupal installation problems, causing adept lock"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by howardde on 2007-08-03
Hi i decided to try out drupal, so I used adept to download and install it.

During the process debconf gave the following error:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/myslqd/mysqld.sock'(2)

...and now the adept database is locked, and adept is read mode only. I have rebooted, after trying to make sure no apt-get console was open etc.

Searching the forums here for a solution to that, i've found and tried this:

sudo apt-get -f install

sudo dpkg --configure -a

The first cmd asks me to manually type the second one in, and that runs the same program (ableit inconsole) that throws the original ERROR, as noted above. In console I get:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/myslqd/mysqld.sock'(2)

Can anyone help please?

---

### Post by az on 2007-08-03
I would suggest removing drupal and installing it by hand.

[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

The version in the repos is already insecure and you are going to have to keep it up-to-date yourself anyway.  As well, you are going to need to fetch and install the extra modules yourself.

You should use the package manager to maintain your LAMP stack, but the web applications on top of that should be maintained by hand.

Drupal has a update-status module that is very useful.


To fix your database problem, how did you install LAMP?  Perhaps you want to reset your mysql-root password if you don't know what the password is before you install Drupal (currently 5.2).

---

### Post by howardde on 2007-08-03
To fix your database problem, how did you install LAMP? Perhaps you want to reset your mysql-root password if you don't know what the password is before you install Drupal (currently 5.2).

Hi! Thanks for your answer. I will certainly install it by hand next time!

I installed Linux via a disk iso, apache, mySQL and php i left to adept, they wern't on my system before, to the best of my knowledge. I figured adept would realize that drupal depended on them and install them as well.

Do you know how I can uninstall drupal effectively from the command line? 
Is it 'sudo apt-get uninstall drupal'?

Thanks for your time

---

### Post by howardde on 2007-08-03
removal:
sudo apt-get remove drupal-5.1

this seemed to work but it couldn't remove the datase, giving th e same error as before:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I've run update and upgrade succesfully now.

---

### Post by az on 2007-08-03
Okay, what apache, php and mysql packages do you have installed?  List them all.

---

### Post by howardde on 2007-08-03
hi az,
This problem is solved now! (adept being locked)

Thankyou for your help :)

I have installed the stack as per:

[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

..and am onto my next problem...cringe...

---

