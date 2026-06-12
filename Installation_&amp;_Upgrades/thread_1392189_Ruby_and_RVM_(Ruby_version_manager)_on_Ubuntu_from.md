---
title: "Ruby and RVM (Ruby version manager) on Ubuntu from source"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by dsjbirch on 2010-01-27
Hope this helps someone, I've just done a fresh install of Karmic, here's the steps I followed.

Ruby and RVM on Ubuntu from source

nb, you might remove zlib1g zlib1g-dev from the list below, I ended up needing to install it again later from source I dunno why

Getting prepared
$ apt-get update
$ apt-get -y install build-essential zlib1g zlib1g-dev libxml2 libxml2-dev libxslt-dev sqlite3 libsqlite3-dev locate git-core libssl-dev openssl autoconf subversion bison
$ apt-get -y install curl wget

Get, Compile and configure zlib
$ cd ~/Downloads
$ wget [http://www.gzip.org/zlib/zlib-1.2.3.tar.gz](http://www.gzip.org/zlib/zlib-1.2.3.tar.gz)
$ rm zlib-1.2.3.tar.gz 
$ cd zlib-1.2.3
$ ./configure
$ make
$ make test
$ sudo make install

Add /usr/local/lib to your environment path
$ sudo gedit /etc/environment

nb, I was gonna opt for ruby 1.9.1 but you need a prior version of ruby installed to compile it! Install 1.9.1 later using rvm

SVN checkout ruby repo into Downloads folder
$ cd ~/Downloads
$ svn co [http://svn.ruby-lang.org/repos/ruby/branches/ruby_1_8_7](http://svn.ruby-lang.org/repos/ruby/branches/ruby_1_8_7)

nb, I'm not sure if you really need to do a sudo make here, maybe just a plain make will suffice?

Compile and install ruby
$ cd ~/Downloads/ruby_1_8_7
$ autoconf
$ ./configure
$ sudo make
$ sudo make install

Get gems manager
$ cd ~/Downloads
$ wget [http://rubyforge.org/frs/download.php/60718/rubygems-1.3.5.tgz](http://rubyforge.org/frs/download.php/60718/rubygems-1.3.5.tgz)

Rubygems: Unzip, install and tidy
$ tar xvzf rubygems-1.3.5.tgz
$ cd rubygems-1.3.5
$ sudo ruby setup.rb
$ cd ..
$ rm rubygems-1.3.5.tgz

Install rvm from github
$ mkdir -p ~/.rvm/src/rvm/ 
$ cd ~/.rvm/src 
$ git clone [http://github.com/wayneeseguin/rvm.git](http://github.com/wayneeseguin/rvm.git)
$ cd rvm
$ ./install

Get stuff for other ruby environments, recommended by rvm
$ aptitude install curl sun-java6-bin sun-java6-jre sun-java6-jdk
$ aptitude install curl bison build-essential zlib1g-dev libssl-dev libreadline5-dev libxml2-dev git-core
$ aptitude install curl mono-2.0-devel

QUOTE FROM HANDY RVM OUTPUT 

"
You must now finish the install manually:

1) Place the following line at the end of your shell's loading files(.bashrc and then .bash_profile for bash and .zshrc for zsh), after all path/variable settings:

     if [[ -s /home/user/.rvm/scripts/rvm ]] ; then source /home/user/.rvm/scripts/rvm ; fi

2) Ensure that there is no 'return' from inside the .bashrc file. (otherwise rvm will be prevented from working properly).

3) CLOSE THIS SHELL and open a new one in order to use rvm.
"

$ gedit ~/.bashrc
$ gedit ~/.bash_profile

You aught now to be able to 

$ rvm install 1.9.1

or 

$ rvm install jruby

and if that works, how about 

$ rvm 1.9.1 --default

now look,

$ ruby -v

cool eh \\:D/

Start here for more help and commands
[http://rvm.beginrescueend.com/introduction/](http://rvm.beginrescueend.com/introduction/)

---

### Post by rafbueno on 2010-02-03
Many thanks! This worked for me!
But if someone try to install the rails gem: gem install rails
and the system don find some folder, just create the folder on location and all gonna work.

---

### Post by 71fractals on 2010-02-19
After installing rvm as a root, my system ruby isn't being repleaced by rubies from rvm:
```

 &#10140;  ~  ruby -v
ruby 1.8.7 (2009-06-12 patchlevel 174) [i486-linux]
 &#10140;  ~  rvm list

rvm Rubies

=> ruby-1.9.2-preview1 [ i386 ]

Default Ruby (for new shells)

   ruby-1.9.2-preview1 [ i386 ]

System Ruby

   system [ ]

 &#10140;  ~  rvm ruby -v

<i> ruby-1.9.2-preview1: ruby 1.9.2dev (2009-07-18 trunk 24186) [i686-linux]  </i>  

ruby 1.9.2dev (2009-07-18 trunk 24186) [i686-linux]

```

How to fix this and why rvm clones files from /usr/local/rvm/gems to $home/.gems ? I want to keep all rvm files in one place for all users

---

### Post by zhinker on 2010-03-21
Don't forget to run this to set the default:
  rvm 1.9.1 --default

---

### Post by nowhere@cox.net on 2010-04-09
Everybody always glosses over this part:
> You must now finish the install manually:

1) Place the following line at the end of your shell's loading files(.bashrc and then .bash_profile for bash and .zshrc for zsh), after all path/variable settings:

if [[ -s /home/user/.rvm/scripts/rvm ]] ; then source /home/user/.rvm/scripts/rvm ; fi

2) Ensure that there is no 'return' from inside the .bashrc file. (otherwise rvm will be prevented from working properly).
With a standard ubuntu install this isn't trivial and I'm not sure how to proceed. It seems that when you ssh into your machine, .bash_profile is executed if it exsits but if you run a terminal from inside gnome then .bashrc is executed. The rvm install scripts has me split everything in .bashrc above the return line into .bashrc (which is actually nothing) and everything else into .bash_profile. The result is that launching a terminal has none of the special formatting like coloring and such.

I assume there is a better way? Anyone?

Thanks!

EDIT: Talked with rvm creator. We just added the line mentioned at the end of the .bashrc file and left the return line in place and everything seems to work.

---

### Post by kittekat on 2010-04-15
I solved the .bashrc/.bash_profile challenge on ubuntu in the following way:

1) rename the original Ubuntu .bashrc file to .bashrc_part2
2) remove the line with the '... && return'
3) create an empty .bashrc file
4) add to this file the requested line:
if [[ -s /home/user/.rvm/scripts/rvm ]] ; then source /home/user/.rvm/scripts/rvm ; fi
5) add also the follwing lines:
if [[ ! -z "PS1" ]] ; then
  source ~/.bashrc_part2
fi

now a "graphic" terminal has again the usual features (as a colored ls alias,...), and the rvm scripts are also happy (as there is no 'return') to see)

the cause for the otherwise observed problem is, that a GDM terminal on Ubuntu does NOT execute the ./bash_profile at login (as it is expected by the rest of the linux community)

---

