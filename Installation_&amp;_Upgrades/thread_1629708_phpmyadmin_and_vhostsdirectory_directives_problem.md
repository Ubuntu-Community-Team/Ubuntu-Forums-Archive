---
title: "phpmyadmin and vhosts/directory directives problem"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by llebbuhnairb on 2010-11-24
Hoping for a little insight about all of this...

I'm running Ubuntu Server 10.04, Apache2.

I've setup in my sites avail. folder two configs:

```
/etc/apache2/sites-available$ cat com.vesrv.fg8fd5hl.ve 
<VirtualHost *:80>
	ServerName ve.fg8fd5hl.vesrv.com
	DocumentRoot /var/www/com.vesrv.fg8fd5hl.ve
</VirtualHost>
```

```
/etc/apache2/sites-available$ cat ws.wildcard
<VirtualHost *:80>
	ServerName test.wildcard.ws
	DocumentRoot /var/www/ws.wildcard.test
</VirtualHost>
<VirtualHost *:80>
	ServerName wildcard.ws
	ServerAlias *.wildcard.ws
	DocumentRoot /var/www/ws.wildcard
</VirtualHost>
```

they are sym link'd to sites enabled as 0-catch-all and ws.wildcard respectively.

I have installed phpmyadmin and can see that it is intact in usr/share/phpmyadmin

I can also see it's config:

```
cat conf.d/*
# Read the documentation before enabling AddDefaultCharset.
# In general, it is only a good idea if you know that all your files
# have this encoding. It will override any encoding given in the files
# in meta http-equiv or xml encoding tags.

#AddDefaultCharset UTF-8
Alias /javascript /usr/share/javascript/

<Directory "/usr/share/javascript/">
	Options FollowSymLinks MultiViews
</Directory>
#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 http://www.example.com/subscription_info.html
#

#
# Putting this all together, we can internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  If you include the Alias in the global server
# context, is has to come _before_ the 'Alias /error/ ...' line.
#
# The default include files will display your Apache version number and your
# ServerAdmin email address regardless of the setting of ServerSignature.
#
# WARNING: The configuration below will NOT work out of the box if you have a
#          SetHandler directive in a <Location /> context somewhere. Adding
#          the following three lines AFTER the <Location /> context should
#          make it work in most cases:
#          <Location /error/>
#             SetHandler none
#          </Location>
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 37 lines.

#<IfModule mod_negotiation.c>
# <IfModule mod_include.c>
#  <IfModule mod_alias.c>
#
#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var
#  </IfModule>
# </IfModule>
#</IfModule>
# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
	Options FollowSymLinks
	DirectoryIndex index.php

	<IfModule mod_php5.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>

</Directory>

# Authorize for setup
<Directory /usr/share/phpmyadmin/setup>
    <IfModule mod_authn_file.c>
    AuthType Basic
    AuthName "phpMyAdmin Setup"
    AuthUserFile /etc/phpmyadmin/htpasswd.setup
    </IfModule>
    Require valid-user
</Directory>

# Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/libraries>
    Order Deny,Allow
    Deny from All
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
    Order Deny,Allow
    Deny from All
</Directory>

#
# Disable access to the entire file system except for the directories that
# are explicitly allowed later.
#
# This currently breaks the configurations that come with some web application
# Debian packages. It will be made the default for the release after lenny.
#
#<Directory />
#	AllowOverride None
#	Order Deny,Allow
#	Deny from all
#</Directory>


# Changing the following options will not really affect the security of the
# server, but might make attacks slightly more difficult in some cases.

#
# ServerTokens
# This directive configures what you return as the Server HTTP response
# Header. The default is 'Full' which sends information about the OS-Type
# and compiled in modules.
# Set to one of:  Full | OS | Minimal | Minor | Major | Prod
# where Full conveys the most information, and Prod the least.
#
#ServerTokens Minimal
ServerTokens OS
#ServerTokens Full

#
# Optionally add a line containing the server version and virtual host
# name to server-generated pages (internal error documents, FTP directory
# listings, mod_status and mod_info output etc., but not CGI generated
# documents or custom error documents).
# Set to "EMail" to also include a mailto: link to the ServerAdmin.
# Set to one of:  On | Off | EMail
#
#ServerSignature Off
ServerSignature On

#
# Allow TRACE method
#
# Set to "extended" to also reflect the request body (only for testing and
# diagnostic purposes).
#
# Set to one of:  On | Off | extended
#
TraceEnable Off
#TraceEnable On
```

For whatever reason, perhaps my misunderstanding of how the directory directives hsould work, i can't seem to get ot phpmyadmin. I'm honestly not sure what domain it should show for, both?

Any help on this is welcome.

---

### Post by dgoosens on 2010-11-24
have you configured your /etc/hosts properly ?

---

### Post by llebbuhnairb on 2010-11-24
> **dgoosens said:**
> have you configured your /etc/hosts properly ?

Not sure how this applies here, excuse me if I'm misunderstanding, but I thought the proper use of /etc/hosts was to associate a domain with an ip address. Examples where I've used this:

- setting a domain to be hosted locally: 127.0.0.1 sandbox
- before dns propagates: 192.0.32.10 example.com

The domain(s) in question here both have dns records set.

---

### Post by efflandt on 2010-11-24
Did you symlink the apache2 config for phpmyadmin to apache's sites-enabled directory?  Installation of phpmyadmin did not do that for me, even though it said it was going to configure apache2.  Otherwise apache2 may be totally unaware of phpmyadmin virtual host.

But I do not have all of that installed right now, so cannot provide details.  But there is likely something under /etc/phpmyadmin.

---

### Post by llebbuhnairb on 2010-11-24
> **efflandt said:**
> Did you symlink the apache2 config for phpmyadmin to apache's sites-enabled directory?  Installation of phpmyadmin did not do that for me, even though it said it was going to configure apache2.  Otherwise apache2 may be totally unaware of phpmyadmin virtual host.

But I do not have all of that installed right now, so cannot provide details.  But there is likely something under /etc/phpmyadmin.

From what I can see, anything under conf.d gets imported into the config, including the symlink that is there:

```
/etc/apache2/conf.d$ ls -l
total 12
-rw-r--r-- 1 root root  269 Sep 28 05:52 charset
lrwxrwxrwx 1 root root   45 Nov 23 21:29 javascript-common.conf -> /etc/javascript-common/javascript-common.conf
-rw-r--r-- 1 root root 3296 Sep 28 05:52 localized-error-pages
lrwxrwxrwx 1 root root   28 Nov 23 21:35 phpmyadmin.conf -> ../../phpmyadmin/apache.conf
-rw-r--r-- 1 root root 1481 Sep 28 05:52 security
```

```
/etc/apache2/conf.d$ cat ../../phpmyadmin/apache.conf
# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
	Options FollowSymLinks
	DirectoryIndex index.php

	<IfModule mod_php5.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>

</Directory>

# Authorize for setup
<Directory /usr/share/phpmyadmin/setup>
    <IfModule mod_authn_file.c>
    AuthType Basic
    AuthName "phpMyAdmin Setup"
    AuthUserFile /etc/phpmyadmin/htpasswd.setup
    </IfModule>
    Require valid-user
</Directory>

# Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/libraries>
    Order Deny,Allow
    Deny from All
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
    Order Deny,Allow
    Deny from All
</Directory>
```

---

### Post by llebbuhnairb on 2010-11-25
RESOLVED

I was able to get this to work by simply adding:

```
Alias /phpmyadmin /usr/share/phpmyadmin
```

within the virtual host for the domain at which I want to get to it using.

To anyone knowledgable on the subject, I'd love a better understanding as to how/why this works.

---

