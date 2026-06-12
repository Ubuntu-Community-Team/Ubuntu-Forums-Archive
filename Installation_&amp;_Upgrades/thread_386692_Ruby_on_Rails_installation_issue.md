---
title: "Ruby on Rails installation issue"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by joe_f on 2007-03-17
Hello all,

First off, I'm quite new to any distribution of Linux, so if this question seems idiotic, I apologize in advance, this is not for lack of searching.

I'm trying to install Ruby on Rails on my Ubuntu here.  Doing the standard installation rendered me with Ruby 1.8.3, which horrifically, is not compatible with Rails *bonk*.  Now, I went back and installed Ruby 1.8.5 (which to the best of my knowledge works with Rails), but when I try and create a Rails application, it gives me the same error of:

Rails does not work with Ruby version 1.8.3.
Please upgrade to version 1.8.4 or downgrade to 1.8.2.

Doing a $ruby -v gives me:
ruby 1.8.5 (2006-08-25) [i686-linux]

So, it seems to think I'm still using 1.8.3 when my latest install was 1.8.5.  And no, I did not uninstall 1.8.3 at anytime, because honestly, I'm not really sure how.

Now, I'm sure I'm just overlooking where to change some sort of configuration file, but I can't for the life of me figure this out.  Any help would be much appreciated. 

Thank you in advance,
Joe

---

### Post by joe_f on 2007-03-18
Bump.

Just seeing if any of the Sunday morning crew may have any insight.

Thanks again,
Joe

---

### Post by madcow72 on 2007-03-18
Hey!  Not really sure what ruby is, actually.  But if you wanted to uninstall it, you should be able to just do:
```
sudo aptitude remove ruby
sudo aptitude purge ruby
```
in the terminal.  Then do:
```
sudo aptitude install ruby
```
which should install the latest version.

---

### Post by deman on 2007-03-19
Hi joe_f,

Maybe you can install directly from source. It's very easy and some more you can have the latest and greatest Ruby :guitar: 

You can follow the steps here at my blog:
[http://codersifu.blogspot.com/2007/03/howto-install-ruby-in-ubuntu-edgy-610.html](http://codersifu.blogspot.com/2007/03/howto-install-ruby-in-ubuntu-edgy-610.html)

---

### Post by erwinquita on 2007-03-19
Here's a basic [[COLOR="DarkRed"]screencast how-to install ruby on rails in ubuntu/debian[/COLOR]]("http://www.ibatayo.com/rails/categories/2/posts/9")

Ruby : 1.8.5-p12
RubyGems : 0.9.2
Rails : 1.2.1
OS : ubuntu 6.10 Edgy Eft

Hope this helps!

---

