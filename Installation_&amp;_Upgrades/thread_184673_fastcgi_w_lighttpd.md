---
title: "fastcgi w/ lighttpd"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by viniosity on 2006-05-30
I have lighttpd set up and running on my dapper box but the minute I add mod_fastcgi to my server.modules lighttpd fails to load.  The error log is no help so the only thing I can figure is that maybe lightty does not come compiled with fastcgi access by default?

Anyone have any ideas for me to try?

---

### Post by t3r0 on 2006-05-30
Hi,

Do you get any error messages to console if you start lighty manually with:
```

lighttpd -f /path/to/your_config_file

```
?? 

And did you make any other changes to your default conf file(s)?


-Tero

Edit: 

If I remember right Ubuntus default lighty conf is split into multiple files, and fastcgi is loaded by default in other conf file, "mods-enabled.conf" or something similar... 
So maby you are loading the module twice??

---

### Post by viniosity on 2006-05-30
I probably made lots of changes to my config file.. in fact I'm using one from a debian server setup that works.  In any case, typing the full command shows these errors:

```

viniosity@seashell:/var/www/buyindie/public# 2006-05-30 11:12:02: (mod_fastcgi.c.1022) execve failed for: /var/www/buyindie/public/dispatch.fcgi No such file or directory 
2006-05-30 11:12:02: (mod_fastcgi.c.1048) the fastcgi-backend /var/www/buyindie/public/dispatch.fcgi failed to start: 
2006-05-30 11:12:02: (mod_fastcgi.c.1052) child exited with status 2 /var/www/buyindie/public/dispatch.fcgi 
2006-05-30 11:12:02: (mod_fastcgi.c.1055) if you try do run PHP as FastCGI backend make sure you use the FastCGI enabled version.
You can find out if it is the right one by executing 'php -v' and it should display '(cgi-fcgi)' in the output, NOT (cgi) NOR (cli)
For more information check http://www.lighttpd.net/documentation/fastcgi.html#preparing-php-as-a-fastcgi-program 
2006-05-30 11:12:02: (mod_fastcgi.c.1060) If this is PHP on Gentoo add fastcgi to the USE flags 
2006-05-30 11:12:02: (mod_fastcgi.c.1356) [ERROR]: spawning fcgi failed. 
2006-05-30 11:12:02: (server.c.834) Configuration of plugins failed. Going down.

```

This is a rails app so I don't think the PHP errors are valid.  Also I actually do have the directory in question:

```

viniosity@seashell:/var/www/buyindie/public# ls -al
total 52
drwxr-xr-x  6 root     www-data 4096 2006-05-30 08:48 .
drwxr-xr-x 15 root     www-data 4096 2006-05-30 08:16 ..
-rwxr-xr-x  1 www-data www-data  235 2006-04-07 13:34 404.html
-rwxr-xr-x  1 www-data www-data  318 2006-04-07 13:34 500.html
-rwxr-xr-x  1 www-data www-data  482 2006-04-07 13:34 dispatch.cgi
-rwxr-xr-x  1 www-data www-data  864 2006-04-07 13:34 dispatch.fcgi
-rwxr-xr-x  1 www-data www-data  482 2006-04-07 13:34 dispatch.rb
-rwxr-xr-x  1 www-data www-data    0 2006-04-07 13:34 favicon.ico
-rw-r--r--  1 root     www-data 1250 2006-04-07 13:34 .htaccess
drwxr-xr-x  2 www-data www-data 4096 2006-05-30 15:47 images
drwxr-xr-x  2 www-data www-data 4096 2006-04-10 14:51 javascripts
-rwxr-xr-x  1 www-data www-data   99 2006-04-07 13:34 robots.txt
drwxr-xr-x  3 www-data www-data 4096 2006-05-11 15:32 store
drwxr-xr-x  2 www-data www-data 4096 2006-05-25 10:23 stylesheets

```

---

### Post by t3r0 on 2006-05-30
hmm... 

It might be permission problem.,, Try 
```

# chmod ug+rwx  /var/www/buyindie/public/dispatch.fcgi
# chown -R www-data:www-data /var/www/buyindie

```

Also check that www-data user has permissions to write the fcgi socket defined in your conf file... (/tmp/ ?? )


If no luck, post your conf file here... 



- Tero

---

### Post by viniosity on 2006-05-30
I don't think it's a permissions issue. I chowned /tmp to www-data:www-data but still got the same error.  Here's my lighttpd.conf.  Any other conf files I can provide? (fast_cgi is commented out b/c I used the lightty enable script to handle it)

