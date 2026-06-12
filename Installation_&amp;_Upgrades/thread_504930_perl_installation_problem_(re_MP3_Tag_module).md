---
title: "perl installation problem (re: MP3 Tag module)"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by scholzilla on 2007-07-19
Hi,

I'm trying to install pacpl so that I can convert among various audio formats. There is apparently something wrong with my perl installation (feisty) that prevents me from installing the MP3::Tag module required by pacpl. Here's what happens when I try installing from root:
---------------------
[email]root@matt-laptop:/home/matt/.cpan[/email]/build/MP3-Tag-0.9709# make -i install
mkdir /usr/local/man/man1: File exists at /usr/share/perl/5.8/ExtUtils/Install.pm line 112
make: [pure_site_install] Error 17 (ignored)
Appending installation info to /usr/local/lib/perl/5.8.8/perllocal.pod
---------------------
As you can see, ignoring the error doesn't bypass the problem. I reinstalled perl and it didn't help. Any suggestions? The guy who wrote pacpl suggested I post here for help.

Thanks

---

### Post by ChrisDerson on 2008-02-27
Hi,

I just fixed a very similar problem with OCS NG.  The problem seems to be that Perl expects the modules to be installed in /usr/local, but Ubuntu uses /usr.

According the the PerlDoc entry for [MakeMaker]("http://perldoc.perl.org/ExtUtils/MakeMaker.html") you should be able to provide some parameters to Makefile.PL to change the install locations.  However, I couldn't get this to work, so in the end I modified the Makefile, changing /usr/local references to /usr.

I would proceed with a little caution though, I don't think you should change *all* the /usr/local references, just the ones that seem to end up pointing to a man page.

---

