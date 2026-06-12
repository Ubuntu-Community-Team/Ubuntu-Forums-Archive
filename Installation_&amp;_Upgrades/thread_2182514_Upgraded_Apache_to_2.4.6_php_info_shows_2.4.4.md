---
title: "Upgraded Apache to 2.4.6 php info shows 2.4.4"
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by Deronius on 2013-10-21
I recently upgraded my web server to apache 2.4.6.  apache2 -v returns:

Server version: Apache/2.4.6 (Ubuntu)
Server built:   Sep 23 2013 06:56:57

However, when I go to my phpinfo page, it still shows Apache 2.4.4 as the version.  I've restarted apache.  Any ideas on this discrepancy?

---

### Post by Kirboosy on 2013-10-21
You may need to upgrade your php. What version are you running?

Also a small chance it could be cache related you might want to try clearing your browser cache.


Hope that helps!
~Caboose

---

### Post by Deronius on 2013-10-21
I'm running 5.4.16.  I see that the latest stable version is at 5.4.21. I added ondrej/php5 which has up to php 5.5.5 and did the upgrade but I'm still at 5.4.16.  I'd like to avoid compiling it myself but I may need to.  Thanks for the help.

---

### Post by Deronius on 2013-10-21
So for me this is how I solved things.  I reverted back to my server before the upgrade to apache and then executed (selecting no to installing maintainers version):

```

add-apt-repository ppa:ondrej/apache2
add-apt-repository ppa:ondrej/php5
apt-get update
apt-get upgrade
apt-get install php5 
service mysql restart
service apache2 restart

```

I should have just been able to do a install of php5 but I think I had mucked around and couldn't get back to the state I should have been in.

---

### Post by Kirboosy on 2013-10-21
Cool, glad it was an easy and clean fix.

Please use the thread tools to mark the thread as "Solved"

Thanks!
~Caboose

---

### Post by Deronius on 2013-10-22
Done and thanks for the help.

---

