---
title: "Problem with Twiki after upgrade"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by joel@parke.ods.org on 2008-11-04
Hi,

After the upgrade, I have a problem with apache2 which is setup up to use Twiki.  My home page is [http://parke.ods.org/twiki/bin/view.pl](http://parke.ods.org/twiki/bin/view.pl) which displays:

>>Internal Server Error
>>
>>The server encountered an internal error or misconfiguration and was unable to complete your request.
>>
>>Please contact the server administrator, >>[email]joel@parke.ods.org[/email] and inform them of the time the error >>occurred, and anything you might have done that may have caused the error.
>>
>>More information about this error may be available in the server error log.
>>Apache/2.2.9 (Ubuntu) DAV/2 SVN/1.5.1 PHP/5.2.6-2ubuntu4 with >>Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_ssl/2.2.9 OpenSSL/0.9.8g >>mod_perl/2.0.4 Perl/v5.10.0 Server at parke.ods.org Port 80

The Sever log then shows the following errors:

[Tue Nov 04 00:54:08 2008] [error] [client 192.168.1.1] Can't locate CGI/Session.pm in @INC (@INC contains: /var/twiki/lib/CPAN/lib//arch/ /var/twiki/lib/CPAN/lib//5.10.0/x86_64-linux-gnu-thread-multi/ /var/twiki/lib/CPA$
[Tue Nov 04 00:54:08 2008] [error] [client 192.168.1.1] BEGIN failed--compilation aborted at (eval 12) line 1.
[Tue Nov 04 00:54:08 2008] [error] [client 192.168.1.1] Premature end of script headers: view.pl

*** This looks like one of my dependencies has been clobbered, but I am not sure where to look exactly.  SO if you know twiki, could you point out what to fix?

Thanks,
Joel Parke

---

### Post by pmacaodh on 2009-11-12
I also have a problem after upgrade - mod_auth_pam.so is missing, so apache2 can't start without PAM and therefore twiki, in it's existing configuration is unavailable.

To solve, I'm going down the route of getting back mod_auth_pam.so, but if there is a better solution, I'd love to hear it, because it's not plain sailing (for me).

So, here's what happens:

[FONT=System][COLOR=Gray]apache2ctl start
apache2: Syntax error on line 203 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/auth_pam.load: Cannot load /usr/lib/apache2/modules/mod_auth_pam.so into server: /usr/lib/apache2/modules/mod_auth_pam.so: cannot open shared object file: No such file or directory[/COLOR]
[/FONT] 
libapache2-mod-auth-pam is no longer supported in karmic apparently, so I couldn't install from package manager.  So, I went to sourceforge and got the mod_auth_pam tarball to compile, but on make, it can't find securtiy/pam_appl.h...

I persevere...

---

### Post by pmacaodh on 2009-11-12
Ah, headers are not installed.  libpam0g provided the headers required...  Installed and compiled ('make' and 'make install').  Now, TWiki is back online for me.

---

