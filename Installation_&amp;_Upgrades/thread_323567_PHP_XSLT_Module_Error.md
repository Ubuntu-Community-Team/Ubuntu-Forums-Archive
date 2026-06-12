---
title: "PHP XSLT Module Error"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by smakonin on 2006-12-22
I have installed the php5-xsl package using:

aptitude install php5-xsl

I have restarted and rebooted my server. PHP Info shows:

PHP Version 5.1.2
System	Linux icarus 2.6.15-23-powerpc #1 Tue May 23 13:46:54 UTC 2006 ppc

xsl

XSL	enabled
libxslt Version	1.1.15
libxslt compiled against libxml Version	2.6.22
EXSLT	enabled
libexslt Version	1.1.15

But I am still getting this error:

Fatal error: Call to undefined function xslt_create()

Am I missing something?

My INI file (/etc/php5/apache2/php.ini) has this at the bottom:

extension=xsl.so


Can anyone help me? 

Thanks,
Stephen.

---

### Post by spii on 2007-03-23
I have this same situation. It's a shame this post wasn't answered... I'll have to keep hunting :]

---

### Post by Pinkydead on 2007-05-16
This seems to be common problem.

I found a reference that suggests that the XSLT functions aren't supported in PHP 5.

On the page for 'XSL functions' there is wrapper that emulates the older functions - it's a crappy solution, but it works.

I'd love to see a better solution...

---

### Post by Pinkydead on 2007-05-17
..to add just a little more to that.

After using that wrapper it seemed kind of stupid not to just use the XSLTProcessor class directly - based on the code in the wrapper.

It's actually quite straightforward, though not a simple as the original functions.

I think that's probably the better solution.

---