```

# Debian lighttpd configuration file
# 

############ Options you really have to take care of ####################

## modules to load
# mod_access, mod_accesslog and mod_alias are loaded by default
# all other module should only be loaded if neccesary
# - saves some time
# - saves memory

server.modules              = ( 
            "mod_access",
            "mod_alias",
            "mod_accesslog",
           "mod_rewrite", 
#           "mod_fastcgi",
       	"mod_redirect", 
#           "mod_status", 
#           "mod_evhost",
           "mod_compress",
#           "mod_usertrack",
#           "mod_rrdtool",
#           "mod_webdav",
#           "mod_expire",
#           "mod_flv_streaming",
#           "mod_evasive"
 )

## a static document-root, for virtual-hosting take look at the 
## server.virtual-* options
server.document-root       = "/var/www/"

## where to send error-messages to
server.errorlog            = "/var/log/lighttpd/error.log"

## files to check for if .../ is requested
index-file.names           = ( "index.php", "index.html", 
                               "index.htm", "default.htm" )


## Use the "Content-Type" extended attribute to obtain mime type if possible
# mimetype.use-xattr = "enable"

#### accesslog module
accesslog.filename         = "/var/log/lighttpd/access.log"

## deny access the file-extensions
#
# ~    is for backupfiles from vi, emacs, joe, ...
# .inc is often used for code includes which should in general not be part
#      of the document-root
url.access-deny            = ( "~", ".inc" )



######### Options that are good to be but not neccesary to be changed #######

## bind to port (default: 80)
#server.port               = 81

## bind to localhost only (default: all interfaces)
#server.bind                = "localhost"

## error-handler for status 404
#server.error-handler-404  = "/error-handler.html"
#server.error-handler-404  = "/error-handler.php"

## to help the rc.scripts
server.pid-file            = "/var/run/lighttpd.pid"

## 
## Format: <errorfile-prefix><status>.html
## -> ..../status-404.html for 'File not found'
#server.errorfile-prefix    = "/var/www/"

## virtual directory listings
dir-listing.encoding        = "utf-8"
server.dir-listing          = "enable"

## send unhandled HTTP-header headers to error-log
#debug.dump-unknown-headers  = "enable"

### only root can use these options
#
# chroot() to directory (default: no chroot() )
#server.chroot            = "/"

## change uid to <uid> (default: don't care)
server.username            = "www-data"

## change uid to <uid> (default: don't care)
server.groupname           = "www-data"

#### compress module
#compress.cache-dir          = "/var/tmp/lighttpd/cache/compress/"
#compress.filetype           = ("text/plain", "text/html")

#### status module
# status.status-url = "/server-status"
# status.config-url = "/server-config"

#### url handling modules (rewrite, redirect, access)
# url.rewrite                 = ( "^/$"             => "/server-status" )
# url.redirect                = ( "^/wishlist/(.+)" => "http://www.123.org/$1" )

#
# define a pattern for the host url finding
# %% => % sign
# %0 => domain name + tld
# %1 => tld
# %2 => domain name without tld
# %3 => subdomain 1 name
# %4 => subdomain 2 name
#
# evhost.path-pattern = "/home/storage/dev/www/%3/htdocs/"

#### expire module
# expire.url                  = ( "/buggy/" => "access 2 hours", "/asdhas/" => "access plus 1 seconds 2 minutes")

#### rrdtool
# rrdtool.binary = "/usr/bin/rrdtool"
# rrdtool.db-name = "/var/www/lighttpd.rrd"

## this is a hack
alias.url = ("___invalid___" => "___invalid___")

#### handle Debian Policy Manual, Section 11.5. urls
#### and by default allow them only from localhost

#$HTTP["host"] == "localhost" {
#	global {
#		alias.url += ( 
#			"/doc/" => "/usr/share/doc/",
#			"/images/" => "/usr/share/images/"
#		)
#	}
#	dir-listing.activate = "enable"
#}


$HTTP["host"] == "buydev.foo.com" {
server.document-root = "/var/www/buyindie/public/"
server.error-handler-404 = "/dispatch.fcgi"
server.indexfiles = ("dispatch.fcgi")
  fastcgi.server = (".fcgi" =>
    ("localhost" =>
       ("socket" => "/tmp/buyindie.socket",
                    "min-procs" => 2,
                    "max-procs" => 2,
       "bin-path" =>"/var/www/buyindie/public/dispatch.fcgi",
       "bin-environment" => ("RAILS_ENV" => "development")
  )))
}


#### variable usage:
## variable name without "." is auto prefixed by "var." and becomes "var.bar"
#bar = 1
#var.mystring = "foo"

## integer add
#bar += 1
## string concat, with integer cast as string, result: "www.foo1.com"
#server.name = "www." + mystring + var.bar + ".com"
## array merge
#index-file.names = (foo + ".php") + index-file.names
#index-file.names += (foo + ".php")


#### external configuration files
## mimetype mapping
include_shell "/usr/share/lighttpd/create-mime.assign.pl"

## load enabled configuration files, 
## read /etc/lighttpd/conf-available/README first
include_shell "/usr/share/lighttpd/include-conf-enabled.pl"


```

---

### Post by Paerez on 2006-05-30
Instead of adding it in, I ran:

$ sudo lighty-enable-mod fastcgi

Since the ubuntu set-up of Lighttpd creates links to supplements of the conf file based on this command. Fastcgi is working for me this way.

good luck

---

### Post by viniosity on 2006-06-01
Ok, there were lots of problems with my install (missing libmysql-ruby for one) but at the end of the day the problem with lighttpd was that by dispatch.fcgi file contained a pointer to ruby on a windows machine (where the app was developed).  Changing the first line of that dispatch.fcgi to #!/usr/bin/ruby fixed my problem.

Hope this helps somebody else..

---

