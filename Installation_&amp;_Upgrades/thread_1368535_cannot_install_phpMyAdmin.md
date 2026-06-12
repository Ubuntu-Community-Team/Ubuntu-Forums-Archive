---
title: "cannot install phpMyAdmin"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by stewie17 on 2009-12-30
Hi everyone.

I'm still fairly new to Linux, so please bear with me. Yesterday I upgraded to PHP 5.3.1, which went off fine. My problem is that I did a dist-upgrade and it removed phpMyAdmin. Now I cannot re-install the program either in the terminal, or in Synaptic (both give me errors saying the required files are uninstallable), so I downloaded the lastest version and placed it in var/www/. I tried to setup the config.inc.php file and now I get a 403 error.:confused:

To upgrade PHP, I followed the instructions at:
[http://blog.astrumfutura.com/archives/427-Installing-PHP-5.3.1-On-Ubuntu-9.10-Karmic-Koala-With-aptitudeapt-get.html](http://blog.astrumfutura.com/archives/427-Installing-PHP-5.3.1-On-Ubuntu-9.10-Karmic-Koala-With-aptitudeapt-get.html)

My config file is just a simple file (from the phpMyAdmin Documentation) which looks like this:
<?php

$i=0;
$i++;
$cfg['Servers'][$i]['user']          = 'root';
$cfg['Servers'][$i]['password']      = 'cbb74bc'; // use here your password
$cfg['Servers'][$i]['auth_type']     = 'config';
?>

Up until I upgraded PHP, phpMyAdmin was working fine. I can create a db in the terminal, but I prefer not to have to do so. Any help is greatly appreciated.

---

### Post by pytheas22 on 2009-12-30
I'd work harder to install it using a package instead of from source; it will probably be easier that way, and will make it simpler to remove or upgrade phpmyadmin later.  What error did Synaptic give you when you tried to install that way?

---

