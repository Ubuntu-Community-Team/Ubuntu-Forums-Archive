---
title: "`require': no such file to load — mkmf (LoadError)"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by jang3 on 2014-03-19
I was trying to install rails on Ubuntu Natty Narwhal 11.04, using ruby1.9.1.


I installed ruby using apt-get install ruby1.9.1-full which contains the dev package. I googled the error and all have suggested I install the 1.9.1-dev which I already have.

> Building native extensions.  This could take a while...
ERROR:  Error installing rails:
    ERROR: Failed to build gem native extension.


        /usr/bin/ruby1.8 extconf.rb
extconf.rb:36:in `require': no such file to load -- mkmf (LoadError)
    from extconf.rb:36




Gem files will remain installed in /usr/lib/ruby/gems/1.8/gems/bcrypt-ruby-3.0.1 for inspection.
Results logged to /usr/lib/ruby/gems/1.8/gems/bcrypt-ruby-3.0.1/ext/mri/gem_make.out

---

