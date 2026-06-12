---
title: "installing and using rails"
date: 2013-02-02
forum: Installation &amp; Upgrades
---

### Post by lukenkosi on 2013-02-02
hi, 
i need help here. i am new to programming and interested in learning  rubyonrails. 
i installed the above mentioned software on ubuntu 12.10 using i found  on ubuntu community page. 
after installation, i tried to run the command rake db:migrate, and i  got the following errors please help. 





luke@luke-pc:~/www/railsapp$ rake db:migrate 
NOTE: Gem.source_index is deprecated, use Specification. It will be  removed on or after 2011-11-01. 
Gem.source_index called from  /home/luke/www/railsapp/vendor/rails/railties/lib/rails/gem_dependency.rb:21. 
NOTE: Gem::SourceIndex#initialize is deprecated with no replacement. It  will be removed on or after 2011-11-01. 
Gem::SourceIndex#initialize called from  /home/luke/www/railsapp/vendor/rails/railties/lib/rails/vendor_gem_source_index.rb:100. 
NOTE: Gem::SourceIndex#add_spec is deprecated, use  Specification.add_spec. It will be removed on or after 2011-11-01. 
Gem::SourceIndex#add_spec called from  /usr/local/lib/site_ruby/1.9.1/rubygems/source_index.rb:91. 
NOTE: Gem::SourceIndex#add_spec is deprecated, use  Specification.add_spec. It will be removed on or after 2011-11-01. 
Gem::SourceIndex#add_spec called from  /usr/local/lib/site_ruby/1.9.1/rubygems/source_index.rb:91. 
NOTE: Gem::SourceIndex#add_spec is deprecated, use  Specification.add_spec. It will be removed on or after 2011-11-01. 
Gem::SourceIndex#add_spec called from  /usr/local/lib/site_ruby/1.9.1/rubygems/source_index.rb:91. 
NOTE: Gem::SourceIndex#add_spec is deprecated, use  Specification.add_spec. It will be removed on or after 2011-11-01. 
Gem::SourceIndex#add_spec called from  /usr/local/lib/site_ruby/1.9.1/rubygems/source_index.rb:91. 
NOTE: Gem::SourceIndex#add_spec is deprecated, use  Specification.add_spec. It will be removed on or after 2011-11-01. 
Gem::SourceIndex#add_spec called from  /usr/local/lib/site_ruby/1.9.1/rubygems/source_index.rb:91. 
NOTE: Gem::SourceIndex#add_spec is deprecated, use  Specification.add_spec. It will be removed on or after 2011-11-01. 
Gem::SourceIndex#add_spec called from  /usr/local/lib/site_ruby/1.9.1/rubygems/source_index.rb:91. 
rake aborted! 
ERROR: 'rake/rdoctask' is obsolete and no longer supported. Use  'rdoc/task' (available in RDoc 2.4.2+) instead. 
/home/luke/www/railsapp/Rakefile:8:in `<top (required)>' 
(See full trace by running task with --trace)

---

### Post by dino99 on 2013-02-03
as said:  Use 'rdoc/task' (available in RDoc 2.4.2+) to avoid using deprecated syntaxes.

[http://ruby.railstutorial.org/help](http://ruby.railstutorial.org/help)
[https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)

---

### Post by mariosant on 2013-02-03
Well ruby on rails can be a little complicated is someone does not guide you. I will write the steps for a successful install of ruby on rails on ubuntu.

* First of all remove any ruby stuff you have already installed.
* Install ruby 1.9.3: 
```
$ sudo apt-get install ruby1.9.3
```

Ruby has a package system, similar with ubuntu's apt-get. It's called rubygems. This is what you should do to install rails in your home folder:
* Edit your ~/.bashrc and add those two lines
```
export GEM_HOME=/home/<your actual username>/.gems
export PATH=$GEM_HOME/bin:$PATH
```
* Make sure that the path settings are in effect:
```
$ source ~/.bashrc
```

Finally, install rails or any other gem you want:
```
$ gem install rails
```

---

### Post by lukenkosi on 2013-02-05
that was so helpful.

now ruby -v gives me
ruby 1.9.3p194 (2012-04-20 revision 35410) [i686-linux]
and rails -v gives me
Rails 3.2.6

I still have some problems, when i run 
rails new /home/user/www/railsapp/
at the end i get an error
/usr/bin/ruby1.9.1: No such file or directory -- /usr/bin/bundle (LoadError)

user@user-pc:~/www/railsapp$ rake db:migrate --trace
rake aborted!
cannot load such file -- bundler/setup
/usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
/usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
/home/luke/www/railsapp/config/boot.rb:6:in `<top (required)>'
/usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
/usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
/home/luke/www/railsapp/config/application.rb:1:in `<top (required)>'
/usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
/usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
/home/luke/www/railsapp/Rakefile:5:in `<top (required)>'
/usr/lib/ruby/gems/1.9.1/gems/rake-10.0.3/lib/rake/rake_module.rb:25:in `load'
/usr/lib/ruby/gems/1.9.1/gems/rake-10.0.3/lib/rake/rake_module.rb:25:in `load_rakefile'
/usr/lib/ruby/gems/1.9.1/gems/rake-10.0.3/lib/rake/application.rb:583:in `raw_load_rakefile'
/usr/lib/ruby/gems/1.9.1/gems/rake-10.0.3/lib/rake/application.rb:89:in `block in load_rakefile'
/usr/lib/ruby/gems/1.9.1/gems/rake-10.0.3/lib/rake/application.rb:160:in `standard_exception_handling'
/usr/lib/ruby/gems/1.9.1/gems/rake-10.0.3/lib/rake/application.rb:88:in `load_rakefile'
/usr/lib/ruby/gems/1.9.1/gems/rake-10.0.3/lib/rake/application.rb:72:in `block in run'
/usr/lib/ruby/gems/1.9.1/gems/rake-10.0.3/lib/rake/application.rb:160:in `standard_exception_handling'
/usr/lib/ruby/gems/1.9.1/gems/rake-10.0.3/lib/rake/application.rb:70:in `run'
/usr/lib/ruby/gems/1.9.1/gems/rake-10.0.3/bin/rake:33:in `<top (required)>'
/usr/local/bin/rake:23:in `load'
/usr/local/bin/rake:23:in `<main>'

---

