---
title: "Rubygems installation problem"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by mdavis on 2006-09-04
I apologize if this has been posted before; from the quick scan of searches I pulled it up it doesn't appear that it has.

I've tried to install Ruby and Rubygems before on my Ubuntu installation running on VMWare, but I kept running into difficulties, so I started fresh today and documented everything I did in OneNote. My ultimate goal is to get SimpleTicket up and running. Hopefully someone can look at my configuration and tell me why I keep having trouble with gems. Thank you.

Regards,

Mark Davis.

10:45 AM - Too many problems getting Rails to work; performing clean install of Ubuntu 6.06 LTS.
11:10 AM - account: mdavis, password: markistheman
11:41 AM - Reinstalled successful. Restarting Virtual Machine.
12:01 PM - Applying patches:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
12:04 PM - Installing SSH:
sudo apt-get install ssh
12:06 PM - Installing mysql server:
sudo apt-get install mysql-server
sudo mysqladmin -u root password markistheman
12:09 PM - Creating simpleticket database:
sudo mysqladmin -p create simpleticket
12:11 PM - Getting sources for compiling process:
sudo apt-get install build-essential
12:13 PM - Stopping.
3:03 PM - Back home. Adding repositories (see ubuntuguide.org):
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
3:19 PM - Installing checkinstall:
sudo apt-get install checkinstall
3:21 PM - Preparing to compile ruby:
sudo apt-get install libzlib-ruby libyaml-ruby libdrb-ruby liberb-ruby zlib1g-dev libopenssl-ruby
3:30 PM - Downloaded latest version of Ruby from [www.rubyforge.org/projects/ruby](www.rubyforge.org/projects/ruby)
tar -zxvf ruby-1.8.5
./configure
3:32 PM - uncommenting zlib and stringio lines (remove the #) from the Setup file located at ~ruby-1.8.5/ext
sudo nano Setup
3:35 PM - Compiling ruby:
Ruby-1.8.5/make
/make test
/sudo checkinstall
3:39 PM - Installation failed when I tried to do checkinstall command. Will reboot virtual machine.
3:50 PM - Received same error.
3:57 PM - Didn't perform "sudo make install" command BEFORE sudo checkinstall. Works now. The proper command order seems to be:
./configure
sudo make
sudo make test
sudo make install
sudo checkinstall
4:07 PM - Receiving error when trying to install rubygems:
Downloaded rubygems from rubyforge
sudo ruby setup.rb
5:02 PM - Received error. Logging error for troubleshooting.

mdavis@mdavis-desktop:~/rubygems-0.9.0$ sudo ruby setup.rb
---> bin
<--- bin
---> lib
---> lib/rbconfig
<--- lib/rbconfig
---> lib/rubygems
<--- lib/rubygems
<--- lib
---> bin
<--- bin
---> lib
---> lib/rbconfig
<--- lib/rbconfig
---> lib/rubygems
<--- lib/rubygems
<--- lib
rm -f InstalledFiles
---> bin
mkdir -p /usr/local/bin/
install gem /usr/local/bin/
install gem_mirror /usr/local/bin/
install gem_server /usr/local/bin/
install gemlock /usr/local/bin/
install gemri /usr/local/bin/
install gemwhich /usr/local/bin/
install index_gem_repository.rb /usr/local/bin/
install update_rubygems /usr/local/bin/
<--- bin
---> lib
mkdir -p /usr/local/lib/ruby/site_ruby/1.8/
install gemconfigure.rb /usr/local/lib/ruby/site_ruby/1.8/
install rubygems.rb /usr/local/lib/ruby/site_ruby/1.8/
install ubygems.rb /usr/local/lib/ruby/site_ruby/1.8/
---> lib/rbconfig
mkdir -p /usr/local/lib/ruby/site_ruby/1.8/rbconfig
install datadir.rb /usr/local/lib/ruby/site_ruby/1.8/rbconfig
<--- lib/rbconfig
---> lib/rubygems
mkdir -p /usr/local/lib/ruby/site_ruby/1.8/rubygems
install builder.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install cmd_manager.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install command.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install config_file.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install custom_require.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install dependency_list.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install doc_manager.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install format.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install gem_commands.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install gem_openssl.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install gem_runner.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install incremental_fetcher.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install installer.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install loadpath_manager.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install old_format.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install open-uri.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install package.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install remote_installer.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install rubygems_version.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install security.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install source_index.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install specification.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install timer.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install user_interaction.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install validator.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install version.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
<--- lib/rubygems
<--- lib

As of RubyGems 0.8.0, library stubs are no longer needed.
Searching $LOAD_PATH for stubs to optionally delete (may take a while)...
...done.
No library stubs found.

/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in
`gem_original_require': no such file to load -- zlib (LoadError)
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in
`require'
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems/package.rb:9
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in
`gem_original_require'
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in
`require'
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems/builder.rb:7
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in
`gem_original_require'
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in
`require'
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:93:in `manage_gems'
       from /home/mdavis/rubygems-0.9.0/./post-install.rb:70:in
`install_sources'
       from /home/mdavis/rubygems-0.9.0/./post-install.rb:81:in `try_run_hook'
       from setup.rb:577:in `run_hook'
       from setup.rb:1315:in `exec_task_traverse'
       from setup.rb:1168:in `exec_install'
       from setup.rb:887:in `exec_install'
       from setup.rb:705:in `invoke'
       from setup.rb:674:in `invoke'
       from setup.rb:1352


ERROR #2:

mdavis@mdavis-desktop:~$ gem
/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in
`gem_original_require': no such file to load -- zlib (LoadError)
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in
`require'
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems/package.rb:9
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in
`gem_original_require'
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in
`require'
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems/builder.rb:7
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in
`gem_original_require'
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in
`require'
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:93:in `manage_gems'
       from /usr/local/bin/gem:10

---

### Post by mssever on 2006-09-04
I'm not much of an expert with ruby, but is there a reason you compiled ruby yourself instead of using sudo apt-get install ruby?

I'm wondering if you have a bad install of ruby. Here's what I just did:
```
~/bin/install:$ sudo apt-get install ruby # Actually, I'd already done that
~/bin/install:$ wget http://rubyforge.org/frs/download.php/11289/rubygems-0.9.0.tgz
~/bin/install:$ tar -xzvf rubygems-0.9.0.tgz
~/bin/install:$ cd rubygems-0.9.0
~/bin/install/rubygems-0.9.0:$ sudo ruby setup.rb
[SIZE=1][COLOR=Gray]---> bin
<--- bin
---> lib
---> lib/rbconfig
<--- lib/rbconfig
---> lib/rubygems
<--- lib/rubygems
<--- lib
---> bin
<--- bin
---> lib
---> lib/rbconfig
<--- lib/rbconfig
---> lib/rubygems
<--- lib/rubygems
<--- lib
rm -f InstalledFiles
---> bin
mkdir -p /usr/bin/
install gem /usr/bin/
install gem_mirror /usr/bin/
install gem_server /usr/bin/
install gemlock /usr/bin/
install gemri /usr/bin/
install gemwhich /usr/bin/
install index_gem_repository.rb /usr/bin/
install update_rubygems /usr/bin/
<--- bin
---> lib
mkdir -p /usr/local/lib/site_ruby/1.8/
install gemconfigure.rb /usr/local/lib/site_ruby/1.8/
install rubygems.rb /usr/local/lib/site_ruby/1.8/
install ubygems.rb /usr/local/lib/site_ruby/1.8/
---> lib/rbconfig
mkdir -p /usr/local/lib/site_ruby/1.8/rbconfig
install datadir.rb /usr/local/lib/site_ruby/1.8/rbconfig
<--- lib/rbconfig
---> lib/rubygems
mkdir -p /usr/local/lib/site_ruby/1.8/rubygems
install builder.rb /usr/local/lib/site_ruby/1.8/rubygems
install cmd_manager.rb /usr/local/lib/site_ruby/1.8/rubygems
install command.rb /usr/local/lib/site_ruby/1.8/rubygems
install config_file.rb /usr/local/lib/site_ruby/1.8/rubygems
install custom_require.rb /usr/local/lib/site_ruby/1.8/rubygems
install dependency_list.rb /usr/local/lib/site_ruby/1.8/rubygems
install doc_manager.rb /usr/local/lib/site_ruby/1.8/rubygems
install format.rb /usr/local/lib/site_ruby/1.8/rubygems
install gem_commands.rb /usr/local/lib/site_ruby/1.8/rubygems
install gem_openssl.rb /usr/local/lib/site_ruby/1.8/rubygems
install gem_runner.rb /usr/local/lib/site_ruby/1.8/rubygems
install incremental_fetcher.rb /usr/local/lib/site_ruby/1.8/rubygems
install installer.rb /usr/local/lib/site_ruby/1.8/rubygems
install loadpath_manager.rb /usr/local/lib/site_ruby/1.8/rubygems
install old_format.rb /usr/local/lib/site_ruby/1.8/rubygems
install open-uri.rb /usr/local/lib/site_ruby/1.8/rubygems
install package.rb /usr/local/lib/site_ruby/1.8/rubygems
install remote_installer.rb /usr/local/lib/site_ruby/1.8/rubygems
install rubygems_version.rb /usr/local/lib/site_ruby/1.8/rubygems
install security.rb /usr/local/lib/site_ruby/1.8/rubygems
install source_index.rb /usr/local/lib/site_ruby/1.8/rubygems
install specification.rb /usr/local/lib/site_ruby/1.8/rubygems
install timer.rb /usr/local/lib/site_ruby/1.8/rubygems
install user_interaction.rb /usr/local/lib/site_ruby/1.8/rubygems
install validator.rb /usr/local/lib/site_ruby/1.8/rubygems
install version.rb /usr/local/lib/site_ruby/1.8/rubygems
<--- lib/rubygems
<--- lib

As of RubyGems 0.8.0, library stubs are no longer needed.
Searching $LOAD_PATH for stubs to optionally delete (may take a while)...
...done.
No library stubs found.

  Successfully built RubyGem
  Name: sources
  Version: 0.0.1
  File: sources-0.0.1.gem[/COLOR][/SIZE]
~/bin/install/rubygems-0.9.0:$ gem[SIZE=1][COLOR=Gray]
RubyGems is a sophisticated package manager for Ruby.  This is a
basic help message containing pointers to more information.

  Usage:
    gem -h/--help
    gem -v/--version
    gem command [arguments...] [options...]

  Examples:
    gem install rake
    gem list --local
    gem build package.gemspec
    gem help install

  Further help:
    gem help commands            list all 'gem' commands
    gem help examples            show some examples of usage
    gem help <COMMAND>           show help on COMMAND
                                   (e.g. 'gem help install')
  Further information:
    http://rubygems.rubyforge.org[/COLOR][/SIZE]
```

---

### Post by mdavis on 2006-09-04
> I'm not much of an expert with ruby, but is there a reason you compiled ruby yourself instead of using sudo apt-get install ruby?

I was basing what I did according to these instructions:

[http://fo64.com/articles/2005/10/20/rails-on-breezy](http://fo64.com/articles/2005/10/20/rails-on-breezy)

[http://www.urbanpuddle.com/articles/2006/06/10/install-ruby-rails-on-ubuntu-dapper-drake](http://www.urbanpuddle.com/articles/2006/06/10/install-ruby-rails-on-ubuntu-dapper-drake)

[http://benshead.learningblogs.org/2006/02/21/installing-simpleticket-on-ubuntu-510/](http://benshead.learningblogs.org/2006/02/21/installing-simpleticket-on-ubuntu-510/)

[http://ubuntuforums.org/showthread.php?t=191701&highlight=sudo+ruby+setup.rb](http://ubuntuforums.org/showthread.php?t=191701&highlight=sudo+ruby+setup.rb)

Here is what I've now done and the (new?) error I'm getting now.

```
mdavis@mdavis-desktop:~$ sudo apt-get install ruby
Password:
Reading package lists... Done
Building dependency tree... Done
ruby is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I performed your command and of course it told me that I already had ruby installed, so I removed it.

```
mdavis@mdavis-desktop:~$ sudo apt-get remove ruby
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
 ruby
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 2408kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 73135 files and directories currently installed.)
Removing ruby ...
dpkg - warning: while removing ruby, directory
`/usr/local/lib/ruby/1.8/i686-linux' not empty so not removed.
dpkg - warning: while removing ruby, directory
`/usr/local/lib/ruby/1.8' not empty so not removed.
dpkg - warning: while removing ruby, directory `/usr/local/lib/ruby'
not empty so not removed.
dpkg - warning: while removing ruby, directory `/usr/local/lib' not
empty so not removed.
dpkg - warning: while removing ruby, directory `/usr/local/bin' not
empty so not removed.
dpkg - warning: while removing ruby, directory `/usr/local' not empty
so not removed.
```

So then I installed Ruby again using apt-get:

```
mdavis@mdavis-desktop:~$ sudo apt-get install ruby
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
 ruby
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.0kB of archives.
After unpacking 98.3kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com dapper/main ruby 1.8.2-1 [19.0kB]
Fetched 19.0kB in 1s (13.3kB/s)
Selecting previously deselected package ruby.
(Reading database ... 73063 files and directories currently installed.)
Unpacking ruby (from .../archives/ruby_1.8.2-1_all.deb) ...
Setting up ruby (1.8.2-1) ...
```

Then I tried to install Rubygems again:

```
mdavis@mdavis-desktop:~$ cd rubygems-0.9.0/
mdavis@mdavis-desktop:~/rubygems-0.9.0$ sudo ruby setup.rb
---> bin
<--- bin
---> lib
---> lib/rbconfig
<--- lib/rbconfig
---> lib/rubygems
<--- lib/rubygems
<--- lib
---> bin
<--- bin
---> lib
---> lib/rbconfig
<--- lib/rbconfig
---> lib/rubygems
<--- lib/rubygems
<--- lib
rm -f InstalledFiles
---> bin
mkdir -p /usr/local/bin/
install gem /usr/local/bin/
install gem_mirror /usr/local/bin/
install gem_server /usr/local/bin/
install gemlock /usr/local/bin/
install gemri /usr/local/bin/
install gemwhich /usr/local/bin/
install index_gem_repository.rb /usr/local/bin/
install update_rubygems /usr/local/bin/
<--- bin
---> lib
mkdir -p /usr/local/lib/ruby/site_ruby/1.8/
install gemconfigure.rb /usr/local/lib/ruby/site_ruby/1.8/
install rubygems.rb /usr/local/lib/ruby/site_ruby/1.8/
install ubygems.rb /usr/local/lib/ruby/site_ruby/1.8/
---> lib/rbconfig
mkdir -p /usr/local/lib/ruby/site_ruby/1.8/rbconfig
install datadir.rb /usr/local/lib/ruby/site_ruby/1.8/rbconfig
<--- lib/rbconfig
---> lib/rubygems
mkdir -p /usr/local/lib/ruby/site_ruby/1.8/rubygems
install builder.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install cmd_manager.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install command.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install config_file.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install custom_require.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install dependency_list.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install doc_manager.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install format.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install gem_commands.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install gem_openssl.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install gem_runner.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install incremental_fetcher.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install installer.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install loadpath_manager.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install old_format.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install open-uri.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install package.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install remote_installer.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install rubygems_version.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install security.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install source_index.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install specification.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install timer.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install user_interaction.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install validator.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install version.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
<--- lib/rubygems
<--- lib

As of RubyGems 0.8.0, library stubs are no longer needed.
Searching $LOAD_PATH for stubs to optionally delete (may take a while)...
...done.
No library stubs found.

/usr/local/lib/ruby/site_ruby/1.8/rubygems/source_index.rb:10:in
`require': no such file to load -- digest/sha2 (LoadError)
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems/source_index.rb:10
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:461:in `require'
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:461
       from /home/mdavis/rubygems-0.9.0/./post-install.rb:69:in `require'
       from /home/mdavis/rubygems-0.9.0/./post-install.rb:69:in
`install_sources'
       from /home/mdavis/rubygems-0.9.0/./post-install.rb:81:in `try_run_hook'
       from setup.rb:577:in `run_hook'
       from setup.rb:1315:in `exec_task_traverse'
       from setup.rb:1168:in `exec_install'
       from setup.rb:887:in `exec_install'
       from setup.rb:705:in `invoke'
       from setup.rb:674:in `invoke'
       from setup.rb:1352
```

And of course the gem command still will not work:

```
mdavis@mdavis-desktop:~/rubygems-0.9.0$ gem
/usr/local/lib/ruby/site_ruby/1.8/rubygems/source_index.rb:10:in
`require': no such file to load -- digest/sha2 (LoadError)
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems/source_index.rb:10
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:461:in `require'
       from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:461
       from /usr/local/bin/gem:9:in `require'
       from /usr/local/bin/gem:9
```

---

### Post by mdavis on 2006-09-04
A small update: Using the whereis ruby command, I manually went in and deleted all folders associated with ruby, and then used the sudo apt-get install ruby -y command. Now I get a new error when I try to install gems.

```
mdavis@mdavis-desktop:~/rubygems-0.9.0$ sudo ruby setup.rb
setup.rb:52:in `require': no such file to load -- rbconfig (LoadError)
       from setup.rb:52
```

---

### Post by mssever on 2006-09-04
I'm not sure what your problem is, but I think you should completely remove ruby and start over. Your ystem keeps complaining about /usr/local/lib/ruby/site_ruby/1.8/whatever, which doesn't exist on my system. I've got /usr/local/lib/site_ruby/1.8/whatever.

Also, the whereis command only locates certain files--stuff in your PATH and man path, if I recall correctly. The way I would completely remove ruby would be to firt open up Synaptic (I think this is easier than the command line in this case) and do a search for ruby. Mark everything that comes up about ruby for **complete** removal--keep a list of ehat you're removing if you want to make sure to get everything back. Apply changes and exit.

Next, run ```
sudo updatedb && locate ruby | less
``` This will find any ruby-related stuff on your system that needs to be manually deleted. You might also try ```
locate gem | less
``` 
BTW, updatedb updates the search index. It takes a bit of time to complete, but you should run it before using locate if you've changed stuff on your disk. I run updatedb as a cron job about three times/week, then I only need to manually run it if I've recently made changes that could impact the results.

Once you've cleaned ruby and ruby gems from your machine, try to reinstall. If that doesn't work, then I'm completely baffled.

---

### Post by mdavis on 2006-09-05
I started over with a clean installation, and before I did anything else I just did a regular install of ruby, and then gems worked fine. I guess those guides are a bit faulty.

---

### Post by mssever on 2006-09-05
Yes, those guides... I never looked at them until now, and they make the process unnecessarily difficult. I guess the lesson here is to prefer to use stuff from the repositories if at all possible--over files from other soures or compiling yourself. There's no need to install gem just to get rails; rails is available from Synaptic. Plus, if you install the package ruby, it pulls in all its dependencies automatically. If you use the repository instead of gem, you know two things: first, there is only one place to go for updates; second, you know that the packages are all built to work on Ubuntu (remember, some of your files were trying to use a directory path that doesn't exist--it probably does on some distros).

---

### Post by mdavis on 2006-09-07
The weird thing is that I was able to get it working once I installed rails from normal repositories, and then I could install gem with no problem. But gem would still give me errors when I tried to use it to install feedtools, so I had gem reinstall rails. From that point on I could use gem appropriately, and create the sql server with Webrick for Simpleticket. However, I'm running into some problems with Simpleticket not giving me the appropriate output when I connect to it via HTTP, but that may be operator error at this point.

---

### Post by leemckusic on 2006-09-07
Hello, I went through the same Ruby installation problem.

It appears to me the problem with installing Ruby on a Ubuntu system has these parts:

The version I saw from Ubuntu a few weeks ago was 1.8.3, which is an intermediate version. The rails gem will not install under Ruby 1.8.3.

Thus you need to compile and install Ruby from the official source, Then get Gems and compile and install from official source.

Then doing Gem Install of rails results in an error because one file is missing. Using the Ubuntu ruby package, you copy that file from the location used by Ubuntu to the location expected by the compiled and installed Ruby. That copy is quoted in my book review below.


At the end of this book review I tell the steps to install Ruby and Ruby on Rails and Rubygems:

[http://www.penlug.org/twiki/bin/view/Main/LinuxBookReviewsAgileWebDevelopmentwithRails](http://www.penlug.org/twiki/bin/view/Main/LinuxBookReviewsAgileWebDevelopmentwithRails)

---

### Post by mssever on 2006-09-07
> **leemckusic said:**
> Hello, I went through the same Ruby installation problem.

It appears to me the problem with installing Ruby on a Ubuntu system has these parts:

The version I saw from Ubuntu a few weeks ago was 1.8.3, which is an intermediate version. The rails gem will not install under Ruby 1.8.3.

Thus you need to compile and install Ruby from the official source, Then get Gems and compile and install from official source.

Then doing Gem Install of rails results in an error because one file is missing. Using the Ubuntu ruby package, you copy that file from the location used by Ubuntu to the location expected by the compiled and installed Ruby. That copy is quoted in my book review below.


At the end of this book review I tell the steps to install Ruby and Ruby on Rails and Rubygems:

[http://www.penlug.org/twiki/bin/view/Main/LinuxBookReviewsAgileWebDevelopmentwithRails](http://www.penlug.org/twiki/bin/view/Main/LinuxBookReviewsAgileWebDevelopmentwithRails)

Actually, you're making this much more difficult than it needs to be. If your goal is simply rails, you don't need gems. Doing ```
sudo apt-get install ruby rails
``` will get you everything you need. You don't need to compile from source or anything like that. If you need gems, then the only extra step to install it is: 
```
~/bin/install:$ wget http://rubyforge.org/frs/download.php/11289/rubygems-0.9.0.tgz
~/bin/install:$ tar -xzvf rubygems-0.9.0.tgz
~/bin/install:$ cd rubygems-0.9.0
~/bin/install/rubygems-0.9.0:$ sudo ruby setup.rb
```

BTW: The Ruby version on my system is 1.8.4--not 1.8.3, and I got it from the repos.

---

### Post by niravdani on 2006-09-24
So the trade-off is to install what ubuntu has to offer. What if I have ruby 1.8.5 from the source and would want to install latest Rails using Gem (all from source).

---

