---
title: "Perl Modules Installation Problem"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by tylee on 2007-02-03
Hi, I am setting up MisterHouse on my linux box to control the lights in my basement.  I am installing it on Ubuntu 6.06 LTS Dapper Drake.  I am somewhat new to linux but have definetaly learned a lot since I started.  To set up Misterhouse on my box I am using the tutorial on the Wiki under configuration, how to set it up on Ubuntu[(Here is the link to the tut)]("http://misterhouse.wikispaces.com/Install+Packages").  The tutorial is fine until I try to install the perl modules using CPAN.  When I try to do that it does everything fine until it gets to the Running make test part, at the end.  This is what it says, for example when I try to install Time::HiRes.

[FONT="Lucida Console"]Checking if you kit is complete...
Looks good
Writing Makefile for Time::HiRes
Now you may issue 'make'.  Do not forget to also 'make test'.
Note: if you get an error like this (the Makefile line number may vary):
Makefile:91: *** missing separator
then set the environment variable LC_ALL to "C" and retry
from scratch (re-run perl "Makefile.PL").
(And consider upgrading your Perl.)
   --NOT OK
Running make test
 Can't test without successful make
Running make install
 make had returned bad status, install seems impossible[/FONT]

Every module that I try to install it does this to, and gives the same message.  I am really not sure what this means and need help to fix it.  Thanks.

---

### Post by tylee on 2007-02-03
After doing a little more research I tried to download and install the modules from the tar.gz files on the CPAN website.  All goes well until I have to issue the make command.  It can't find the command make.  What package do I need to issue this command.  I think this is the problem. :)

---

### Post by tylee on 2007-02-03
Sorry for the post, after installing the build-essential package and downloading the tarballs the CPAN modules are installing quite flawlessly.

---

### Post by Trapper on 2007-02-07
Don't apologize for the post. We should be able to do CPAN correctly by default. I guess the Ubuntu folks don't think the same. Oddly, it's the only distro I've ever had that had CPAN fail unless other things were installed prior to it's usage. What's the sense in even having it if it doesn't work from the start? Get with the prog guys ...... we all need build-essential by DEFAULT. There's a hint here .... "essential".

---

### Post by norman_ on 2007-03-17
> **tylee said:**
> Sorry for the post, after installing the build-essential package and downloading the tarballs the CPAN modules are installing quite flawlessly.

Don't be sorry, your post solved my problem.

Thanks!

---

