---
title: "Apache and mod_perl"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by Margate on 2006-12-18
Hi,
I trying to get mod_perl running on Apache2 on Ubuntu 6.10 and most stuff is working, however am not able to use request object or any other mod_perl object from within my default folder /var/www/pp.

I tried this example from perl.Apache.org

```
my $r = shift;
$r->send_http_header('text/plain');
$r->print("mod_perl rules!\n");

```
In apache error.log i get this 

[Mon Dec 18 09:05:14 2006] [error] [client 127.0.0.1] Premature end of script headers: Test3.pl

this is because the header newer is written, so I forced at header by doing

```

print "Content-type: text/html\n\n";
my $r = shift;
$r->send_http_header('text/plain');
$r->print("mod_perl rules!\n");

```

In apache error.log i get this 

[Mon Dec 18 09:08:53 2006] [error] [client 127.0.0.1] Can't call method "send_http_header" on an undefined value at /var/www/pp/Test3.pl line 4.

I believe the undefined value is $r

I tried to do the print_env1 handle example and work as expected

PrintEnv1.pm (i placed this file in /usr/lib/perl5/Apache2 with all other pm files)
```

package Apache2::PrintEnv1;

#use strict;
use warnings;

use Apache2::RequestRec ( ); # for $r->content_type

use Apache2::Const -compile => 'OK';

sub handler {
    my $r = shift;

    $r->content_type('text/plain');
    for (sort keys %ENV){
        print "$_ => $ENV{$_}\n";
    }

    return Apache2::OK;
}
1;


```

Entry in sites-enabled file
```

NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                # RedirectMatch ^/$ /apache2-default/
                RedirectMatch ^/$ /pp/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

        Alias /doc/ "/usr/share/doc/"
        <Directory "/usr/share/doc/">
                Options Indexes MultiViews FollowSymLinks
                AllowOverride None
                Order deny,allow
                Deny from all
                Allow from 127.0.0.0/255.0.0.0 ::1/128
        </Directory>

        # Perl
        PerlModule ModPerl::Registry
        Alias /perl/ /var/www/pp/
        PerlPostConfigRequire /usr/lib/apache2/startup.pl
        <Location /perl/>
                SetHandler perl-script
                PerlResponseHandler ModPerl::Registry
                PerlOptions +ParseHeaders
                Options +ExecCGI +Includes
        </Location>
        PerlModule Apache2::PrintEnv1
        <Location /print_env1>
            SetHandler perl-script
            PerlResponseHandler Apache2::PrintEnv1
        </Location>

```

Output from [http://localhost/print_env1](http://localhost/print_env1)
```

DOCUMENT_ROOT => /var/www
GATEWAY_INTERFACE => CGI/1.1
HTTP_ACCEPT => text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
HTTP_ACCEPT_CHARSET => ISO-8859-1,utf-8;q=0.7,*;q=0.7
HTTP_ACCEPT_ENCODING => gzip,deflate
HTTP_ACCEPT_LANGUAGE => en-us,en;q=0.5
HTTP_CONNECTION => keep-alive
HTTP_HOST => localhost
HTTP_KEEP_ALIVE => 300
HTTP_USER_AGENT => Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1) Gecko/20060601 Firefox/2.0 (Ubuntu-edgy)
MOD_PERL => mod_perl/2.0.2
MOD_PERL_API_VERSION => 2
PATH => /usr/local/bin:/usr/bin:/bin
QUERY_STRING => 
REMOTE_ADDR => 127.0.0.1
REMOTE_PORT => 35690
REQUEST_METHOD => GET
REQUEST_URI => /print_env1
SCRIPT_FILENAME => /var/www/print_env1
SCRIPT_NAME => /print_env1
SERVER_ADDR => 127.0.0.1
SERVER_ADMIN => webmaster@localhost
SERVER_NAME => localhost
SERVER_PORT => 80
SERVER_PROTOCOL => HTTP/1.1
SERVER_SIGNATURE => <address>Apache/2.0.55 (Ubuntu) PHP/5.1.6 mod_perl/2.0.2 Perl/v5.8.8 Server at localhost Port 80</address>
SERVER_SOFTWARE => Apache/2.0.55 (Ubuntu) PHP/5.1.6 mod_perl/2.0.2 Perl/v5.8.8

```

In my /var/www/pp folder i placed an index.pl there printout %ENV 

```

#!/usr/bin/perl
use strict;
print "Content-type: text/html\n\n";

print "<html><head><title>test af perl</title></head><body>";
print "<table>";
foreach my $key (sort keys %ENV)
{
print "<tr><td>$key</td><td>$ENV{$key}</td></tr>";
}
print "</table>";

```

Can anyone help or explain to my why I can't reference $r in my /var/www/pp folder, as i see it, I can reference $r if used in a handler

Regards Margate

---

### Post by balbir97 on 2007-02-26
me too trying to configure mod_perl.
but still no luck!!

---

### Post by wwwebster on 2007-03-11
Just in case you haven't seen this [from the forum archives]

[INDENT][http://ubuntuforums.org/showthread.php?t=16578](http://ubuntuforums.org/showthread.php?t=16578)[/INDENT]

Hope this helps.

---

