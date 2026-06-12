---
title: "Just wanting a Mambo server"
date: 2005-11-11
forum: Installation &amp; Upgrades
---

### Post by Johnny Canuck on 2005-11-11
Hello, 

A friend recommended that I download Ubuntu in order to get myself a server running that's got:

- Apache
- MySQL
- PHP

My Linux experience is close to nada, and all I really want to do is to configure the Mambo (now Joomla) server. The rest is just 'prerequisite'.

I'm wondering if Ubuntu is the right O/S, as when I tried the Apache, it wasn't there, and when I downloaded it from the Internet, apparently there wasn't a 'C' compiler to compile it.

So, I'm looking for a dog simple O/S install (onto a VM host) so I can play with a Joomla server.

Any ideas?

(In the meantime, Ubuntu looks really nice. I just wish the pre-requisites were already running.)

---

### Post by oborysm on 2005-11-11
Ubuntu should work fine. I believe the easiest way to add Apache/php/MySQL is by installing xampp ([http://www.apachefriends.org/en/xampp.html)](http://www.apachefriends.org/en/xampp.html)). 

You can probably install xammp from within Ubuntu using either Synaptic or apt-get. I haven't tried this on Ubuntu, so you're on your own for details :-)

---

### Post by Johnny Canuck on 2005-11-11
Much thanks. I'll have a look at that.

---

### Post by wrtrdood on 2005-11-11
I'm running a fully loaded Ubuntu based server at unixshell.com (vhost).  It works like a charm and has been reliable.  Though a bit involved, installing Apache, PHP, MySQL and Joomla is not at all difficult.  A good guide can be found at
 [http://www.ubuntuforums.org/showthread.php?t=17876&highlight=LAMP+HOWTO](http://www.ubuntuforums.org/showthread.php?t=17876&highlight=LAMP+HOWTO)

That should get you the basic server config then follow the Joomla guide to finish up.

---

### Post by Johnny Canuck on 2005-11-11
[QUOTE=wrtrdood]I'm running a fully loaded Ubuntu based server at unixshell.com (vhost).  It works like a charm and has been reliable.  Though a bit involved, installing Apache, PHP, MySQL and Joomla is not at all difficult.  A good guide can be found at
 [http://www.ubuntuforums.org/showthread.php?t=17876&highlight=LAMP+HOWTO](http://www.ubuntuforums.org/showthread.php?t=17876&highlight=LAMP+HOWTO)

That should get you the basic server config then follow the Joomla guide to finish up.[/QUOTE]
Thanks.

Tried some of that, but error messages cropped up, and I've got no clue what I'm doing.

Oh well, I'll start it all over yet again.

---

### Post by az on 2005-11-11
Drupal is easier to setup and run than Mambo (I haven't used it since it was forked to Joomla)

---

### Post by Johnny Canuck on 2005-11-12
Making slow but steady progress.  The Apachefriends install was fantastic.

Of course, I'd still love for it all to pop out of the box (as it were). . .

---

### Post by andlinux21 on 2005-12-14
mambo isnt that difficult to use I had two servers running mambo pages.  I havent tried it on Ubuntu however if you can get apache running and then mysql you shouldnt have a problem with mambo..

---

### Post by NotJustANewbie on 2005-12-14
Also be aware that xampp is not secure as default [(read here)]("http://www.apachefriends.org/en/xampp.html")

---

### Post by MystaMax on 2005-12-14
[quote=azz]Drupal is easier to setup and run than Mambo (I haven't used it since it was forked to Joomla)[/quote]

how do you figure? I can can get joomla configured and running in about 5 minutes. I don't think you could do that w/ drupal.  Although a great cms, joomla is far simpler to manage than drupal.

---

