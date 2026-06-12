---
title: "How to upgrade Apache/SSL/Mysql/PHP and mimic existing packages"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by kevnews on 2011-08-06
The Payment Card Institute (PCI) is requiring our site to upgrade to the latest versions of Apache, Mysql, OpenSSL, and PHP to fix known bugs that can compromise security.

I can build all these from source, but when I do "make install" they don't mimic at all what is installed (directory format, files, etc) when I do apt-get install (of whatever old versions are in the dist).

How can I find out how the packages are build via configure/make so that I can replicate the files, directory structure, etc, just with the current versions.

If there is a better way to address this I'm all ears.

thx in advance.

---

### Post by lkjoel on 2011-08-06
What version do they require of each?

---

### Post by kevnews on 2011-08-06
hi lkjoel, the anwer is:

openssl: they say greater than 1.0.0d for 1.x and 0.9.8r for 0.x
apache: 1.x 1.3.41-dev or higher, 2.0.x to version 2.0.64-dev or higher than 2.2.18
php: 5.2.1 or higher, for 5.3 must be higher than 5.3.6 or higher than 6.0 dev for 5.0.x when available

thx for any pointers. this is really a nightmare so far.

---

### Post by lkjoel on 2011-08-06
> **kevnews said:**
> hi lkjoel, the anwer is:

openssl: they say greater than 1.0.0d for 1.x and 0.9.8r for 0.x
apache: 1.x 1.3.41-dev or higher, 2.0.x to version 2.0.64-dev or higher than 2.2.18
php: 5.2.1 or higher, for 5.3 must be higher than 5.3.6 or higher than 6.0 dev for 5.0.x when available

thx for any pointers. this is really a nightmare so far.
Could you give me the output of these Terminal commands?
```
lsb_release -a
uname -a

```
For PHP 5.3.6: [https://launchpad.net/~bjori/+archive/php5](https://launchpad.net/~bjori/+archive/php5)

---

### Post by kevnews on 2011-08-06
Thx, here's the info

lsb_release -a

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.04
Release:        11.04
Codename:       natty

uname -a

Linux (obfuscated) 2.6.32-4-pve #1 SMP Fri Nov 26 06:42:28 CET 2010 i686 i686 i386 GNU/Linux

thanks again

---

### Post by lkjoel on 2011-08-06
For PHP 5.3.6: [https://launchpad.net/~bjori/+archive/php5]("https://launchpad.net/%7Ebjori/+archive/php5")

---

### Post by kevnews on 2011-08-06
ok thanks i appreciate it and will check it out.

my general question is: is there not a repository some where of how the packages are built so others can replicate/mimic the procedure to produce analogous packages but with somewhat higher revved software?

in other words, for a given package name, a way to find how it was built...
curious.

thx again!

---

### Post by lkjoel on 2011-08-06
> **kevnews said:**
> ok thanks i appreciate it and will check it out.

my general question is: is there not a repository some where of how the packages are built so others can replicate/mimic the procedure to produce analogous packages but with somewhat higher revved software?

in other words, for a given package name, a way to find how it was built...
curious.

thx again!
Yes it is possible, but for PHP 5, you don't need to build it.
Here is how you can install PHP 5.3.6:
```
sudo add-apt-repository ppa:bjori/php5
sudo apt-get update
sudo apt-get dist-upgrade

```

For OpenSSL and Apache, could you give me the link to the source? I'll be able to give you instructions on how to convert them into a package.

---

### Post by kevnews on 2011-08-06
thanks!

here's the openssl source:

[http://www.openssl.org/source/openssl-0.9.8r.tar.gz](http://www.openssl.org/source/openssl-0.9.8r.tar.gz)

and apache:

[http://apache.cyberuse.com//httpd/httpd-2.2.19.tar.gz](http://apache.cyberuse.com//httpd/httpd-2.2.19.tar.gz)

I'm very curious how go from the sources above to a package that installs similarly to the existing packages available/referenced from the dist.

PS: I can build from the above of course... and when I do there is no sites-enabled, sites-available, no folder called /etc/apache2, but of course I can get it to work but all our software kinda breaks because it looks so much different.

PPS: Another trick is how to tell apache to use the new openssl but I can probably figure that out, esp. if it just replaces the relevant .sa's, .so's and I rebuild ldconfig.


thx again!

---

### Post by lkjoel on 2011-08-06
Try this for apache and openssl:
```
sudo apt-get install checkinstall
./configure; make; sudo checkinstall

```

---

### Post by jgsancheza on 2011-11-04
Hello, is an old topic but thank´s for the information.

---

