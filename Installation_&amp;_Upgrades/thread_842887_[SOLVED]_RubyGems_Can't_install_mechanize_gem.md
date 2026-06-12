---
title: "[SOLVED] RubyGems: Can't install mechanize gem"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by rocsco on 2008-06-27
Entered:

gem install mechanize

Got the following:

ERROR:  Error installing mechanize:
        ERROR: Failed to build gem native extension.

/usr/bin/ruby1.8 extconf.rb install mechanize
extconf.rb:1:in `require': no such file to load -- mkmf (LoadError)
        from extconf.rb:1

Am I missing a dependency?

Would appreciate any advice as to how to fix.
Regards

---

### Post by Partyboi2 on 2008-06-27
Maybe you need the ruby1.8-dev package installed.

---

### Post by rocsco on 2008-06-27
Thanks for the quick reply.
Apparently I didn't have it and it seems there is some progress.
Would really appreciate it if you could have a look at the following because its not quite right yet.

Did a sudo apt-get install ruby1.8-dev and that completed OK.

-----------------------
 sudo gem install mechanize
Building native extensions.  This could take a while...
ERROR:  Error installing mechanize:
	ERROR: Failed to build gem native extension.

/usr/bin/ruby1.8 extconf.rb install mechanize
checking for main() in -lc... no
creating Makefile

make
cc -I. -I. -I/usr/lib/ruby/1.8/i486-linux -I.  -fPIC -fno-strict-aliasing -g -g -O2  -fPIC  -c hpricot_scan.c
In file included from ext/hpricot_scan/hpricot_scan.rl:9:
/usr/lib/ruby/1.8/i486-linux/ruby.h:40:21: error: stdlib.h: No such file or directory
/usr/lib/ruby/1.8/i486-linux/ruby.h:44:21: error: string.h: No such file or directory
/usr/lib/ruby/1.8/i486-linux/ruby.h:54:19: error: stdio.h: No such file or directory
/usr/lib/ruby/1.8/i486-linux/ruby.h:71:20: error: alloca.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:11,
                 from /usr/lib/ruby/1.8/i486-linux/ruby.h:91,
                 from ext/hpricot_scan/hpricot_scan.rl:9:
/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory
In file included from /usr/lib/ruby/1.8/i486-linux/ruby.h:718,
                 from ext/hpricot_scan/hpricot_scan.rl:9:
/usr/lib/ruby/1.8/i486-linux/missing.h:16:24: error: sys/time.h: No such file or directory
/usr/lib/ruby/1.8/i486-linux/missing.h:25:25: error: sys/types.h: No such file or directory
In file included from /usr/lib/ruby/1.8/i486-linux/ruby.h:719,
                 from ext/hpricot_scan/hpricot_scan.rl:9:
/usr/lib/ruby/1.8/i486-linux/intern.h:219: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;fd_set&#8217;
/usr/lib/ruby/1.8/i486-linux/intern.h:219: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;fd_set&#8217;
/usr/lib/ruby/1.8/i486-linux/intern.h:219: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;fd_set&#8217;
/usr/lib/ruby/1.8/i486-linux/intern.h:219: warning: &#8216;struct timeval&#8217; declared inside parameter list
/usr/lib/ruby/1.8/i486-linux/intern.h:219: warning: its scope is only this definition or declaration, which is probably not what you want
/usr/lib/ruby/1.8/i486-linux/intern.h:220: warning: &#8216;struct timeval&#8217; declared inside parameter list
/usr/lib/ruby/1.8/i486-linux/intern.h:455: warning: parameter names (without types) in function declaration
In file included from ext/hpricot_scan/hpricot_scan.rl:9:
/usr/lib/ruby/1.8/i486-linux/ruby.h:728:21: error: pthread.h: No such file or directory
In file included from ext/hpricot_scan/hpricot_scan.rl:9:
/usr/lib/ruby/1.8/i486-linux/ruby.h:730: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rb_nativethread_t&#8217;
ext/hpricot_scan/hpricot_scan.rl: In function &#8216;hpricot_scan&#8217;:
ext/hpricot_scan/hpricot_scan.rl:185: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
ext/hpricot_scan/hpricot_scan.rl:244: warning: incompatible implicit declaration of built-in function &#8216;memmove&#8217;
make: *** [hpricot_scan.o] Error 1


Gem files will remain installed in /usr/lib/ruby/gems/1.8/gems/hpricot-0.6 for inspection.
Results logged to /usr/lib/ruby/gems/1.8/gems/hpricot-0.6/ext/hpricot_scan/gem_make.out
------------------
Regards

---

### Post by rocsco on 2008-06-28
Problem solved.

Visit 

[http://www.rubyhead.com/2008/04/25/installing-ruby-rails-on-ubuntu-804-hardy-heron/](http://www.rubyhead.com/2008/04/25/installing-ruby-rails-on-ubuntu-804-hardy-heron/)

which has an excellent post on the procedure for installing ruby properly.

Why does Linux have to be so arcane?

Hasn't the penny dropped that it doesn't have to be this way!!!

---

### Post by RubyHead on 2009-01-09
> **rocsco said:**
> Problem solved.

Visit 

[http://www.rubyhead.com/2008/04/25/installing-ruby-rails-on-ubuntu-804-hardy-heron/](http://www.rubyhead.com/2008/04/25/installing-ruby-rails-on-ubuntu-804-hardy-heron/)

which has an excellent post on the procedure for installing ruby properly.

Why does Linux have to be so arcane?

Hasn't the penny dropped that it doesn't have to be this way!!!

Thanks rocsco!  I created a script for doing the install.  It works in both 8.04 and 8.10.  It can be downloaded from the same post.

---

### Post by ubunny on 2009-01-09
I got 'sudo gem install mechanize' to work but this solution didn't go for me 100%.  I had to add anything from sudo apt-get install for libxslt

include the following to that large apt-get install list:
libxslt-ruby libxslt-ruby1.8 libxslt1.1 libxslt1-dev libxslt1-dbg

afterwards 'sudo gem install mechanize' loaded 2 gems, mechanize and nokogiri

Otherwise you'll get the following errors

```

 sudo gem install mechanize
