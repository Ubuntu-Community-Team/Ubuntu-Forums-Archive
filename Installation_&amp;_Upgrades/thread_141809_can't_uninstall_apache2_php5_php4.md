---
title: "can't uninstall apache2 php5 php4"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by gheboy on 2006-03-09
dear all,

i have install apache2 and php5 also php4 (as cgi)...by using apt-get install.
now, i want to remove all of them ...

i have tried by using apt-get remove, apt-get remove --purge, and also dpkg -r,

and still cannot remove them...

could anyone help me....thanks before...

---

### Post by localzuk on 2006-03-09
Could you explain what happens when you try to remove them? Do you receive error messages?

---

### Post by gheboy on 2006-03-09
it said that "package is not install, so not remove"
(for php4 and php5)
but when i try with : [http://localhost/info.php](http://localhost/info.php)
info.php (is a file which i made to list php configuration)..it still works

meanwhile when i sudo apt-get remove apache2...it works and succeed..but not all of the folder which contain apache removed...

because i'm new in linux, i didn't know what should i do, if i re-install the ubuntu it takes a long time....:cry:

thanks 4  ur help..please help me...:-?

---

### Post by localzuk on 2006-03-10
It appears that you have not installed the package 'php5' or 'php4' but one of the CLI versions. Have you tried running 'apt-get remove php*'?

When you removed apache it will remove the application but not the content that is in whatever directories that you have set up (ie /var/www/html will still contain anything you have put in it...).

If you do a 'apt-cache search php' what do you get as an output (it may be quite large, so pipe it to a file like 'apt-cache search php > out.txt'). Have a look at the output and see if there are any which say 'installed'.

---

### Post by sudjatno on 2007-06-10
Hi,

Try using Add/Remove from the Desktop, Advance option, search for Apache2, remove installed packages.
This should remove all your installed Apache2. Have not tried for PHP5 or PHP4.

CHeers:D

---

### Post by devil_kills on 2007-12-26
next time test apt-get autoremove apache2 for my its work

---

### Post by masterdam79 on 2008-07-11
I'm getting the error when trying all of the above:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

