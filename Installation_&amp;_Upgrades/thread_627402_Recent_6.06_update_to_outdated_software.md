---
title: "Recent 6.06 update to outdated software"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by -IGI- on 2007-11-30
Today I got update for PHP to version 5.1.2... that's almost 2 years old version.
I can understand if it was last stable version in that branch but there is 5.1.6 which has zillion bug fixes and is not new too (1.5+ years old). Not even mentioning fresh release of 5.2.5.
Is this normal ? Such updates look silly to me.

And will apache be updated to 2.2.x in this century ?

---

### Post by -IGI- on 2008-01-22
Why the hell PHP5 still at 5.1.2 ? :confused: That's just ridiculous !!!
Please, update it atleast to 5.1.4 so we can use Zend framework.
And just curious - will dapper still use 6.15 kernel in 2011? What the point ? I am using 18.8 and it runs like a charm and support much more devices.
Yes, I can update packages myself from sources but if I have to keep track and update manually all required software what the job of support team ? I am not talking about rare software but main packages that installed almost on every linux box.
Support means keep software up to date, not apply several security patches only.
6.06 support sucks unfortunately :(

---

### Post by ddrplayer512 on 2008-01-22
Remember, you are using Dapper, the Long Term Support. They use old, but tested software. If you don't like the outdated software, try the latest release, in this case 7.10. They have a lot new features over Dapper. ;)

---

### Post by -IGI- on 2008-01-22
That's the problem - php 5.1.2 cannot be called stable because it has a lot of internal software bugs fixed in versions up to 5.1.6. I mean - stability is not just a security.
I choosed LTS version just because I don't want to reinstall my server very often. 7.10 will die in 11 monthes that means reinstall server twice this year (now and in the end of year). Don't like this idea at all :(
If support will work a bit it can be avoided.

---

### Post by az on 2008-01-22
> **-IGI- said:**
> That's the problem - php 5.1.2 cannot be called stable because it has a lot of internal software bugs fixed in versions up to 5.1.6. I mean - stability is not just a security.
I choosed LTS version just because I don't want to reinstall my server very often. 7.10 will die in 11 monthes that means reinstall server twice this year (now and in the end of year). Don't like this idea at all :(
If support will work a bit it can be avoided.

The problem is that when you add features, you also introduce the chance to break things.  This is why there is a difference between a production server and a development server.

Patches get applied to PHP5 in Dapper without the version increasing.  But when a bug is found that cannot be patched, the version number will increase.  That means that the version you download may contain fixes that are in later versions.

If your needs are such that you need to run a development server, don't use Dapper; it's as simple as that.

---

### Post by PmDematagoda on 2008-01-22
> **-IGI- said:**
> Why the hell PHP5 still at 5.1.2 ? :confused: That's just ridiculous !!!
Please, update it atleast to 5.1.4 so we can use Zend framework.
And just curious - will dapper still use 6.15 kernel in 2011? What the point ? I am using 18.8 and it runs like a charm and support much more devices.
Yes, I can update packages myself from sources but if I have to keep track and update manually all required software what the job of support team ? I am not talking about rare software but main packages that installed almost on every linux box.
Support means keep software up to date, not apply several security patches only.
6.06 support sucks unfortunately :(

If you believe that Ubuntu 6.06 lacks support, then Red Hat Enterprise Linux 5 must be even worse, let me give a few examples of the packages it uses:-
linux kernel 2.6.18
xorg 1.1.1
firefox 1.5.0.12

so considering that, Red Hat support should be very much worse than Ubuntu 6.06, but this is not true since Red Hat Enterprise 5 is very stable and receives very good support.

So +1 on az's comment, I would have said the same thing:).

---

