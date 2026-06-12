---
title: "Ruby gems not working...?"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by japtar10101 on 2008-05-08
I'm trying to install rails according to this website: [https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)


However, instead of wget, I directly downloaded rubygems from [http://rubyforge.org/frs/?group_id=126](http://rubyforge.org/frs/?group_id=126)

finally, I followed these commands:
```
tar xzvf rubygems-1.1.1.tgz
cd rubygems-1.1.1
sudo ruby setup.rb
sudo ln -s /usr/bin/gem1.8 /usr/bin/gem

```

After that, whenever I run gem, I get this error:
```
/usr/bin/gem:23: uninitialized constant Gem::GemRunner (NameError)
```

Which is...a Ruby error.  What went wrong?  How can I fix this?

By the way, /usr/bin/gem looks like this:
```
#! /usr/bin/ruby1.8
#--
# Copyright 2006 by Chad Fowler, Rich Kilmer, Jim Weirich and others.
# All rights reserved.
# See LICENSE.txt for permissions.
#++


require 'rubygems'
Gem.manage_gems

required_version = Gem::Version::Requirement.new(">= 1.8.0")
unless  required_version.satisfied_by?(Gem::Version.new(RUBY_VERSION))
  puts "Expected Ruby Version #{required_version}, was #{RUBY_VERSION}"
  exit(1)
end

# We need to preserve the original ARGV to use for passing gem options
# to source gems.  If there is a -- in the line, strip all options after
# it...its for the source building process.
args = !ARGV.include?("--") ? ARGV.clone : ARGV[0...ARGV.index("--")]

Gem::GemRunner.new.run(args) #ERROR line
```

---

### Post by Partyboi2 on 2008-05-08
Maybe this fix will work for you.
[http://www.nickpeters.net/2007/12/31/fix-for-uninitialized-constant-gemgemrunner-nameerror/](http://www.nickpeters.net/2007/12/31/fix-for-uninitialized-constant-gemgemrunner-nameerror/)

---

