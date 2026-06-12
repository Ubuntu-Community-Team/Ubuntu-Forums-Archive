---
title: "Rake gives rake/rdoctask' is obsolete and no longer supported. Use 'rdoc/task' (avail"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by gleble on 2013-01-28
I use 10.04. I have just reinstalled ruby 1.9.2 and rails 3.0.6.rc1. 
When I try rake db:migrate, I get:
```
naat@naat-laptop:~/eskvalleytales8$ rake db:migrate
rake aborted!
ERROR: 'rake/rdoctask' is obsolete and no longer supported. Use 'rdoc/task' (available in RDoc 2.4.2+) instead.
/home/naat/eskvalleytales8/Rakefile:6:in `require
```'
This is from my rakefile:
```
require 'rubygems'
require 'bundler/setup'

require 'rake'
require 'rake/testtask'
require 'rdoc/task'

$LOAD_PATH << File.join(File.dirname(__FILE__), 'lib')
require 'paperclip
```'
Has anybody any idea why I get his error ad how to fix it?

---

### Post by diverso on 2013-03-01
Hi, 

I also have the same problem while I'm running on osx I got the exact same error, I found this browsing for solutions, [bugs.debian.org/cgi-bin/bugreport.cgi?bug=649984]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=649984") and also somebody was suggesting to edit the rakefile in order to replace rake/rdoctask with rdoc/task. Did you manage to solve this? still wondering how to.

---

