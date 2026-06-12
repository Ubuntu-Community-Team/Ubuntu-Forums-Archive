---
title: "problems installing nginx"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by stewie17 on 2010-01-13
Hi all!

I'm trying to get Nginx set up and I ran into a problem. For a little background on what I've done up until this point, [check out this thread]("http://ubuntuforums.org/showthread.php?p=8660140#post8660140"). Also, I'm [following this tutorial]("http://library.linode.com/web-frameworks/ruby-on-rails/ruby-on-rails-nginx-ubuntu-9.04").

At this point I have Nginx istalled in opt/nginx. Now here's the problem. When I run
```

cd passenger-2.2.4/bin
./passenger-install-nginx-module

```everything goes just fine until it starts compiling source files. At which point I get this message
```

/usr/bin/ruby1.8 -S /usr/bin/rake clean nginx
/usr/bin/rake:19: undefined method `bin_path' for Gem:Module (NoMethodError)

```Does anyone know what is going wrong? Thanks in advance for any help.

---

