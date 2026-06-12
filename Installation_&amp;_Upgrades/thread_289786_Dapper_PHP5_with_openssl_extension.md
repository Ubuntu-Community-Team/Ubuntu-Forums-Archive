---
title: "Dapper: PHP5 with openssl extension"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by nrasmus on 2006-10-31
Hello,

Apologies if this is in the wrong forum, or I missed the answer elswhere.

I plan to migrate a breezy LAMP server to a new box running Dapper.  

For most of the setup, I am following: [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4)

I would like the PHP5 to include support for openssl (not in apache, but so PHP can scripts can act as an ssl client--eg PHPmailer).  I've done a fair amount of searching, but am unaware if this is possible with apt.  Do I need to compile my own PHP5?  

Secondarily, I'd like bzip supported in PHP too, but that's more of a minor issue.

---

### Post by nrasmus on 2006-10-31
OK--

Thanks to this thread:
[http://ubuntuforums.org/showthread.php?t=269885](http://ubuntuforums.org/showthread.php?t=269885)

I just downloaded the php5-src, and the debian/rules seems to indicate that --with-openssl=/usr \ (and --with-bz2 \), so I guess the php5 package does install these by default?  That wasn't the case with php4, AFAIK.  Anyway, I'll go ahead with apt and see what .so modules show up in /usr/lib/php5/*dir*/

---

### Post by nrasmus on 2006-10-31
I'm new to these forums--if there's a way to edit your own posts, sorry.

apt-get install did not seem to create the module in /usr/lib/php5/20051025 for openssl.  Now I am stuck.  Can anyone help?

Thanks.

---

