---
title: "Confused PHP version"
date: 2016-12-03
forum: Installation &amp; Upgrades
---

### Post by xinul2 on 2016-12-03
The following is effecting our  phpBB website running on a linux server. I'm hoping someone can recommend a fix or point me to a  solution.

During the summer, without realizing it, the linux server  running our phpBB website had the version of php updated. Our phpBB  website was then broke as the php version was now one not supported by  phpBB.

Was able to get phpBB running again, but now's here the problem. Seems we have a confused mixed php versions situation.

At the linux server command line doing php -i|grep 'PHP Version" returns 7.0.9-1+deb.sury.org~xenial+1

In our phpBB website checking the PHP information I see PHP Version 5.6.24-1+deb.sury.org~xenial+1

We  only want the PHP version 5.6.24 How do I fix the linux server  believing php 7.0.9 is in use? This is causing a sendmail problem as we  no longer get phpBB notifications, emails, etc. Sendmail worked fine  before the mistaken php update.

I'm a volunteer for non profit organization trying to both administer and webmaster their website.

Thanks.70

---

