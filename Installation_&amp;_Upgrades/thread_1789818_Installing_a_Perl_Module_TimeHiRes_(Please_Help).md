---
title: "Installing a Perl Module Time::HiRes (Please Help)"
date: 2011-06-24
forum: Installation &amp; Upgrades
---

### Post by JonnySnip3r on 2011-06-24
Hey guys i have searched high and low on the internet but i cannot find a way to install this module. Its called Time::HiRes I have tried a few things with no joy.

Can anyone help? 

Thanks.

---

### Post by Lars Noodén on 2011-06-24
It appears not to be in the repository.  Which other methods have you tried?  You might be able to install from [CPAN](http://www.cpan.org/misc/cpan-faq.html#How_install_Perl_modules).  See -MCPAN

---

### Post by Lars Noodén on 2011-06-24
Here is the request for packaging it:

[https://bugs.launchpad.net/ubuntu/+bug/801532](https://bugs.launchpad.net/ubuntu/+bug/801532)

---

### Post by gmargo on 2011-06-24
**Time::HiRes** is included with the **perl** package; there is no need to install it separately.

---

### Post by Lars Noodén on 2011-06-24
Thanks. Sorry I missed that one.

$ perl -e "use Time::HiRes"

---

