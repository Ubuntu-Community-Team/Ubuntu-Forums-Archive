---
title: "PHPMotion &amp; phpSHIELD"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by abasel on 2008-08-22
I'm trying to install PHPMotion.

I think I've managed to install all the right components.

Documentation on the sight isn't too great so I'm not sure what permissions to set where.

How do I fix the following error:

Warning: dl() [function.dl]: Dynamically loaded extensions aren't enabled in /var/www/PHPMOTION/classes/config.php on line 2
PHP script /var/www/PHPMOTION/classes/config.php is protected by phpSHIELD and requires the phpSHIELD loader phpshield.5.2.lin. The phpSHIELD loader has not been installed, or is not installed correctly. Please visit the phpSHIELD php encoder site to download required loader.

Just found installation instructions :-)

Will keep you posted

---

### Post by abasel on 2008-08-24
Ok.. all appeared to work until I tried uploading a file. I then get the following:
```
Not Found

The requested URL /cgi-bin/audio/uu_upload.pl was not found on this server.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch Server at vserver.rosminicollege.school.nz Port 80
```

If I go to /var/www, I can see the cgi-bin folder. The permissions on the folder and files are 755 ... the uu_upload.pl file is there

How do I fix this?

---

### Post by mysoogal on 2009-05-03
copy all the CGI files into here /usr/lib/cgi-bin

in your vhost conf its set to /usr/lib/cgi-bin not in /var/www/cgi-bin

same thing with ostube cgi folder, just put all ur cgi files into /usr/lib/cgi-bin

and restart web server.

---

### Post by jk.cheng on 2010-03-31
how about if users on the shared hosting... the hosting is for sure ubuntu... but how user gonna setup it...

---

### Post by bouwerik on 2010-04-08
Any idea how to get phpmotion started on ubuntu 10.04 - 64bit, latest version of phpmotion, ixed.5.3.lin is installed and recognized by php (shown in phpinfo). I get the following error: Fatal error: SourceGuardian Loader - This protected script does not support version 5.3.2-1ubu of PHP.

Any way to get this working?

Cheers

---

