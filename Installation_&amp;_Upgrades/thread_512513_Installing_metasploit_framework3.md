---
title: "Installing metasploit framework3"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by erealz on 2007-07-29
hey eveyone first let me start by saying im not new to linux but im by no means a guru. im very much into security and pentesting. im trying to install metasploit framework3. all required packages are installed no problem.

my question is according to the install instructions 
> To perform a system-wide installation, we recommend that you copy the en-
tire Framework directory into a globally accessible location (/usr/local/msf)
[B]and then create [symbolic links]("http://en.wikipedia.org/wiki/Symbolic_link") from the msf* applications to a directory in
the system path (/usr/local/bin)[/B]. User-specific modules can be placed into
HOME/.msf3/modules directory. The structure of this directory should mirror
that of the global modules directory found in the framework distribution.



now this is the part ware i sound like a newb. how the hell do i create a "symbolic links"?! 

here what i have done so far...:
1)extract the msf to my desktop
2)copy the entire msf package to the /usr/local dir.
3)then copyed all the msf executables to /usr/local/bin
4)then coped the modules to it own dir in /home/.msf3 hidden dir

i then try and run any of the user interfaces and i get this

$ msfconsole
/usr/local/bin/msfconsole:10:in `require': no such file to load -- rex (LoadError)
        from /usr/local/bin/msfconsole:10

ware am i going wrong im know im misunderstanding something:confused: plz help

ps: i really wish metasploit framework came in a .deb package for ease of install. i would like to create one my self to make easy for everyone else to install if some one can also point to where i can learn how to do this that would be sweet to.

---

### Post by erealz on 2007-07-29
as easy to install as extracting the files my ***!! the only way i can run is to keep a cop of the entires msf file in my home dir and executing them from within the dir.

---

### Post by talby on 2007-07-30
there is some assistance from the [metasploit framwork support page (link)](http://framework.metasploit.com/msf/support), cllicking on [Installing Metasploit 3 on Ubuntu/Kubuntu Linux (link)]("http://metasploit.com/dev/trac/wiki/Metasploit3/InstallUbuntu") shows you how to install the dependencies (Ruby on Rails w/ ssl support).

The rubygems link is broken try [getting the latest version here (link)]("http://rubyforge.org/frs/?group_id=126&release_id=11889") (I used REL_0_9_4).  Check out ["Installing Ruby on Rails on Ubuntu Dapper or Edgy" @howtogeek.com (link) ]("http://www.howtogeek.com/howto/ubuntu/installing-ruby-on-rails-on-ubuntu-dapper-or-edgy/") this is a good overview on installing Ruby on Rails and testing.

In a nutshell:
1 - [Enable the "universe" repository (ubuntuguide:feisty link)]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

2 - Install Ruby and needed dependencies from the universe repository by running these commands:
```
sudo apt-get install ruby libruby rdoc
sudo apt-get install libyaml-ruby
sudo apt-get install libzlib-ruby
sudo apt-get install libopenssl-ruby
sudo apt-get install libdl-ruby
sudo apt-get install libreadline-ruby
sudo apt-get install libiconv-ruby
```

3 - install the latest "rubygems" and "rails" package by running these commands:
```
sudo su -
mkdir /opt/ruby
cd /opt/ruby
wget http://rubyforge.org/frs/download.php/20989/rubygems-0.9.4.tgz
tar xf rubygems-0.9.4.tgz
cd rubygems-0.9.4
ruby setup.rb 
gem install rails &#8211;include-dependencies
```
To test it, start another session as your regular user and run these commands:
```
rails testapp
cd testapp
./script/server
```
you should see this output:
```
=> Booting WEBrick&#8230;
=> Rails application started on http://0.0.0.0:3000
=> Ctrl-C to shutdown server; call with &#8211;help for options
[2006-12-07 05:28:37] INFO WEBrick 1.3.1
[2006-12-07 05:28:37] INFO ruby 1.8.4 (2005-12-24) [i486-linux]
[2006-12-07 05:28:37] INFO WEBrick::HTTPServer#start: pid=6687 port=3000
```
Test it out by clicking on this:
[_http://localhost:3000_]("http://localhost:3000")
If you see a web page, you're good to go.  Hit "CTRL-C" to end the test server.

Now you are finally ready to install the metasploit framework!  When I installed it, I put it in /opt (since all non-OS apps that are not part of the repository base should go there) I did this:

```
sudo su -
mkdir /opt/metasploit
cd /opt/metasploit
tar xzf /download-dir-here/framework-3.0.tar.gz
find /opt/metasploit/framework-3.0/ -maxdepth 1 -type f ! -name README -print -exec ln -s {} /usr/local/bin \;
```

The last find command links the executables to /usr/loca/bin (mentioned in the starting thread)

Let try it...
```
$ msfconsole

                                  _
                                 | |      o
 _  _  _    _ _|_  __,   ,    _  | |  __    _|_
