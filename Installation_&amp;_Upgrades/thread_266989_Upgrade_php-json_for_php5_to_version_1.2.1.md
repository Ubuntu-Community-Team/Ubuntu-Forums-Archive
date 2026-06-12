---
title: "Upgrade php-json for php5 to version 1.2.1"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by orengabay on 2006-09-28
Hi all,
I want to upgrade php-json to version 1.1.* or later for sugarcrm support but I can't find how to do that. I found a SRPM package I don't know how to install and I do not find it using synaptic.
Any hint will help.

Thanks,
Oren

---

### Post by Jussi Kukkonen on 2006-09-28
1.1.0 is in Dapper, so I'm guessing you want 1.2.X?

Edgy has 1.2.1, you might want to try installing that from .debs ([http://packages.ubuntu.com/](http://packages.ubuntu.com/)) or upgrading to Edgy. Neither is an especially good solution for a production server.

---

### Post by orengabay on 2006-09-28
Thank you, I installed the Edgy version on my development machine and it looks fine now.

---

### Post by Jimbo MF on 2006-10-05
On a related note Sugar CRM requires php5-json 1.1.1 (later versions do not work at this time)
I have found this on the net and am having some trouble installing it.
using ./configure Get the following message :
*configure: error: Cannot find php-config. Please use --with-php-config=PATH*

So I used ./cofigure --with-php-config=/etc/php5/apache2/php.ini

and i get the following error: 
[I]/etc/php5/apache2/php.ini: line 1: [PHP]: command not found
/etc/php5/apache2/php.ini: line 3: syntax error near unexpected token `;;'
/etc/php5/apache2/php.ini: line 3: `;;;;;;;;;;;'
configure: error: Cannot find php-config. Please use --with-php-config=PATH[/I]

Anyone had some susess or Ideas on how to point me in the right direction.

Thanks in advance.
James

---

### Post by kamermans on 2006-10-30
I just had that same error, it's not asking for the config file, it's asking for the "php-config" utility included with the php-dev package.  I'm using php4, but this should work on either:

apt-get install php5-dev # (or php4-dev)

now you should be able to do this:

which php-tools

If you see something like "/usr/bin/php-tools" you are good to go.

[http://www.teratechnologies.net/](http://www.teratechnologies.net/)

---

