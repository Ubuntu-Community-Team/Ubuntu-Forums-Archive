---
title: "Ruby on Rails install issues"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by timClicks on 2008-10-16
Hi there, I'm trying to install Ruby on Rails, by using their package manager RubyGem. Does this look familiar at all?

tim@tim-laptop:~$ sudo gem install rails
[sudo] password for tim: 
Successfully installed rails-2.1.1
1 gem installed
tim@tim-laptop:~$ rails /diamond
The program 'rails' is currently not installed.  You can install it by typing:
sudo apt-get install rails
bash: rails: command not found

---

### Post by MyNameisTheStig on 2008-10-19
Hi

I've had problems installing Ruby on Rails too, but the following commands worked after several attempts:

```
robin@robin-laptop:~$ sudo apt-get install rubygems
```
```
robin@robin-laptop:~$ sudo gem install rails
```
```
robin@robin-laptop:~$ sudo apt-get install rails
```

Hope that helps,
MyNameisTheStig

---

### Post by timClicks on 2008-11-02
thanks Stig. have managed get it up and running.

---

### Post by gphilip on 2009-04-04
I had the same problem. I fixed this by locating the "rails" executable and updating my PATH variable to add its directory.

To locate the rails executable, I did the following:

1. ```
$ sudo updatedb
```
2. Wait till updatedb completes its thing.
3.```
$ locate rails |grep -e "bin/rails$" 
/var/lib/gems/1.8/bin/rails
/var/lib/gems/1.8/gems/rails-2.3.2/bin/rails
$
```

These two files differ in a few lines, and I am not sure of the significance. I put /var/lib/gems/1.8/bin in my PATH : added the following to my ~/.bashrc

```
 export PATH=$PATH:/var/lib/gems/1.8/bin 
```

I opened another terminal window, and typing in rails resulted in a big usage message.

Hope this helps,
Philip

---

### Post by anoldhacker on 2009-07-06
> **timClicks said:**
> Hi there, I'm trying to install Ruby on Rails, by using their package manager RubyGem. Does this look familiar at all?

tim@tim-laptop:~$ sudo gem install rails
[sudo] password for tim: 
Successfully installed rails-2.1.1
1 gem installed
tim@tim-laptop:~$ rails /diamond
The program 'rails' is currently not installed.  You can install it by typing:
sudo apt-get install rails
bash: rails: command not found

Rails requires gem version >= 1.3.1.  If you don't have it in your OS repo, d/l & install it from source.

And don't ever, EVER install rails from an OS repo.  Rails moves too fast/OS repos move too slow.

---

### Post by umuro on 2009-07-07
Ruby on Rails installation; used by many people happily:
[http://conceptspace.wikidot.com/rails101:basic-ruby-on-rails-installation](http://conceptspace.wikidot.com/rails101:basic-ruby-on-rails-installation)

---

### Post by knetcozd on 2009-07-17
I had the same problem but what i found to work easily is to do the following:

first install xampp

next install rails as a gem and not via apt-get,also install mysql,rake gems
```
gem install rails
gem install mysql
gem install rake
```

next locate rails bin
```
locate rails |grep bin
for me its here:
/var/lib/gems/1.8/bin/rails

```

next create a symlink to the rails and rake binary
```
ln -s /var/lib/gems/1.8/bin/rails  /usr/bin/rails
ln -s /var/lib/gems/1.8/bin/rake  /usr/bin/rake 
```

also if you have troubles interacting with your mysql database, just leave 1 blank space before your password eg.
```
instead of:
password:password
use:
password: password
```

Now rails should run smoothly:P

---

### Post by sms420 on 2009-07-19
Hi there, this is my first post, so I apologize in advance for if it's uber redundant.

But I already have RoR installed on my machine, but whenever trying to do anything, it seems like there is always an error as my gems / rails / ruby / whatever is outdated. 

Is there a way to completely uninstall (1) Ruby (2) Gems (3) Rails (4) anything else remotely associated with numbers 1-3, and then reinstall these things with the latest and greatest version?

Thanks.

---

### Post by timClicks on 2009-08-09
@sms420

anoldhacker's point is pretty important - the Ubuntu repositories will always run behing. An active project like Rails is going to be increasingly outstripping the MOTU.

---

