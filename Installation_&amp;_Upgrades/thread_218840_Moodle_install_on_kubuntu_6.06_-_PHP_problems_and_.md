---
title: "Moodle install on kubuntu 6.06 - PHP problems and solutions"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by marineBoy on 2006-07-19
Hi,
Not sure if this is the appropriate place for this but I thought I'd contribute anyway in case anyone else has similar problems. I've also posted it on the moodle.org forums.

The problem:
I was running kubuntu 6.06, apache 2.0.55, mysql 5.0.22, PHP 5.1.2 on a dell inspiron 6000 laptop. The install of moodle 1.6 was failing with a blank page. I tried

    * re-installing apache
    * re-installing php5
    * modifying php.ini to increase the memory_limit(?) to 24M from 8M

I then tried installing Moodle 1.5.4 which also failed.

Solution
I couldn't drop down to PHP 4.x because MediaWiki needs php>=5. I installed php 5.1.4 (and some libraries due to dependencies) from Edgy (the next distro version) and the install of 1.6+ went fine. Hopefully, I haven't screwed anything else up.


Regards,
Duncan

---

### Post by marineBoy on 2006-07-19
Ho hum, spoke too soon - the install went fine, but it still doesn't work - lots of blank pages. It's a PHP problem from what other information I've found, so I'll carry on and report back. Another late night of ](*,)

Regards,
MarineBoy

---

### Post by marineBoy on 2006-07-19
Ok, maybe not,  It installed OK but there were still loads of blank pages on adding users, teachers, courses, etc. It is working now.

I'm running kubuntu 6.06. This is what I did:

   1. copied /usr/share/doc/php5-common/examples/php.ini-recommended to /etc/php5/apache2/php.ini
   2. edited the file and uncommented the following in the Dynamic Extensions section:

    * extension=mysql.so
    * extension=mysqli.so
    * extension=gd.so

   3. Restarted apache

Now the pages that wouldn't display before all seem to work.

Regards,
Duncan

---

