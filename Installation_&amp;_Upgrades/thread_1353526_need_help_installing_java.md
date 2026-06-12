---
title: "need help installing java"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by chillyomi on 2009-12-12
i went to the site java.com then i downloaded a bin file and it shows instructions on how to install java from the bin fil but i dont get it it it says to open terminal then type in su after that it asks me the password but when i type nothing appears what a nooby problem:(

---

### Post by MelDJ on 2009-12-12
thats normal. when you type the password in terminal, it will be invisible. just continue typing and press enter

---

### Post by phillw on 2009-12-12
> **chillyomi said:**
> i went to the site java.com then i downloaded a bin file and it shows instructions on how to install java from the bin fil but i dont get it it it says to open terminal then type in su after that it asks me the password but when i type nothing appears what a nooby problem:(

Not uncommon - a lot of tutorials say to su -- this is not such a good idea.

before you type any of the commands listed after they say to su, you type in sudo - The 1st time you do it, it will ask you your password. This will stay 'live' for about 10 minutes.

As an example

```
$ su
# apt-get moo

```

Becomes 
```
 $ sudo apt-get moo
```

Don't type in the **$** or **#** !!

By the way, apt-get moo  will not break your system ;-)

Hope that helps you !!

Regards,

Phill.

---

### Post by QIII on 2009-12-12
Hang tight on all of that.  Installing Java on Ubuntu is not as straight forward as all that.  You could install it from the repositories, but since Canonical decided to move to OpenJDK (bad move IMHO), the newest version you can get from the repos is u15, which has some security flaws.

Installing per Sun's instructions will likely not get you the results you want, because it will be difficult to make sure that Sun's Java is used as the default.

Please follow this guy's easy tutorial.

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by chillyomi on 2009-12-13
Thank you very much people :D im still learning havent had anytime to learn all the commands Ubuntu uses

---

