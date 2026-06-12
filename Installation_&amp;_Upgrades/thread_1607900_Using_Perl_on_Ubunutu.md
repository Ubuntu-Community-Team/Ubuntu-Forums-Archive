---
title: "Using Perl on Ubunutu"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by andrea_bio on 2010-10-28
Hello

I am new to Ubuntu and have not used it before this week!

I need to run some Perl programs on Ubuntu. I was told that the Perl version that is installed on Ubuntu is the system perl and I should not interfere with it because it is used by system programs to perform various housekeeping tasks.

I was advised of 2 options:
1) Create a local perl installation and install all my modules there
2) Use the system installation but install all my modules in a separate directory

Regarding the second option only for now to reduce the complexity of the answer:
a) where does apt-get install perl modules?
b) can you configure apt-get to install perl modules to a custom location?
c) lets say I install a different version of a module that system perl needs to my local directory. I want to use this version of the module in my programs but I want the system perl to keep using its own version of the module. Can i use the PERL5LIB environment variable to tell my programs where to look for this module or will this cause the system perl to also use the version of the module in my local directory? If this is the case I will have to use the 'use lib' statement in my perl programs.

Many thanks in advance for your help

---

