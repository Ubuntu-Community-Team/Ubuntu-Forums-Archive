---
title: "php5-imagick won't install on 7.04-server"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by weboutreach on 2007-10-12
Wierd thing here - I am new to Ubuntu, but very familiar with Debian.

I've just built my first ubuntu box using 7.04-server, and I need to install the imagick extensions for PHP5. It's worth mentioning that my setup here is

Apache2.2
PHP5-CGI
apache2_mod_suphp

So anyway, I found the package and ran:

```
apt-get install php5-imagick
```

Which seemed to work. It added the appropriate line to /etc/php5/cgi/php.ini

PHP doesn't seem to give any errors, but the imagick functions just don't work. For example, this simple script when run...

```
<?php
$img=new Imagick();
?>
```

Gives the error

**[COLOR="Red"]Fatal error: Class 'Imagick' not found in <pathname>/test.php on line 2[/COLOR]**

Anyone any ideas on this? I've used php5-imagick loads of times on things like Fedora and FreeBSD without problems. It's almost like the Class declaration isn't in the extension or something.

Thanks in advance,

Neil S Hamilton

---

### Post by chefweb on 2007-10-12
try this one:

sudo apt-get install imagemagick

and then:

sudo /etc/init.d/apache2 restart

---

### Post by capitol on 2007-10-16
doesn't help

---

### Post by weboutreach on 2007-10-19
No, it doesn't help - I agree.

I tried the following:

```
apt-get install imagemagick
dpkg-reconfigure php5-imagick
/etc/init.d/apache2 restart
```

Still get the same error.

Does anyone know what's going on?

---

### Post by weboutreach on 2007-10-19
I should mention that I ran that logged in as root, rather than using sudo.

---

### Post by inhabit on 2007-10-19
Try adding the line:

```
extension=imagick.so
```

to your php.ini file, probably located under /etc/php5/cgi/ and reloading apache.

---

### Post by weboutreach on 2007-10-19
OK - well since the last post I've upgraded to gutsy since I'm already a day late in doing that :)

That helps (a bit) - at least it's loading the extension now. Incidentally, before it *had* added the relevent extension line to /etc/php5/cgi/php.ini

Now it's done it properly and actually created imagick.ini within /etc/php5/cgi/conf.d which is nice to see.

However, if I try to run something like getimagewidth() on an Imagick object then I get the following error:

```
Fatal error: Uncaught exception 'ImagickException' with message 'Can not process empty wand.' 
```
I should point out that this is code which runs fine on other servers, including Debian-based systems, so I'm very confident it's not the code.

Any more clues?

Thanks,

Neil

---

### Post by inhabit on 2007-10-19
It sounds like a simple problem with not having set register_globals in your php.ini. See if it's set on, and change it if necessary.

I've sometime also run into the problem that PHP doesn't recognize GET variables at all. That was on NetBSD, though, and I have no idea why it did that.

---

### Post by weboutreach on 2007-10-19
The following is set in /etc/php5/cgi/php.ini:

```
register_globals = Off
```

Is that right? I have to say that on every other server where this works fine, it's also set to off. To be honest, I hate the thought of having that set - it's really really nasty!

Thanks,

N

---

### Post by inhabit on 2007-10-19
If it's off on other servers, then changing it shouldn't have effect.

Well, I'm kinda out of ideas..

---

### Post by weboutreach on 2007-10-19
Sadly me two. I reckon it must be a dependancy problem or something, particularly since it's behaviour changed when I upgraded to Gutsy this morning.

I can't help thinking some library must be corrupt, but libmagick etc. seems up to date. So I'm stuck too!

Neil

---

### Post by weboutreach on 2007-10-19
OK - I solved it. I might add this was for 7.10 (Gutsy) rather than 7.04 as the title suggests. The trick is to pretend that ubuntu's php5-imagick package is broken, and do it the old fashioned way using pecl!

I did:

```
sudo apt-get install make php5-dev php-pear
sudo apt-get remove php5-imagick
sudo pecl install imagick
```

You may not need to do this next step if the file already exists, but add the following file called [FONT="Courier New"]/etc/php5/conf.d/imagick.ini[/FONT]

```
# configuration for php imagick module
extension=imagick.so
```

Because I am using apache2_mod_suphp I didn't need to restart Apache, but if you do, just run:

```
sudo /etc/init.d/apache2 restart
```

I hope that works for other people, and helps somebody!

Thanks,

Neil S Hamilton
WebOutreach

---

### Post by daiwai on 2007-10-27
I had the same problem on my gutsy. However when following weboutreach's steps i still got an error from the pecl install:

```
configure: error: Cannot locate configuration program Wand-config
```

The solution was to install *libmagick9-dev* before installing imagick with pecl. Hope this might help others who get the same error.. Thanks everyone for solving this! :)

So basically i did:

```
sudo apt-get install make php5-dev php-pear
sudo apt-get remove php5-imagick
sudo apt-get install libmagick9-dev
sudo pecl install imagick
```

---

### Post by weboutreach on 2007-11-04
Good call daiwai - I'd missed that because I must have left it installed at some point from fiddling! I re-did the same process on a clean server, and still got a the error, and your tip worked a treat.

Thanks for clarifying that for us!

Neil

---

### Post by mr_niceguy on 2008-02-25
Thanks for posting this! Very helpful.

---

### Post by jemmrich on 2008-03-02
Just wanted to say thanks to daiwai, things are working great for me now :)

---

### Post by bobbwhy on 2008-05-31
Hey all.. Well.. Um.. I really appreciate your posts.. Unfortunately.. I tried it all.  

I think i did anyway.. am running Gutsy on amd 64x2... .. 

After doing pecl (hell... after learning what pecl is...) .. the installation looked as though it went well in the command line.. but now php simply does not recognize imagick at all..... not on the test pages and not in phpinfo..  

Hate to bug you on what seemed to be a closed post.. but wondered if anyone had an idea or two ?

Many hours spent on this.. :-(...  appreciate any assistance

thanks

---

