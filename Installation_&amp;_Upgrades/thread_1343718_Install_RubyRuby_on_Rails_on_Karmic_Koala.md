---
title: "Install Ruby/Ruby on Rails on Karmic Koala"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by Lavix on 2009-12-02
I followed the step-by-step tutorial to install Ruby:RoR on Ubuntu 9.10 (see more details on [http://www.hackido.com/2009/11/install-ruby-on-rails-on-ubuntu-karmic.html)](http://www.hackido.com/2009/11/install-ruby-on-rails-on-ubuntu-karmic.html))
Everything was OK util I tried to install rails:
```

RubyGems installed the following executables:
  /usr/bin/gem1.8

serge@ubuntu:~/rubygems-1.3.5$ gem -v
The program 'gem' can be found in the following packages:
 * rubygems1.8
 * rubygems1.9.1
Try: sudo apt-get install <selected package>
gem: command not found
serge@ubuntu:~/rubygems-1.3.5$ sudo ln -s /usr/bin/gem1.8 /usr/local/bin/gem
serge@ubuntu:~/rubygems-1.3.5$ sudo ln -s /usr/bin/ruby1.8 /usr/local/bin/ruby
serge@ubuntu:~/rubygems-1.3.5$ sudo ln -s /usr/bin/rdoc1.8 /usr/local/bin/rdoc
serge@ubuntu:~/rubygems-1.3.5$ sudo ln -s /usr/bin/ri1.8 /usr/local/bin/ri
serge@ubuntu:~/rubygems-1.3.5$ sudo ln -s /usr/bin/irb1.8 /usr/local/bin/irb
serge@ubuntu:~/rubygems-1.3.5$ gem -v
1.3.5
serge@ubuntu:~/rubygems-1.3.5$ sudo gem install rails
ERROR:  Error installing rails:
  invalid gem format for /usr/lib/ruby/gems/1.8/cache/rake-0.8.7.gem
serge@ubuntu:~/rubygems-1.3.5$ cd ~
serge@ubuntu:~$ sudo gem install rails
ERROR:  Error installing rails:
  invalid gem format for /usr/lib/ruby/gems/1.8/cache/rake-0.8.7.gem
serge@ubuntu:~$ udo gem install gemcutter
The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo
udo: command not found
serge@ubuntu:~$ sudo gem install gemcutter
ERROR:  Error installing gemcutter:
  invalid gem format for /usr/lib/ruby/gems/1.8/cache/json_pure-1.2.0.gem
serge@ubuntu:~$ 

```
Has anybody had the same problem? How to resolve it, please? Thank you.

---

### Post by eljacob on 2009-12-09
Hi,

I used the following steps and it is working on my machine:

- installed Ruby and RubyGems using Synaptic Package Manager (graphical interface)

- installed Rails with the following command:
sudo gem install rails

- installed Rake with the following command:
sudo gem install rake

- updated the path
add export PATH=/var/lib/gems/1.8/bin:$PATH as the last line of ~/.bashrc

Actually you could install everything at once simply by installing the meta-package rails, using Synaptic Manager, but I read on other threads that it is better to install rails using rubygems


I hope it works for you.

---

### Post by Lavix on 2009-12-09
What exactly should I check in Synaptic Manager to install Ruby, please?
Thank you.

---

### Post by eljacob on 2009-12-09
you should check the following packages:
ruby
rubygems

if you intend to use sqlite3 and the internal Ruby web server (WEBrick) you should also check:
sqlite3
libsqlite3-ruby
libopenssl-ruby

As of now these packages will install Ruby 1.8.7, RubyGems 1.3.5 and all their dependencies. After that you can install Rails using RubyGems, with will make it easier for you to keep it updated later.

---

### Post by Lavix on 2009-12-09
I did as you adviced:
- installed ruby, rubygems via Synaptic Package Manager
and then:
```

serge@ubuntu:~$ sudo gem install rake
ERROR:  Error installing rake:
    invalid gem format for /var/lib/gems/1.8/cache/rake-0.8.7.gem
serge@ubuntu:~$ gem -v
1.3.5
serge@ubuntu:~$ ruby -v
ruby 1.8.7 (2009-06-12 patchlevel 174) [i486-linux]
serge@ubuntu:~$ 

```Of course I added 
```

export PATH=/var/lib/gems/1.8/bin:$PATH as the last line of ~/.bashrc

```

---

### Post by eljacob on 2009-12-09
If you have the file rake-0.8.7.gem in your cache directory you probably installed it earlier. I don't know why it is complaining about this file, but you might try to uninstall rake and install it again:

uninstall rake:
sudo gem uninstall rake

remove the gem from your machine if it is still there:
sudo rm /var/lib/gems/1.8/gems/rake-0.8.7.gem
sudo rm /var/lib/gems/1.8/cache/rake-0.8.7.gem

install rake again:
sudo gem install rake

---

### Post by Lavix on 2009-12-09
It's very strange what I have:
```

serge@ubuntu:~$ gem list

*** LOCAL GEMS ***


serge@ubuntu:~$ sudo rm /var/lib/gems/1.8/cache/rake-0.8.7.gem
serge@ubuntu:~$ sudo gem install rake
ERROR:  Error installing rake:
    invalid gem format for /var/lib/gems/1.8/cache/rake-0.8.7.gem
serge@ubuntu:~$ 

```

---

### Post by eljacob on 2009-12-09
I've read on other threads and forums that if we try to use both apt-get (Synaptics) and gem to install and update our system we will end up with a mess.

I installed only the package "rails" on a test machine and everything worked fine, but RubyGems didn't recognize the installed gems, as if they did not exist - and I couldn't update them later.

That's why I used Synaptic only to install the Ruby interpreter and RubyGems, and installed all the gems (including Rake and Rails) using RubyGems.

If Rake was installed on your machine using Synaptic, as a dependency of another package (maybe rails) RubyGem won't recognize it.

You could try to find rake and remove with these commands:
rake --version       #will show if you have rake installed, and which version
which rake              #will show you where it is been called from - the directory where it is installed

Or maybe you should use Synaptic to uninstall all the packages you installed related to Ruby, Rails or Rake, and start over again. I would to that...

---

### Post by Lavix on 2009-12-09
```

serge@ubuntu:~$ rake --version
The program 'rake' is currently not installed.  You can install it by typing:
sudo apt-get install rake
rake: command not found
serge@ubuntu:~$ sudo apt-get install rake
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  rake
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 141kB of archives.
After this operation, 1,176kB of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com karmic/universe rake 0.8.4-1 [141kB]
Fetched 141kB in 1s (136kB/s)
Selecting previously deselected package rake.
(Reading database ... 151522 files and directories currently installed.)
Unpacking rake (from .../archives/rake_0.8.4-1_all.deb) ...
Processing triggers for man-db ...
Setting up rake (0.8.4-1) ...
serge@ubuntu:~$ rake --version
rake, version 0.8.4

```

---

### Post by Lavix on 2009-12-09
```

serge@ubuntu:~$ sudo gem update --system --debug -V
Exception `NameError' at /usr/local/lib/site_ruby/1.8/rubygems/command_manager.rb:161 - uninitialized constant Gem::Commands::UpdateCommand
Exception `Gem::LoadError' at /usr/local/lib/site_ruby/1.8/rubygems.rb:827 - Could not find RubyGem test-unit (>= 0)

Updating RubyGems
Exception `Gem::LoadError' at /usr/local/lib/site_ruby/1.8/rubygems.rb:827 - Could not find RubyGem sources (> 0.0.1)

GET 200 OK: http://gems.rubyforge.org/latest_specs.4.8.gz
Nothing to update
serge@ubuntu:~$ 

```

My gems environment:
```

serge@ubuntu:~$ gem environment
RubyGems Environment:
  - RUBYGEMS VERSION: 1.3.5
  - RUBY VERSION: 1.8.7 (2009-06-12 patchlevel 174) [i486-linux]
  - INSTALLATION DIRECTORY: /usr/lib/ruby/gems/1.8
  - RUBY EXECUTABLE: /usr/bin/ruby1.8
  - EXECUTABLE DIRECTORY: /usr/bin
  - RUBYGEMS PLATFORMS:
    - ruby
    - x86-linux
  - GEM PATHS:
     - /usr/lib/ruby/gems/1.8
     - /home/serge/.gem/ruby/1.8
  - GEM CONFIGURATION:
     - :update_sources => true
     - :verbose => true
     - :benchmark => false
     - :backtrace => false
     - :bulk_threshold => 1000
  - REMOTE SOURCES:
     - http://gems.rubyforge.org/
serge@ubuntu:~$ 

```

---

### Post by eljacob on 2009-12-09
It seems you are in the middle of a fight between apt-manager and gems - each one does not recognize components installed by the other.

I don't know how to fix this. There is probably a way to tell RubyGems to recognize gems already installed, but I have no idea how.

I've seen posts with problems similar to yours as old as 2005, so this is not a new problem.

I would recommend that you use Synaptic to uninstall all packages related to Rails, Ruby and Rake.

Then you could reinstall only Ruby and RubyGems and use gem to install everything else, as I posted before. 

It will take only a few minutes, should work (worked for me anyway), and would be much easier than to figure out what you have installed with each package manager and fix it.

And you will end up with the latest version for all gems. You downloaded rake 0.8.4 using "apt-get install rake", and I received 0.8.7 using "gem install rake".

---

### Post by Lavix on 2009-12-09
Tnak you [eljacob]("http://ubuntuforums.org/member.php?u=958317") for your participation.
After long googling I also saw that issue was discussed still in 2005.
Unfortunately, I can't find an isue from that problem, - no matter how I install Ruby and  gems. Hope someone will find a solution one day.

---

### Post by eljacob on 2009-12-09
Hi Lavix,

If you want to give it another shot, I created a couple of scripts that might help fixing your installation. 

The first script, remove_ror.sh, tries to remove any packages related to Ruby and/or Rails that might be installed on your system. Please, run it first. Some packages might not be installed, so it is ok if you see some errors.

After that the second script, install_ror.sh installs Ruby, RubyGems and Rails again the way it worked for me.

If you decide to run these scripts please be sure that you have a current backup of your machine. I revised both as carefully as I could, I ran both on my machine, and it worked, but we can never know for sure.

To run these scripts download them to your machine, set the execution attribute, and execute both:
sudo chmod +x remove_ror.sh
sudo chmod +x install_ror.sh
./remove_ror.sh
./install_ror.sh

After running both scripts check if the last line in your ~/.bashrc is:
export PATH=/var/lib/gems/1.8/bin:$PATH

Close your console window and restart it, so that it will reload .bashrc, and try typing:
ruby --version
rails --version
rake --version
gem list

If everything worked fine you should have ruby 1.8.7, rails 2.3.5 and rake 0.8.7 installed (as of today). You should also see all the basic gems listed.

Good luck!

---

### Post by Lavix on 2009-12-10
Thank you so much [eljacob]("http://ubuntuforums.org/member.php?u=958317"). I'll try it tomorrow.
But I checked it once again and it looks as if when executing gem command to install no matter whicg gem, ruby tries to pass through the port 7000 that was blocked by the enterprise firewall. So I took another laptop, installed Ruby on it and tried to get gems from my home. And everything was installed without any problems. 
I executed 'netstat' util on a Windows PC and it showed me ports in use; When I opened the file that ruby was angry for when installing gems: ../cache/gem_name, it's there where the number 7000 was indicated as well as the error exact content( I'd prefer that the message to be more user-friendly)
```

<html><head>
<meta http-equiv="content-type" content="text/html; charset=ISO-8859-1">
</head><body><header>
</header>

<center><img src="http://192.168.50.254:7000/blocked.jpg">
<p><b>This website is blocked.</b></p>
<p><b>To unlock it's content, please send a request to <a href="mailto:support@mydomain.com">support@mydomain.com</a></b></p>
</center>
</body></html>

```
I'm waiting the confirmation and 'green light' of our network team to have that port open and I'll try it again.
Thank you !

---

