---
title: "Help me getting gem error! while installing beef"
date: 2016-07-17
forum: Installation &amp; Upgrades
---

### Post by dc31 on 2016-07-17
I was trying to install beef in my ubuntu 16.04 
but when i tryed to install all the gems using bundle install :: then it is giving me error any solution??

```
root@spirit:/opt/beef# bundle installDon't run Bundler as root. Bundler can ask for sudo if it is needed, and
installing your bundle as root will break this application for all non-root
users on this machine.
Warning: the running version of Bundler is older than the version that created the lockfile. We suggest you upgrade to the latest version of Bundler by running `gem install bundler`.
Fetching gem metadata from https://rubygems.org/..........
Fetching version metadata from https://rubygems.org/...
Fetching dependency metadata from https://rubygems.org/..
Using addressable 2.4.0
Using ansi 1.5.0
Using chunky_png 1.3.5
Using daemons 1.2.3
Using fastercsv 1.5.5
Using json 1.8.3
Using json_pure 1.8.3
Using multi_json 1.11.3
Installing eventmachine 1.0.9.1 with native extensions


Gem::Ext::BuildError: ERROR: Failed to build gem native extension.


    current directory: /var/lib/gems/2.3.0/gems/eventmachine-1.0.9.1/ext
/usr/bin/ruby2.3 -r ./siteconf20160717-10318-lxlul1.rb extconf.rb
mkmf.rb can't find header files for ruby at /usr/lib/ruby/include/ruby.h


extconf failed, exit code 1


Gem files will remain installed in /var/lib/gems/2.3.0/gems/eventmachine-1.0.9.1 for inspection.
Results logged to /var/lib/gems/2.3.0/extensions/x86_64-linux/2.3.0/eventmachine-1.0.9.1/gem_make.out
Installing http_parser.rb 0.6.0 with native extensions


Gem::Ext::BuildError: ERROR: Failed to build gem native extension.


    current directory: /var/lib/gems/2.3.0/gems/http_parser.rb-0.6.0/ext/ruby_http_parser
/usr/bin/ruby2.3 -r ./siteconf20160717-10318-zon21l.rb extconf.rb
mkmf.rb can't find header files for ruby at /usr/lib/ruby/include/ruby.h


extconf failed, exit code 1


Gem files will remain installed in /var/lib/gems/2.3.0/gems/http_parser.rb-0.6.0 for inspection.
Results logged to /var/lib/gems/2.3.0/extensions/x86_64-linux/2.3.0/http_parser.rb-0.6.0/gem_make.out
Using erubis 2.7.0
Using espeak-ruby 1.0.3
Using execjs 2.6.0
Using geoip 1.6.1
Using librex 0.0.999
Using libv8 3.11.8.17
Using mime-types-data 3.2016.0221
Using mojo_magick 0.5.6
Installing msgpack 0.5.12 with native extensions


Gem::Ext::BuildError: ERROR: Failed to build gem native extension.


    current directory: /var/lib/gems/2.3.0/gems/msgpack-0.5.12/ext/msgpack
/usr/bin/ruby2.3 -r ./siteconf20160717-10318-1p0hbw0.rb extconf.rb
mkmf.rb can't find header files for ruby at /usr/lib/ruby/include/ruby.h


extconf failed, exit code 1


Gem files will remain installed in /var/lib/gems/2.3.0/gems/msgpack-0.5.12 for inspection.
Results logged to /var/lib/gems/2.3.0/extensions/x86_64-linux/2.3.0/msgpack-0.5.12/gem_make.out
Using parseconfig 1.0.8
Using rack 1.6.4
Using rainbow 2.1.0
Using ref 2.0.0
Using rubyzip 1.2.0
Using tilt 2.0.2
Using tins 1.10.1
Using bundler 1.11.2
Using data_objects 0.10.17
Using dm-core 1.2.1
Using rqrcode 0.10.1
An error occurred while installing eventmachine (1.0.9.1), and Bundler cannot
continue.
Make sure that `gem install eventmachine -v '1.0.9.1'` succeeds before
bundling.
root@spirit:/opt/beef# ruby beef
Could not find dm-do-adapter-1.2.0 in any of the sources
Run `bundle install` to install missing gems.
root@spirit:/opt/beef# 



```

---

### Post by TheFu on 2016-07-17
My RoR knowledge is a little dated. Haven't touch it in a few years, but ... best practice is to use a complete ruby environment that you own and not to touch/use the OS installed version.  That means inusing rbenv or rvm or something newer. 

Also, never use root to do webapp stuff.

So, to solve this, I'd start by looking at the version of all the major packages required - ruby, rails, other big things and work backwards to setup an rvm environment with those exact versions installed.  Then I'd use the version of bundler that works with that setup to install all the dependencies.   Never touching the root account the entire time.

Then, if there are issues during the dependencies, I'd start by reading each line of the output carefully ... looking for output logs, opening each and working through them for errors and log files. Fix the first error and try again. Fix the new, first error, and try again.  Make sense?

Not really relevant now, but the first error above is: ```
mkmf.rb can't find header files for ruby at /usr/lib/ruby/include/ruby.h
```  
Questions:
a) is that error correct?  Does ruby.h NOT exist where it says it doesn't?
b) Does ruby.h exist somewhere else on the machine? Does that location *make sense*?  If not, 
c) Can you install whatever ruby bundle would be needed to make that file available?  I'm not suggesting an apt-get ... I'm suggesting using rvm/rbenv to get the correct package and install it within the specific version of ruby environment being used.
d) "native extensions" usually means compiled C/C++ code.  It is fine to install the compilers and required dependencies for those using apt-get.  build-essential is usually the package to start with, but there may be other dependencies too. 

Installing these packages might be all that is needed to fix the root cause of the error above, doubtful, but possible. I think there is part of ruby missing too.

Did I mention not to use root or sudo for any ruby/rails/bundler/gem operations? Please don't. installing those things with root is a security risk. Also, don't run the webapp as root either. Why make it easier for crackers to pwn the system?  The only place you might need sudo is when setting up the reverse proxy into the webapp - those config files are generally, and necessarily, owned by root.

Make sense?  I'll try to help with more details, if you ask along the "best practice" route.

---

