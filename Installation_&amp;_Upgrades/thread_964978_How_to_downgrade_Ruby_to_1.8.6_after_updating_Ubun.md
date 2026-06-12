---
title: "How to downgrade Ruby to 1.8.6 after updating Ubuntu to 8.10?"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by g0nzo on 2008-10-31
Hi,

I've just updated Ubuntu to 8.10 and everything seems to be fine except for Ruby version. It has been updated to 1.8.7, but older version of Rails (Ruby web framework) don't work with 1.8.7.

How to downgrade Ruby packages (ruby1.8, ruby1.8-dev, libruby1.8, libreadline-ruby1.8, libopenssl-ruby1.8, libdbm-ruby1.8, maybe something else too) to 1.8.6 version as in Ubuntu 8.04?

---

### Post by guigs on 2008-11-02
I have the same problem. I'm a Ruby on Rails developer and since I upgraded to Intrepid my applications stoped working. The problem is that Rails 2.1 (actually it's the current version, not an old one) is not compatible with Ruby 1.8.7.
I need to downgrade to Ruby 1.8.6, but I can't do it from Synaptic. The "force version" option is not enabled for Ruby.

---

### Post by g0nzo on 2008-11-02
You can try upgrade your app to Rails 2.1.2 - I had Rails 2.1.0 app and upgrading to 2.1.2 fixed problems with Ruby 1.8.7 for me.

But that's just a single app of many that I've got, some are still using Rails 1.2 branch and it would be really great, if there was an option to downgrade Ruby to 1.8.6 using synaptic.

---

### Post by mferrier on 2008-11-02
I'm also looking for the answer to this question, if any of you Ubuntu gurus can help.

---

### Post by mferrier on 2008-11-02
Should we just remove ruby and install the version we want without apt?

---

### Post by mferrier on 2008-11-03
Okay, I think I figured out how to do this. I used "pinning".

First, I updated my /etc/apt/sources.list to include hardy for all the sources. It now looks like this:

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid main restricted
deb http://mirror.cs.umn.edu/ubuntu/ hardy main restricted
# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid main restricted
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid-updates main restricted
deb http://mirror.cs.umn.edu/ubuntu/ hardy-updates main restricted

# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid-updates main restricted
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid universe
deb http://mirror.cs.umn.edu/ubuntu/ hardy universe

# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid universe
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy universe

# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid-updates universe
deb http://mirror.cs.umn.edu/ubuntu/ hardy-updates universe

# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid-updates universe
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid multiverse
deb http://mirror.cs.umn.edu/ubuntu/ hardy multiverse

# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy multiverse
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid multiverse


# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid-updates multiverse
deb http://mirror.cs.umn.edu/ubuntu/ hardy-updates multiverse

# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid-updates multiverse
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.cs.umn.edu/ubuntu/ intrepid-backports main restricted universe multiverse
deb http://mirror.cs.umn.edu/ubuntu/ hardy-backports main restricted universe multiverse

deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb http://archive.canonical.com/ubuntu hardy partner

deb-src http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid-security main restricted
deb http://mirror.cs.umn.edu/ubuntu/ hardy-security main restricted

# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid-security main restricted
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy-security main restricted

# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid-security universe
deb http://mirror.cs.umn.edu/ubuntu/ hardy-security universe

# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid-security universe
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy-security universe

# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid-security multiverse
deb http://mirror.cs.umn.edu/ubuntu/ hardy-security multiverse

# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid-security multiverse
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy-security multiverse

```

Then, I created /etc/apt/preferences and made it look like this:

```
Package: ruby
Pin: release a=hardy
Pin-Priority: 900

Package: ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: rdoc1.8
Pin: release a=hardy
Pin-Priority: 900

Package: ri1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libgtk2-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libdbd-sqlite3-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libopenssl-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libsqlite3-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: ruby1.8-dev
Pin: release a=hardy
Pin-Priority: 900

