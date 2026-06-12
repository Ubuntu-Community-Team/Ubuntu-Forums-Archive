---
title: "Problems installing bson_ext"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by noealejandro on 2012-06-03
Hello everybody.

I've been found plenty of information related to this problem, but I can't solve mine.  When I try to install bson_ext I get (details of my configuration are below):

$ sudo gem install bson_ext    
Building native extensions.  This could take a while...
ERROR:  Error installing bson_ext:
        ERROR: Failed to build gem native extension.

        /usr/bin/ruby1.9.1 extconf.rb
checking for asprintf()... *** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers.  Check the mkmf.log file for more
details.  You may need configuration options.

Provided configuration options:
        --with-opt-dir
        --without-opt-dir
        --with-opt-include
        --without-opt-include=${opt-dir}/include
        --with-opt-lib
        --without-opt-lib=${opt-dir}/lib
        --with-make-prog
        --without-make-prog
        --srcdir=.
        --curdir
        --ruby=/usr/bin/ruby1.9.1
/usr/lib/ruby/1.9.1/mkmf.rb:381:in `try_do': The compiler failed to generate an executable file. (RuntimeError)
You have to install development tools first.
        from /usr/lib/ruby/1.9.1/mkmf.rb:461:in `try_link0'
        from /usr/lib/ruby/1.9.1/mkmf.rb:476:in `try_link'
        from /usr/lib/ruby/1.9.1/mkmf.rb:619:in `try_func'
        from /usr/lib/ruby/1.9.1/mkmf.rb:894:in `block in have_func'
        from /usr/lib/ruby/1.9.1/mkmf.rb:790:in `block in checking_for'
        from /usr/lib/ruby/1.9.1/mkmf.rb:284:in `block (2 levels) in postpone'
        from /usr/lib/ruby/1.9.1/mkmf.rb:254:in `open'
        from /usr/lib/ruby/1.9.1/mkmf.rb:284:in `block in postpone'
        from /usr/lib/ruby/1.9.1/mkmf.rb:254:in `open'
        from /usr/lib/ruby/1.9.1/mkmf.rb:280:in `postpone'
        from /usr/lib/ruby/1.9.1/mkmf.rb:789:in `checking_for'
        from /usr/lib/ruby/1.9.1/mkmf.rb:893:in `have_func'
        from extconf.rb:3:in `<main>'


Gem files will remain installed in /usr/lib/ruby/gems/1.9.1/gems/bson_ext-1.6.2 for inspection.
Results logged to /usr/lib/ruby/gems/1.9.1/gems/bson_ext-1.6.2/ext/cbson/gem_make.out


------------------------------

My current configuration is:

$ which ruby
/usr/bin/ruby

$ whereis ruby
ruby: /usr/bin/ruby /usr/bin/ruby1.8 /usr/lib/ruby /usr/bin/X11/ruby /usr/bin/X11/ruby1.8 /usr/share/man/man1/ruby.1.gz

$ ruby -v
ruby 1.9.3p0 (2011-10-30 revision 33570) [i686-linux]

$ gem list
*** LOCAL GEMS ***

bson (1.6.2)
bundle (0.0.1)
bundler (1.1.4)
libv8 (3.10.8.0)
mongo (1.6.2)

$ ls -l /usr/bin/ruby*         
lrwxrwxrwx 1 root root    9 may 29 18:40 /usr/bin/ruby -> ruby1.9.1
-rwxr-xr-x 1 root root 5504 mar  3 09:21 /usr/bin/ruby1.8
-rwxr-xr-x 1 root root 5516 dic  2  2011 /usr/bin/ruby1.9.1

$ ls -l /usr/bin/gem*          
lrwxrwxrwx 1 root root   8 may 29 18:40 /usr/bin/gem -> gem1.9.1
-rwxr-xr-x 1 root root 888 jun  3 10:54 /usr/bin/gem1.9.1


And I have installed ruby-dev. I will appreciate any suggestion. Thanks in advance.

---

