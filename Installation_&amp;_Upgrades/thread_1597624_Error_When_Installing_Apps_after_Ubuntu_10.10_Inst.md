---
title: "Error When Installing Apps after Ubuntu 10.10 Install"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by ViKz on 2010-10-15
Hi there,

I've just installed Ubuntu 10.10 and I seem to be having some problems installing applications from Software Centre and installing updates from update manager.

Heres the error message I got when I was trying to install software using the software centre:

```

The installation or removal of a software package failed.

 installArchives() failed:  
 Extract templates from packages: 58% 
 Extract templates from packages: 100% 
  
 Extract templates from packages: 58% 
 Extract templates from packages: 100% 
 Setting up tzdata (2010m-0ubuntu0.10.10) ... 
 Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
 Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
 Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
 Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
 Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
 Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
 Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
 Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
 Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
 Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109. 
 dpkg: error processing tzdata (--configure): 
  subprocess installed post-installation script returned error exit status 128 
 No apport report written because MaxReports is reached already 
 Errors were encountered while processing: 
  tzdata 
 Setting up tzdata (2010m-0ubuntu0.10.10) ... 
 Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
 Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
 Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
 Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
 Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
 Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
 Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
 Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
 Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
 Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109. 
 dpkg: error processing tzdata (--configure): 
  subprocess installed post-installation script returned error exit status 128 
 
```Now I'm kinda new to Ubuntu so I can't make heads or tails of this...is anyone able to shed some light and provide a resolution?

---

### Post by mörgæs on 2010-10-15
There are several threads in the forum regarding this topic, for example

[http://wwww.ubuntuforums.org/showthread.php?t=1594803](http://wwww.ubuntuforums.org/showthread.php?t=1594803)

---

