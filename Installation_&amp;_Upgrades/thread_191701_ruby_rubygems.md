---
title: "ruby rubygems"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by elefante on 2006-06-07
The package **ruby1.8.4** from Ubuntu repositories does not work.
I tried to install **ruby-1.8.4.tar.gz** on a freshy Dapper with these packages installed: build-essential, libzlib-ruby, zlib1g and zlib1g-dev
```
tar -zxvf Ruby-1.8.4.tar.gz
cd Ruby-1.8.4.tar.gz
./configure
make
checkinstall
```
It seems install correctly, but when I try to install Rubygems:
```
tar -zxvf rubygems-0.8.11.tgz
cd rubygems-0.8.11.tgz
sudo ruby setup.rb
```
I got this error:
```
/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require__': no such file to load -- stringio (LoadError)
```
I got this error before (This is the third time that I install Dapper Drake)
```
/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require__': no such file to load -- zlib (LoadError)
```
Thank you for your listening.

---

### Post by Lutz Mueller on 2006-06-12
I had the same problem and could not get it to run.
My configuration is breezy with Ruby 1.8.4 and Rubygems 0.8.11.

I made sure that I installed the libraries from the rubygems faq:

apt-get install libzlib-ruby
apt-get install libyaml-ruby
apt-get install libdrb-ruby
apt-get install liberb-ruby
apt-get install rdoc

also:

apt-get install zlib1g-dev
apt-get install libopenssl-ruby