Package: libdbi-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libatk1-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libpango1-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libatk1-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libgdk-pixbuf2-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libglib2-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libcairo-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: irb1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libreadline-ruby1.8
Pin: release a=hardy
Pin-Priority: 900
```

I guess this tells the system to use the hardy versions of all these packages. Then I did 'apt-get install ruby1.8 ... (all the packages)' and it downgraded them all to the hardy versions.

Hope this helps someone.

---

### Post by guigs on 2008-11-05
Upgrading to Rails 2.1.2 did't solve the problem. Rails 2.1 is really incompatible with Ruby 1.8.7 (see [http://www.rubyonrails.org/down](http://www.rubyonrails.org/down)). I've tried the solution posted by mferrier but it did't work. 
After modifying /etc/apt/sources.list and creating /etc/apt/preferences, I run "apt-get install ruby1.8 ruby1.8-dev" but it says ruby1.8 is already the last version:

```

$ sudo apt-get install ruby1.8 ruby1.8-dev
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
ruby1.8 já é a versão mais nova.
ruby1.8-dev já é a versão mais nova.
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.

```

---

### Post by guigs on 2008-11-05
Finally I got Ruby 1.8.6 on Intrepid!!
After including hardy sources in /etc/apt/sources.list I had to "Reload package information" using Synaptic.
Then I could select ruby packages and "force version" to 1.8.6
Now I have my Ruby on Rails development environment working again in Ubuntu.
Thanks!

---

### Post by dgalindo on 2008-11-06
Thanks a lot !,  this really saved my day.

---

### Post by arnonmoscona on 2008-11-08
One slight correction. The version below does not include rails in /etc/apt/preferences. To install rails I needed to add the two additional packages:

```


Package: rails
Pin: release a=hardy
Pin-Priority: 900

Package: libncurses-ruby1.8
Pin: release a=hardy
Pin-Priority: 900


```

Also, on my particular system, neither apt-get nor synaptic worked correctly to do this. I had to use dselect to do the job and then it finally worked.


> **mferrier said:**
> Okay, I think I figured out how to do this. I used "pinning".

First, I updated my /etc/apt/sources.list to include hardy for all the sources. It now looks like this:

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid main restricted
deb http://mirror.cs.umn.edu/ubuntu/ hardy main restricted
# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid main restricted
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid-updates main restricted
deb http://mirror.cs.umn.edu/ubuntu/ hardy-updates main restricted

# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid-updates main restricted
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid universe
deb http://mirror.cs.umn.edu/ubuntu/ hardy universe

# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid universe
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy universe

# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid-updates universe
deb http://mirror.cs.umn.edu/ubuntu/ hardy-updates universe

# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid-updates universe
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid multiverse
deb http://mirror.cs.umn.edu/ubuntu/ hardy multiverse

# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy multiverse
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid multiverse


# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid-updates multiverse
deb http://mirror.cs.umn.edu/ubuntu/ hardy-updates multiverse

# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid-updates multiverse
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.cs.umn.edu/ubuntu/ intrepid-backports main restricted universe multiverse
deb http://mirror.cs.umn.edu/ubuntu/ hardy-backports main restricted universe multiverse

deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb http://archive.canonical.com/ubuntu hardy partner

deb-src http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid-security main restricted
deb http://mirror.cs.umn.edu/ubuntu/ hardy-security main restricted

# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid-security main restricted
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy-security main restricted

# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid-security universe
deb http://mirror.cs.umn.edu/ubuntu/ hardy-security universe

# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid-security universe
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy-security universe

# Line commented out by installer because it failed to verify:
deb http://mirror.cs.umn.edu/ubuntu/ intrepid-security multiverse
deb http://mirror.cs.umn.edu/ubuntu/ hardy-security multiverse

# Line commented out by installer because it failed to verify:
deb-src http://mirror.cs.umn.edu/ubuntu/ intrepid-security multiverse
deb-src http://mirror.cs.umn.edu/ubuntu/ hardy-security multiverse

```