/ |/ |/ |  |/  |  /  |  / \_|/ \_|/  /  \_|  |
  |  |  |_/|__/|_/\_/|_/ \/ |__/ |__/\__/ |_/|_/
                           /|
                           \|


       =[ msf v3.0
+ -- --=[ 176 exploits - 104 payloads
+ -- --=[ 17 encoders - 5 nops
       =[ 30 aux

msf > 
```

It's working!  woohoo!

I had to edit /opt/metasploit/framework-3.0/data/msfweb/config/environment.rb to reflect the rails version "1.2.3" to get the msfweb app working...

```
$ msfweb

[*] Starting msfweb v3.0 on http://127.0.0.1:55555/

=> Booting WEBrick...
=> Rails application started on http://127.0.0.1:55555
=> Ctrl-C to shutdown server; call with --help for options
[2007-08-03 10:22:49] INFO  WEBrick 1.3.1
[2007-08-03 10:22:49] INFO  ruby 1.8.4 (2005-12-24) [i486-linux]
[2007-08-03 10:22:49] INFO  WEBrick::HTTPServer#start: pid=28997 port=55555
```

Open firefox, put in "http://127.0.0.1:55555" and you should see the metasploit web front end!

Hope this helps, cheers

---

### Post by tsunami99 on 2007-08-02
Thanks Talby 

I got to step three and had problems installing rails

Step 
3 - install the latest "rubygems" and "rails" package by running these commands:

Code:
sudo su -
mkdir /opt/ruby
cd /opt/ruby
wget [http://rubyforge.org/frs/download.php/20989/rubygems-0.9.4.tgz](http://rubyforge.org/frs/download.php/20989/rubygems-0.9.4.tgz)
tar xf rubygems-0.9.4.tgz
cd rubygems-0.9.4
ruby setup.rb 
gem install rails –include-dependencies

when I ran install rails -include-dependencies it could not get past he proxy server so I set the environment property HTTP_PROXY by adding the following line  to ~/.bashrc

export HTTP_PROXY=http://your_proxy_host:proxy_port

once I did this it failed to connect the first time but on the second attempt it did install. However when i opened another console to confirm install I using rails testapp I received an error stating rails was not installed. So I ran 

sudo apt-get install rails, which seemed to install o.k. To test this I ran  

Code:
rails testapp
cd testapp
./script/server

and I did see this output:

Code:
=> Booting WEBrick…
=> Rails application started on [http://0.0.0.0:3000](http://0.0.0.0:3000)
=> Ctrl-C to shutdown server; call with –help for options
[2006-12-07 05:28:37] INFO WEBrick 1.3.1
[2006-12-07 05:28:37] INFO ruby 1.8.4 (2005-12-24) [i486-linux]
[2006-12-07 05:28:37] INFO WEBrick::HTTPServer#start: pid=6687 port=3000

At which point I could browse to ruby ralis page at [http://localhost:3000/](http://localhost:3000/)

From your explanation at this point you need to create a symbolic link to the /usr/local/bin folder

"When I installed it, I put it in /opt (since all non-OS apps that are not part of the repository base should go there) I did this:


Code:
sudo su -
mkdir /opt/metasploit
cd /opt/metasploit
tar xzf /download-dir-here/framework-3.0.tar.gz
find /opt/metasploit/framework-3.0/ -maxdepth 1 -type f ! -name README -print -exec ln -s {} /usr/local/bin \;The last find command links the executables to /usr/loca/bin (mentioned in the starting thread)"

however, when using ln to create the symbolic link i still could not launch msfconsole. I am still receiving the command was not found.  

any further help would be appreciated:)

---

### Post by Drzymalski on 2007-08-02
I followed the directions posted above and i get this error with msfweb

User@Ubuntu7.10:~$ msfweb

[*] Starting msfweb v3.0 on [http://127.0.0.1:55555/](http://127.0.0.1:55555/)

Cannot find gem for Rails ~>1.2.2.0:
    Install the missing gem with 'gem install -v=1.2.2 rails', or
    change environment.rb to define RAILS_GEM_VERSION with your desired version.

---

### Post by tsunami99 on 2007-08-02
Checking the symbolic links with ls -l revealed the symbolic link was incorrect. I had to remove all symbolic links and created them manually one by one from /usr/local/bin to be sure.

ln -s /opt/metatsploit/framework-3.0/msfconsole msfconsole
ln -s /opt/metatsploit/framework-3.0/msfweb msfweb
ln -s /opt/metatsploit/framework-3.0/msfd msfd
ln -s /opt/metatsploit/framework-3.0/msfcli msfcli
ln -s /opt/metatsploit/framework-3.0/msfencode msfencode
ln -s /opt/metatsploit/framework-3.0/msfgui msfgui
ln -s /opt/metatsploit/framework-3.0/msfopcode msfopcode
ln -s /opt/metatsploit/framework-3.0/msfpayload msfpayload
ln -s /opt/metatsploit/framework-3.0/msfpescan msfpescan

then check the symbolic links again with ls-l to make sure everything is o.k.

I was then able to launch msfconsole

---

### Post by tsunami99 on 2007-08-02
I also got the following message when running msfweb

User@Ubuntu7.10:~$ msfweb
[*] Starting msfweb v3.0 on [http://127.0.0.1:55555/](http://127.0.0.1:55555/)

Cannot find gem for Rails ~>1.2.2.0:
Install the missing gem with 'gem install -v=1.2.2 rails', or
change environment.rb to define RAILS_GEM_VERSION with your desired version.

I changed the enviroment.rb file to reflect the version of rails installed, which is 1.2.3, then I received the same error message reffering to that version 1.2.3.

---

### Post by tsunami99 on 2007-08-03
I also tried to update metasploit using svn  update /opt/metasploit/framework-3.0 and this is not working either; error message is:

svn: Propfind request failed on /opt/metasploit/framework-3.0/

---

### Post by talby on 2007-08-03
> **tsunami99 said:**
> I also got the following message when running msfweb

User@Ubuntu7.10:~$ msfweb
[*] Starting msfweb v3.0 on [http://127.0.0.1:55555/](http://127.0.0.1:55555/)

Cannot find gem for Rails ~>1.2.2.0:
Install the missing gem with 'gem install -v=1.2.2 rails', or
change environment.rb to define RAILS_GEM_VERSION with your desired version.

I changed the enviroment.rb file to reflect the version of rails installed, which is 1.2.3, then I received the same error message reffering to that version 1.2.3.

I tried the same, running msfweb I got the same "1.2.2 error" then edited /opt/metasploit/framework-3.0/data/msfweb/config/environment.rb to "1.2.3" and it's working...

```
$ msfweb

[*] Starting msfweb v3.0 on http://127.0.0.1:55555/

=> Booting WEBrick...
=> Rails application started on http://127.0.0.1:55555
=> Ctrl-C to shutdown server; call with --help for options
[2007-08-03 10:22:49] INFO  WEBrick 1.3.1
[2007-08-03 10:22:49] INFO  ruby 1.8.4 (2005-12-24) [i486-linux]
[2007-08-03 10:22:49] INFO  WEBrick::HTTPServer#start: pid=28997 port=55555
```

Hey this is getting to be a pretty good metasploit howto, I'll add this to my original post :)

---

### Post by tsunami99 on 2007-08-06
Glad you have it working :) but I still have a problem:(

When testing to see if rails is installed using the following steps

Code:
rails testapp
cd testapp
./script/server

It builds an environment.rb file in the opt/ruby/rubygems-0.9.4/testapp/config folder, why is it referring to version 1.2.1 here? 

I tried editing /opt/metasploit/framework-3.0/data/msfweb/config/environment.rb to "1.2.1" instead of 1.2.3 and it still doesn't work. 

Talby can you provide me with the version you have  used in the ......testapp/config/environement.rb file. Perhaps the version of rails I have is screwed. I may need to start over :(. 

Also can you use svn update to update metasploit? I think I am having an issue because I am behind a proxy and firewall (which I have no control over).

---

### Post by tsunami99 on 2007-08-06
I edited the /opt/metasploit/framework-3.0/data/msfweb/config/environment.rb file again using 1.2.3 as the version. Then I reinstalled rails using gem install -v=1.2.3 rails and said yes to install all dependencies individually, and now it's alive :). Now all I have to do is get these updates.

---

### Post by phydaux on 2007-11-03
I have installed version 1.2.4 from the repositories, and encountered similar problems.  I found that **gem install -v=1.2.4 rails** did NOT work, but **gem install -v=1.2.4.0 ** DID work.

---

### Post by Mr_Mischif on 2007-12-07
Sorry to dredge up an old thread, but I'm having a problem getting the web interface to work. I've gotten all the required dependencies for it, and I can start it, but when I travel to the address, it gives me a "500 Internal Server Error" error. What do I do about it?

---

### Post by jopusbob on 2007-12-31
this is the out put that i am getting could someone help???

mine@Seminator5000:~/testapp$ msfweb

[*] Starting msfweb v3.0 on [http://127.0.0.1:55555/](http://127.0.0.1:55555/)

=> Booting WEBrick...
Rails Error: Unable to access log file. Please ensure that /opt/metasploit/framework-3.0/data/msfweb/log/production.log exists and is chmod 0666. The log level has been raised to WARN and the output directed to STDERR until the problem is fixed.
/opt/metasploit/framework-3.0/lib/rex/logging/sinks/flatfile.rb:20:in `initialize': Permission denied - /home/mine/.msf3/logs/msfweb.log (Errno::EACCES)
        from /opt/metasploit/framework-3.0/lib/rex/logging/sinks/flatfile.rb:20:in `new'
        from /opt/metasploit/framework-3.0/lib/rex/logging/sinks/flatfile.rb:20:in `initialize'
        from /opt/metasploit/framework-3.0/lib/msf/base/logging.rb:39:in `new'
        from /opt/metasploit/framework-3.0/lib/msf/base/logging.rb:39:in `enable_log_source'
        from ./script/../config/../config/../../../lib/msf/ui/web/driver.rb:153:in `initialize_logging'
        from ./script/../config/../config/../../../lib/msf/ui/web/driver.rb:49:in `initialize'
        from ./script/../config/../config/environment.rb:24:in `new'
        from ./script/../config/../config/environment.rb:24
         ... 13 levels...
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from ./script/server:3
        from /usr/local/bin/msfweb:82:in `load'
        from /usr/local/bin/msfweb:82

---

### Post by The Tronyx on 2007-12-31
> **Mr_Mischif said:**
> Sorry to dredge up an old thread, but I'm having a problem getting the web interface to work. I've gotten all the required dependencies for it, and I can start it, but when I travel to the address, it gives me a "500 Internal Server Error" error. What do I do about it?

I too am having the same problem.

Jopusbob, try running sudo gem install rails &#8211;include-dependencies again.

---

### Post by Furality on 2008-01-19
Ive tried everything i know to install this, when i try to do what i want, ill show you what ive done.


root@reid-laptop:~# msfconsole 

                 o                       8         o   o
                 8                       8             8
ooYoYo. .oPYo.  o8P .oPYo. .oPYo. .oPYo. 8 .oPYo. o8  o8P
8' 8  8 8oooo8   8  .oooo8 Yb..   8    8 8 8    8  8   8
8  8  8 8.       8  8    8   'Yb. 8    8 8 8    8  8   8
8  8  8 `Yooo'   8  `YooP8 `YooP' 8YooP' 8 `YooP'  8   8
..:..:..:.....:::..::.....::.....:8.....:..:.....::..::..:
::::::::::::::::::::::::::::::::::8:::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::::::::::::


       =[ msf v3.0
+ -- --=[ 176 exploits - 104 payloads
+ -- --=[ 17 encoders - 5 nops
       =[ 30 aux

msf > load db_sqlite3
[*] Successfully loaded plugin: db_sqlite3
msf > db_create 
[-] Error while running command db_create: This plugin failed to load:  Failed to connect to the database

Call stack:
/opt/metasploit/framework-3.0/plugins/db_sqlite3.rb:89:in `cmd_db_create'
/opt/metasploit/framework-3.0/lib/rex/ui/text/dispatcher_shell.rb:230:in `send'
/opt/metasploit/framework-3.0/lib/rex/ui/text/dispatcher_shell.rb:230:in `run_command'
/opt/metasploit/framework-3.0/lib/rex/ui/text/dispatcher_shell.rb:196:in `run_single'
/opt/metasploit/framework-3.0/lib/rex/ui/text/dispatcher_shell.rb:191:in `each'
/opt/metasploit/framework-3.0/lib/rex/ui/text/dispatcher_shell.rb:191:in `run_single'
/opt/metasploit/framework-3.0/lib/rex/ui/text/shell.rb:120:in `run'
/usr/local/bin/msfconsole:77


Im at a loss at what to do,

---

### Post by The Tronyx on 2008-01-28
looks like you didn't start msfweb, the internal server.

---

