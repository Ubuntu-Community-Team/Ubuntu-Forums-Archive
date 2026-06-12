---
title: "apt-get install squirrelmail?"
date: 2005-07-05
forum: Installation &amp; Upgrades
---

### Post by greystreet on 2005-07-05
Ok this is going to sound really dumb but here it goes.  I have built dovecot, postfix, apache2, php4 and now I am trying to setup squirrelmail.  For some reason though apt-get install squirrelmail can not find squirrelmail.  I am very green to using apt-get and do not know how to search the reprository of packages available.  So I am guessing I am requesting a package that does not exist.  Any help would be great!

Grey

---

### Post by bored2k on 2005-07-05
> $ apt-cache show squirrelmail

**Description: Webmail for nuts**
 SquirrelMail is a standards-based webmail package written in PHP4. It
 includes built-in pure PHP support for the IMAP and SMTP protocols, and
 all pages render in pure HTML 4.0 (with no Javascript) for maximum
 compatibility across browsers. It has very few requirements and is very
 easy to configure and install. SquirrelMail has all the functionality
 you would want from an email client, including strong MIME support,
 address books, and folder manipulation.

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

