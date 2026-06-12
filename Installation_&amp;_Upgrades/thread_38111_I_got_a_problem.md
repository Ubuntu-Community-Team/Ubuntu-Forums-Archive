---
title: "I got a problem"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by Kakason on 2005-05-30
I am installing Ruby.1.8.2
and I got up to 'make install'

This appears from my terminal.

 ```

./miniruby ./inst ruby.rb --dest-dir="" --make="make" --mflags="" --make-flags="" --mantype="doc"
mkdir -p -m 755 /usr/local/libruby/1.8 /usr/local/lib/ruby/1.8/i686-linux /usr/loca/lib/ruby
site_ruby/1.8 /usr/local/lib/ruby/site_ruby/1.8/i686_linux
/home/username/ruby-1.8.2/lib/fileutils.rb:209:in `mkdir': Permission denied - /usr/local/lin/ruby
Errno::EACCES
from /home/username/ruby-1.8.2/lib/fileutils.rb:209:in`fu_mkdir'
from /home/username/ruby-1.8.2/lib/fileutils.rb:193:in`makedirs'
from /home/username/ruby-1.8.2/lib/fileutils.rb:191:in`reverse-each'
from /home/username/ruby-1.8.2/lib/fileutils.rb:191:in`makedirs'
from /home/username/ruby-1.8.2/lib/fileutils.rb:177:in`each'
from /home/username/ruby-1.8.2/lib/fileutils.rb:177:in`makedirs'
from /home/username/ruby-1.8.2/lib/fileutils.rb:967:in`makedirs'
from ./inst ruby.rb:71:in`makedirs'
from ./inst ruby.rb:99:in
make: *** [install-nodoc] Error 1
```

Also I am  the admin.
Also I would like to ask what is flex, and how to I install it on my machine?

Kakason

---

### Post by mostwanted on 2005-05-30
Is 1.8.2 *that* important, because you can just apt-get 1.8.1. Saves the trouble of compiling stuff yourself.

$ sudo apt-get install ruby

---

### Post by Kakason on 2005-05-30
O, Ok. Thanks.

Anyone knows what flex is, because when I try to ./configure Wine, it says I need that. Anyone knows?

NOTE: I also tried 
sudo apt-get install flex
and it didn't work

---

### Post by mingus on 2005-05-31
is this by chance it?

[http://packages.ubuntu.com/hoary/devel/flex](http://packages.ubuntu.com/hoary/devel/flex)

--m

---

### Post by Kakason on 2005-06-01
Thanks.
I finally understand why I couldn't install ruby.
Just had to type this in
sudo make install

Kakason

---

