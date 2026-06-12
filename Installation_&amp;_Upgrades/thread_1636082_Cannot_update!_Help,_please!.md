---
title: "Cannot update! Help, please!"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by Universal fx on 2010-12-02
I am new to Ubuntu and everything seems to be working great but i cannot install updates (181)
I'm using 10.10,

Heres is the error i get :

The installation or removal of a software package failed.

Details -

```
installArchives() failed:  Extracting templates from packages: 16% Extracting templates from packages: 33% Extracting templates from packages: 49% Extracting templates from packages: 66% Extracting templates from packages: 82% Extracting templates from packages: 99% Extracting templates from packages: 100% 
Preconfiguring packages ... 
 Extracting templates from packages: 16% Extracting templates from packages: 33% Extracting templates from packages: 49% Extracting templates from packages: 66% Extracting templates from packages: 82% Extracting templates from packages: 99% Extracting templates from packages: 100% 
Preconfiguring packages ... 
Setting up tzdata (2010o-0ubuntu0.10.10) ... 
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
Setting up tzdata (2010o-0ubuntu0.10.10) ... 
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
```Can somebody please help me. :(

---

### Post by zvacet on 2010-12-03
```
sudo dpkg --configure -a
```

---

### Post by sikander3786 on 2010-12-03
That error doesn't seem to go easily ;-)

Try this one as well and post the output.

```
sudo apt-get install -f
```

---

