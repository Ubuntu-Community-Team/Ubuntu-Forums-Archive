---
title: "add mysql support to php when installed from source"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by kritro on 2008-11-22
Hello
I have installed apache and php from source because I needed to compile it together with oracle instant client.

After that I installed MySQL server via apt-get. Mysql is working but php is not supporting it.

Its nothing in phpinfo() about mysql.

I was able to add /usr/lib/php5/20060613+lfs/ to the extension path, but that didn't to anything. This folder contains the mysql.so and other so files.

My apache location is /usr/local/apache and the php.ini file is in /usr/local/apache/conf/php.ini

I notice that no extra ini files are parsed as in another working installation I have. Maybe this is the problem?

[IMG]http://www.tekit.no/phpinfo.png[/IMG]

Anyone who can push me in the right direction?

---

### Post by kritro on 2008-11-22
I just added the extentions to the php.ini files and it worked.

---

