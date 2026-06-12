---
title: "can't install phpmyadmin on ubuntu 14."
date: 2016-06-01
forum: Installation &amp; Upgrades
---

### Post by tross2 on 2016-06-01
sudo apt-get install phpmyadmin 
 seem to install the package but I can't find the phpmyadmin directory anywhere (it is not in etc, usr, var , unless it's  in another dir)
also when I try to uninstall phpmyadmin, the apt-get states it's not installed.

1) it looks like I using the correct command to install  
2) what commands can I use to see if it is installed ( the install process flashes by quickly, that I can see any errors)
3) how much space is needed? ( I think there is about 150 meg free (out of 260 meg) on the primary drive)  ( all my data and etc, is on a 1tb secondary drive)


other:
this is a stand alone server (on it's own box, not on a VM, not running any gui interface, command line only.) 
I do not use terminal or remote to the box ( it has it on monitor, etc)

apache2 is installed and working.
MySQL is installed and working.
php is installed and working.

I have a web site (using php, html, and JS) that I can upload to and it store the info in the database( file name , uploaded by , etc...)
and I can (thru command line) connect to the database and select from the table(s).

TIA

Tim

---

### Post by tross2 on 2016-06-14
I was able to fix this this myself by using the following: 
( tried some of these before without success (did not try autoremove) but using them all at the same time and some more than once, worked)
[FONT=Courier New]sudo apt-get install -f 
[FONT=Courier New]sudo apt-get update
[FONT=Courier New]sudo apt-get upgrade
[FONT=Courier New]sudo apt-get clean ( did not really seem to fix anything)
[FONT=Courier New]sudo apt-get autoclean ( did not really seem to fix anything)
[FONT=Courier New]sudo apt-get autoremove ( This seem to be the key to fix the issue , removed old pkgs and freed up disk space)
**sudo dpkg –configure -a  ( not sure what the did.)**
[/FONT]
[B]sudo apt-get install phpmyadmin  ( now this installed the pkg and created the folder)

[/B][/FONT]
[/FONT][/FONT][/FONT][/FONT]

---

