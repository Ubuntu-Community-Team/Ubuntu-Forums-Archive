---
title: "First ever Linux install"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by zanzibarwinds on 2011-05-25
Hi

I am downloading Ubuntu 11.04 32 version and plan on installing this for my web development.

I come from an ASP.NET background but have been doing PHP via XAMPP and later Zend CE for the last year or two on my Windows 7 PC.

Installing packages etc for Windows is not always error free so have grown tired of this and decided to install the lastest Ubuntu.

I only plan for the moment to use the Linux install as a place to develop my PHP web apps in a proper environment.

Can anyone point me towards any online litertature that would help me set up this Ubuntu to replicate a web server as closesy as possible please.

Having never installed Ubuntu before I am under the impression that installing and then configuring everything involves a lot of shell commands and I have no idea where to start.

I plan on using PHP and mySql for multiple sites if its at all relevant.

Many thanks
John

---

### Post by linuxinstalledfromhdd on 2011-05-25
Here is a really nice one that I have used before. 

[http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-2)

---

### Post by zanzibarwinds on 2011-05-25
> **linuxinstalledfromhdd said:**
> Here is a really nice one that I have used before. 

[http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-2)

Many thanks linuxinstalledfromhdd.

---

### Post by linuxinstalledfromhdd on 2011-05-25
Also I keep a college textbook handy, it's Guide to Unix Using Linux 4th edition.

---

### Post by zanzibarwinds on 2011-05-25
Thanks again.

That install tutorial has worked fine, I installed ubuntu fine with apache2 etc without issue.

Struggled a little in getting the Ubuntu to link to my Win Vista PC (Which shares my internet connection) but have finally managed this after a couple hours of fiddling.

My current issue is getting websites installed.

The apache test site works as well as php if I place a test php within the same dir with phpinfo()

I could list here everything I've done but that would be somewhat boring.

Needless to say I followed this explanation without success:

[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

as well as

[http://apptools.com/phptools/virtualhost.php](http://apptools.com/phptools/virtualhost.php)

Cannot get website running on [http://localhost/mysite/](http://localhost/mysite/) or even with it mapped to port 8080

Its worth nothing when I began /etc/apache2/httpd.conf was empty

Please note 80 is currently used for normal internet access on this machine.

Any simple apache2 website config pointers would be appreciated.

---

### Post by zanzibarwinds on 2011-05-25
> **zanzibarwinds said:**
> Thanks again.

That install tutorial has worked fine, I installed ubuntu fine with apache2 etc without issue.

Struggled a little in getting the Ubuntu to link to my Win Vista PC (Which shares my internet connection) but have finally managed this after a couple hours of fiddling.

My current issue is getting websites installed.

The apache test site works as well as php if I place a test php within the same dir with phpinfo()

I could list here everything I've done but that would be somewhat boring.

Needless to say I followed this explanation without success:

[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

as well as

[http://apptools.com/phptools/virtualhost.php](http://apptools.com/phptools/virtualhost.php)

Cannot get website running on [http://localhost/mysite/](http://localhost/mysite/) or even with it mapped to port 8080

Its worth nothing when I began /etc/apache2/httpd.conf was empty

Please note 80 is currently used for normal internet access on this machine.

Any simple apache2 website config pointers would be appreciated.

Ok figured it out, somehow. No need to answer this.

Cheers

---

