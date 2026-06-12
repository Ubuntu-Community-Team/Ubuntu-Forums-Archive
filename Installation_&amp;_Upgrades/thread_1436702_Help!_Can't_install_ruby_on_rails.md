---
title: "Help! Can't install ruby on rails"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by zhinker on 2010-03-23
Hi,

I'm trying to install ruby on rails on Ubuntu 9.10.  I'm following the instructions on this site: 
[http://castilho.biz/blog/2009/11/05/ruby-on-rails-ubuntu-9-10-karmic-koala/](http://castilho.biz/blog/2009/11/05/ruby-on-rails-ubuntu-9-10-karmic-koala/)

However, when I try to install Rails I get an error:
```
$ sudo gem install rails
ERROR:  While executing gem ... (Gem::RemoteFetcher::FetchError)
    timed out ([http://gems.rubyforge.org/gems/rake-0.8.7.gem](http://gems.rubyforge.org/gems/rake-0.8.7.gem))
```

It seems like gem can't access [http://gems.rubyforge.org/gems/rake-0.8.7.gem](http://gems.rubyforge.org/gems/rake-0.8.7.gem) for some reason, but when I try to go directly to that address I get the option to download it.  Any ideas how to get around this problem?

I'm thinking if I can somehow tell gem to look for the file locally I can download it and install rails that way.

Please help!

Thanks

---

### Post by slang on 2010-03-23
Hi,

same problem here.
You can download the gems and install them locally.
For that you need to install them like this:

sudo gem install rake-0.8.7.gem

---

### Post by slang on 2010-03-23
Found another solution for this problem.
If you are using virtual box, you have to switch the virtual box network adapter from NAT to Brigded and everything should work fine.

---

### Post by zhinker on 2010-03-23
AHA! Switching to Bridged did the trick!  Thanks a lot!

---

