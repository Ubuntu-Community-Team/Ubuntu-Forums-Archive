---
title: "PHP not working with Apache2"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by slowboy on 2006-12-21
I am having a related problem to this post.  I have damaged my apache2, php4, Ubuntu hoary server by attempting to update to PHP5 without being smart enough.  At this point I have apache2 back up and running, but PHP is not working correctly.  When I try to load the test page "http://localhost/info.php" it prompts me to save the file. So I believe my problem is that the PHP module is not loaded in apache2.

The easiest solution seems to be to run

[INDENT]# apt-get install libapache2-mod-php4
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libapache2-mod-php4: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu15 is to be installed
E: Broken packages[/INDENT]

I get this error here and the module will not install.  I get the same error when attemping with PHP5.

So my next attempt was to load the modules directly so I added the aliases using the following commands:

[INDENT]# ln -s /etc/apache2/mods-available/php4.load /etc/apache2/mods-enabled/php4.load
# ln -s /etc/apache2/mods-available/php4.conf /etc/apache2/mods-enabled/php4.conf[/INDENT]

then I reload the apache2 and get the following:

[INDENT]>/etc/init.d/apache2 restart
 * Forcing reload of web server  (Apache2)...
Syntax error on line 1 of /etc/apache2/mods-enabled/php5.0.load:
Cannot load /usr/lib/apache2/modules/libphp4.so into server: /usr/lib/apache2/mo *les/libphp4.so: undefined symbol: ap_block_alarms                      [fail][/INDENT]

So I guess my question at this point is how to I get the 
[INDENT]libapache2-mod-php4: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu15[/INDENT]fixed so that i can use the
[INDENT]apt-get install libapache2-mod-php4[/INDENT]
to get my php4 working again!?

Thanks !

Matt

---

### Post by az on 2006-12-21
> **slowboy said:**
> 
The following packages have unmet dependencies:
  libapache2-mod-php4: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu15 is to be installed
E: Broken packages

You mixed Debian and Ubuntu sources.

Remove all Debian sources in you sources.list and then dist upgrade.

Try again.  If you have actually installed a version of libc6 from Debian, you will have to downgrade it or do some other funky magic line dist-upgradeing to a later release of Ubuntu.

---

