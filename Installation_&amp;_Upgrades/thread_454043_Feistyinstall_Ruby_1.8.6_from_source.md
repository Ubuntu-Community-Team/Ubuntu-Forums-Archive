---
title: "Feisty/install Ruby 1.8.6 from source"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by cprsize on 2007-05-25
This may be a case of being "just dangerous enough" to cause problems.

Feisty is installed and happy.  But Ruby is 1.8.5 and I want 1.8.6 so I decided to download and install from source.

I'm following the instructions from here: [http://codersifu.blogspot.com/2007/03/howto-install-ruby-in-ubuntu-edgy-610.html](http://codersifu.blogspot.com/2007/03/howto-install-ruby-in-ubuntu-edgy-610.html)

And when I run ruby --version I get this:
```
dwf@flip:~$ ruby --version
ruby 1.8.6 (2007-03-13 patchlevel 0) [i686-linux]
dwf@flip:~$ 
```

But when I try to run 'rails', I get this:
```
dwf@flip:~$ rails
/usr/lib/ruby/1.8/rubygems.rb:9:in `require': no such file to load -- rbconfig (LoadError)
        from /usr/lib/ruby/1.8/rubygems.rb:9
        from /usr/bin/rails:9:in `require'
        from /usr/bin/rails:9
dwf@flip:~$ 
```

Ruby can't seem to find the system files in /usr/lib/ruby/1.8/i686-linux, which is where rbconfig.rb lives.  Do I have some sort of symlink problem?  Synaptic says I still have the default ruby 1.8.5 files installed, but as we see from checking the version on the command line, it looks like I'm running 1.8.6.  So there's some sort of mismatch going on here...

(This is me only sort of understanding installing packages instead of from source)

thx,
--dwf

---

### Post by cprsize on 2007-05-25
I'm not really sure what happened, but it seems to be working now.  It's almost like a reboot fixed it...

Anyone have an idea here?

--dwf

---

### Post by EMTAdam on 2007-05-30
so I'm trying to get ruby 1.8.6 installed on Feisty as well, but when I go to run the configure command I get this; 

```

adam@delta:/opt/src/ruby-1.8.6$ sudo ./configure --prefix=/opt/ruby-1.8.6
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
adam@delta:/opt/src/ruby-1.8.6$

```

I'm pretty new to Linux, I've use windows for years and thought I would try switching over but I need ruby and rails to work or I'll have to go back to windows. Thanks for any help!

.adam.

---

### Post by flargen on 2007-05-31
Firstly, you don't need to run ./configure as root - remove the sudo at the start of the line.

The error may be caused by missing essential headers/libraries (gcc is obviously present). Try installing the package 'build-essential':

```
sudo apt-get install build-essential
```

Also, do you actually need the very latest version of Ruby? You can find Ruby 1.8.5 in the repositories...

---

