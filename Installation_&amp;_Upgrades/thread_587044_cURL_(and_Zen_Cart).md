---
title: "cURL (and Zen Cart)"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by maudmoonshine on 2007-10-22
Just so you know who you are dealing with: I know very little unix.
 
I'm trying to install Zen Cart on what was 7.04 server and have got everything to be green ticks (changed permissions, installed PHP GD support, several other little changes) in Zen Cart's install procedure (zc_install) except: PHP cURL support.
 
I've searched here and google and what I've found has not helped (it's me; I'm sure what's there would be quite clear to most people).
 
One thing I did find (or think I've found) on here was some security problems with cURL that effected all Ubuntu releases up to and including 7.04; but no mention of 7.10. So, you guessed it, I've upgraded to 7.10. No problem with that (it did ask me one thing I did not have a clue about but I just pushed OK and it all seems to be working again: apache, MYSql and PHP).
 
But I've still got the PHP cURL support off warning with Zen Cart. Now I know I need this because of the PayPal hook-up module I have installed on my live shop (this one I'm installing here is for testing but I need to test against PayPal's sandbox too).
 
To cut to the chase: how do I get PHP cURL support installed? and/or working?

---

### Post by maudmoonshine on 2007-10-22
Still not solved my little problem; however...
 
did a:
 
```
 
apt-cache search php

```
 
which brought up something called: 
 
php5-curl - CURL module for php5
 
which looks interesting. So I did a:
 
```
 
sudo apt-get install php-5-curl

```
 
which gave:
 
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package php-5-curl
 
What have I done wrong?

---

### Post by maudmoonshine on 2007-10-23
There's a huge echo in here...
 
Anyway, if you are having similar problems to me then go here: [http://www.theatons.com/blog/2007/07/10/ubuntu-install-setup-curl-for-php-php5/](http://www.theatons.com/blog/2007/07/10/ubuntu-install-setup-curl-for-php-php5/)

---

### Post by Uldis on 2007-12-07
Your code
```
sudo apt-get install php-5-curl
```
Right code 
```
sudo apt-get install php5-curl
```

---

### Post by skrimpy on 2007-12-07
You can also install via Synaptic - just search for "cURL" and then choose to install php5-curl.

My local Zencart installation works beautifully.

---