Building native extensions.  This could take a while...
ERROR:  Error installing mechanize:
	ERROR: Failed to build gem native extension.

/usr/bin/ruby1.8 extconf.rb install mechanize
checking for xmlParseDoc() in -lxml2... yes
checking for xsltParseStylesheetDoc() in -lxslt... no
checking for exsltFuncRegister() in -lexslt... no
checking for libxml/xmlversion.h in /opt/local/include,/opt/local/include/libxml2,/usr/include/libxml2,/usr/include,/usr/include/libxml2,/usr/local/include/libxml2... yes
checking for libxslt/xslt.h in /opt/local/include,/opt/local/include/libxml2,/usr/include/libxml2,/usr/include,/usr/include/libxml2,/usr/local/include/libxml2... no
need libxslt
*** extconf.rb failed ***
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
	--ruby=/usr/bin/ruby1.8
	--with-xml2lib
	--without-xml2lib
	--with-xsltlib
	--without-xsltlib
	--with-exsltlib
	--without-exsltlib


Gem files will remain installed in /usr/lib/ruby/gems/1.8/gems/nokogiri-1.1.0 for inspection.
Results logged to /usr/lib/ruby/gems/1.8/gems/nokogiri-1.1.0/ext/nokogiri/gem_make.out


```

cheers

---

### Post by Ordimus on 2011-07-02
> [http://www.rubyhead.com/2008/04/25/installing-ruby-rails-on-ubuntu-804-hardy-heron/](http://www.rubyhead.com/2008/04/25/installing-ruby-rails-on-ubuntu-804-hardy-heron/)

The above link no longer works, I am having the same issue as rocsco was.

---