Then, I created /etc/apt/preferences and made it look like this:

```
Package: ruby
Pin: release a=hardy
Pin-Priority: 900

Package: ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: rdoc1.8
Pin: release a=hardy
Pin-Priority: 900

Package: ri1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libgtk2-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libdbd-sqlite3-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libopenssl-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libsqlite3-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: ruby1.8-dev
Pin: release a=hardy
Pin-Priority: 900

Package: libdbi-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libatk1-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libpango1-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libatk1-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libgdk-pixbuf2-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libglib2-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libcairo-ruby1.8
Pin: release a=hardy
Pin-Priority: 900

Package: irb1.8
Pin: release a=hardy
Pin-Priority: 900

Package: libreadline-ruby1.8
Pin: release a=hardy
Pin-Priority: 900
```

I guess this tells the system to use the hardy versions of all these packages. Then I did 'apt-get install ruby1.8 ... (all the packages)' and it downgraded them all to the hardy versions.

Hope this helps someone.

---

### Post by tomcocca on 2008-11-12
Hi Guys, thanks so much for your help here.  After I downgraded successfully I lost the RUBY env variable.

So now I have to type ruby before script/server or script/console

Does anybody know how to get that back?

If I type ruby script/server  it works fine

If i just type script/server i just get the following - 

: No such file or directory


Thanks again,
~ Tom

---

### Post by mikhailov on 2008-11-28
I have just combine all yours suggestions to the one post.
You can take a look this one at 
[http://railsgeek.com/2008/11/27/ubuntu-8-10-downgrade-ruby-1-8-7-to-1-8-6]("http://railsgeek.com/2008/11/27/ubuntu-8-10-downgrade-ruby-1-8-7-to-1-8-6")

---

### Post by murb on 2009-02-23
Isn't it simpler to simply add only this line to /etc/apt/sources.list:

```
deb http://nl.archive.ubuntu.com/ubuntu/ hardy main restricted
```

and force, and later lock, the versions for ruby1.8 and libruby1.8 to 1.8.6 using synaptic? (I don't like to overwrite my entire packagelist just to get ruby working ;) )

---

### Post by denro on 2009-06-05
> **murb said:**
> Isn't it simpler to simply add only this line to /etc/apt/sources.list:

```
deb http://nl.archive.ubuntu.com/ubuntu/ hardy main restricted
```

and force, and later lock, the versions for ruby1.8 and libruby1.8 to 1.8.6 using synaptic? (I don't like to overwrite my entire packagelist just to get ruby working ;) )

I ended up adding all hardy sources to get other dependencies working, and then got tired of clicking around in synaptic ( its an older computer), then finally falling back to the preferences file ;) what an adventure. I would recommend the pinning in /etc/apt/preferences if anyone have more than a few dependencies.

---

### Post by cswebgrl on 2009-06-25
Hi,

I have jaunty running and realized that my rails app, specifically activescaffold and image_science do not work with ruby 1.8.7.  I was able to get around image_science with imagemagick, but I don't see an option for activescaffold.  It looks like the best solution is to downgrade to ruby 1.8.6.  

Has anyone else tried using the same code that's listed here for hardy using jaunty?

Thanks!!

---

### Post by anoldhacker on 2009-07-06
> **g0nzo said:**
> Hi,

I've just updated Ubuntu to 8.10 and everything seems to be fine except for Ruby version. It has been updated to 1.8.7, but older version of Rails (Ruby web framework) don't work with 1.8.7.

How to downgrade Ruby packages (ruby1.8, ruby1.8-dev, libruby1.8, libreadline-ruby1.8, libopenssl-ruby1.8, libdbm-ruby1.8, maybe something else too) to 1.8.6 version as in Ubuntu 8.04?

I'm actually surprised by this thread.  We're running 2.2 on 1.8.7 in production on a CEntOS server with no problems.  You might do well to check your deprecation warnings.  It seems more likely to me that rails will be running 1.9 only than 1.8.6 only.

---