then I located the Setup file in /usr/local/src/ruby-1.8.4/ext
and uncommented zlib (remove the #). In fact, I uncommented
practically everything that didn't look like it was Windows stuff.

After saving, I went through the steps of installing ruby again:

cd /usr/local/src/ruby/ruby-1.8.4
./configure
make
make test
make install

then I tried installing rubygems again:

cd /usr/local/src/rubugems-0.8.11
ruby setup.rb

voila, success.

I sure hope this helps. I'm a beginner myself and I'd appreciate 
some feedback as to whether this worked for you if you came 
to this thread looking for answers.

last but not least, you may find this helpful:

[http://fo64.com/articles/2005/10/20/rails-on-breezy](http://fo64.com/articles/2005/10/20/rails-on-breezy)

best,

Lutz

---

### Post by elefante on 2006-06-15
Lutz Mueller,

thank you for your cooperation,

I have installed all the packages you described with one exception: rdoc
I didn't install rdoc because Synaptic asks to install ruby1.8 as a dependent package.
So I did:
```
cd ruby-1.8.4
make clean
./configure
make
make test
sudo make install
```
And got this error now:
```

mkdir -p -m 755 /usr/local/man/man1
/home/fernando/ruby-1.8.4/lib/fileutils.rb:240:in `mkdir': File exists - /usr/local/man (Errno::EEXIST)
        from /home/fernando/ruby-1.8.4/lib/fileutils.rb:240:in `fu_mkdir'
        from /home/fernando/ruby-1.8.4/lib/fileutils.rb:217:in `makedirs'
        from /home/fernando/ruby-1.8.4/lib/fileutils.rb:215:in `makedirs'
        from /home/fernando/ruby-1.8.4/lib/fileutils.rb:201:in `makedirs'
        from /home/fernando/ruby-1.8.4/lib/fileutils.rb:1508:in `makedirs'
        from ./instruby.rb:81:in `makedirs'
        from ./instruby.rb:213
        from ./instruby.rb:205
        from ./instruby.rb:64:in `install?'
        from ./instruby.rb:204
make: *** [do-install-local] Error 1

```
I am a newbie, but I think this is about the system does not allow reinstall ruby. I guess I'm missing something here.
I'm studying a documentation to learn about compilation process now.

thank you.

---

### Post by elefante on 2006-06-19
I finally correctly installed Ruby in my box!
 
The final move was to delete the file **man** located at: **/usr/local/**
this file was blocking the recompiling process.

[SIZE="5"]The process to install Ruby correctly on a freshy Dapper is:[/SIZE]

Install these packages (You can use Synaptic Package Manager for this part)

**build-essential** - this package is for the compiling process.
**checkinstall** - to manage packages installed from source. Using this tool, 
you will see the package you just installed at Synaptic Package Manager. Uninstall becomes easy then.

I don't know about these packages, but they are important:

**libzlib-ruby**
**libyaml-ruby**
**libdrb-ruby**
**liberb-ruby**
**zlib1g-dev**
**libopenssl-ruby**

Now you are ready to the compiling process:

Get the Ruby source-code from the [Ruby project]("http://rubyforge.org/projects/ruby/"). The recomended package at the time of this post was: **Ruby-1.8.4.tar.gz**

Unpack the Ruby-1.8.4.tar.gz at a directory of your choice:

```
~/src$ tar -zxvf Ruby-1.8.4.tar.gz
~/src$ cd ruby-1.8.4
~/src/ruby-1.8.4$ ./configure
```

Special thanks to **Lutz Mueller** for this part.

Now you have to uncomment **zlib** and **stringio** lines (remove the #) from the **Setup** file located at** ~/src/ruby-1.8.4/ext$**

After saving, go through the others steps of installing ruby:
```

~/src/ruby-1.8.4$ make
~/src/ruby-1.8.4$ make test
~/src/ruby-1.8.4$ sudo checkinstall
```

Installing RubyGems:

Get the RubyGems source-code from the [Ruby project]("http://rubyforge.org/frs/?group_id=126&release_id=2471"). The recomended package at the time of this post was: **rubygems-0.8.11.tgz**

Unpack the rubygems-0.8.11.tgz at a directory of your choice:
```
~/src$ tar -zxvf rubygems-0.8.11.tgz
~/src$ cd rubygems-0.8.11
~/src/rubygems-0.8.11$ sudo ruby setup.rb
```

That's it!
I hope it will be helpfull!
Shall the spirit of Ubuntu be with you.

---

### Post by DAaaMan64 on 2006-06-19
```

sudo apt-get install libzlib-ruby libyaml-ruby libdrb-ruby liberb-ruby zlib1g-dev libopenssl-ruby

```

Just an apt-get statement that will get all those additional packages for you, nothing fancy.


I'm lazy, how about you? Enjoy :)

---

### Post by daniel2501 on 2006-07-02
On a related subject, does anyone know of a good how-to for getting apache2 to work with rhtml? I can't seem to get it right...

---

### Post by stewbawka on 2007-08-30
> **elefante said:**
> 
Unpack the rubygems-0.8.11.tgz at a directory of your choice:
```
~/src$ tar -zxvf rubygems-0.8.11.tgz
~/src$ cd rubygems-0.8.11
~/src/rubygems-0.8.11$ sudo ruby setup.rb
```


i get the following error when i try to setup rubygems: 

<--- lib
/usr/local/lib/ruby/site_ruby/1.8/rubygems/remote_fetcher.rb:4:in `require': no such file to load -- zlib (LoadError)
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/remote_fetcher.rb:4
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/source_index.rb:8:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/source_index.rb:8
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:501:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:501
        from /tmp/rubygems-0.9.2/./post-install.rb:81:in `require'
        from /tmp/rubygems-0.9.2/./post-install.rb:81:in `install_sources'
        from /tmp/rubygems-0.9.2/./post-install.rb:116:in `try_run_hook'
        from setup.rb:584:in `run_hook'
        from setup.rb:1322:in `exec_task_traverse'
        from setup.rb:1175:in `exec_install'
        from setup.rb:894:in `exec_install'
        from setup.rb:712:in `invoke'
        from setup.rb:681:in `invoke'
        from setup.rb:1359

I did uncomment the 'zlib' from Setup ... any ideas what is wrong? i had ruby previously installed, but i reinstalled because i'm trying to get rubytk working.. which leads me to my next problem: how do i get rubytk working in ubuntu? i think i have the right packages installed (libtk-ruby and libtcltk-ruby).. Thanks!

BTW, using feisty fawn

---

### Post by quigleydoor on 2007-09-23
I found a workaround here:

[http://lucaschan.com/weblog/2007/03/22/installing-ruby-on-rails-on-centosredhat-4x/](http://lucaschan.com/weblog/2007/03/22/installing-ruby-on-rails-on-centosredhat-4x/)

Also, you can compile the latest version of ruby with these instructions:

[http://www.carmelyne.com/2007/7/17/compiling-ruby-1-8-6-on-ubuntu](http://www.carmelyne.com/2007/7/17/compiling-ruby-1-8-6-on-ubuntu)

:guitar: I now have Ruby 1.8.6 and Gems 0.9.4 on my crappy old Xubuntu 433MHz!

---

