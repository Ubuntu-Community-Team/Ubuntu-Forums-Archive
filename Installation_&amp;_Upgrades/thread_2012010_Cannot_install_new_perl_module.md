---
title: "Cannot install new perl module"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by joj0o on 2012-06-28
Hi, I am fairly new in ubuntu and right now I have problems to install new perl module on my ubuntu 11.10 64 bits.

Every time I download a perl module from CPAN, and tried to compile it through "perl Makefile.PL" It always show an error. here is the error :

Warning: PERL_LIB  (/tmp/perl---------------------------------------------please-run-the-install-script---------------------------------------------/lib)  seems not to be a perl library directory
        (strict.pm not found) at /usr/lib/perl5/ExtUtils/MM_Unix.pm line 1736.
Have /usr/lib/perl/5.12
Want  /tmp/perl---------------------------------------------please-run-the-install-script---------------------------------------------/lib
Your perl and your Config.pm seem to have different ideas about the 
architecture they are running on.
Perl thinks: [5.12]
Config says: [x86_64-linux-thread-multi]
This may or may not cause problems. Please check your installation of perl 
if you have problems building this extension.

After that, if I tried to perform "make" it always produce an error like this :

make: *** No rule to make target `/tmp/perl---------------------------------------------please-run-the-install-script---------------------------------------------/lib/Config.pm', needed by `Makefile'.  Stop.


It also happen if I tried to install through "cpan Module::Name". 

I really confused what happen in here. Can somebody help me with this problem please?

Thanks before.

---

