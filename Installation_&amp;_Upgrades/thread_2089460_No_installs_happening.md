---
title: "No installs happening"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by Ridgerunrbunny on 2012-11-29
I am getting the following when I try to install ANYTHING:


installArchives() failed: Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)
dpkg: warning: 'ldconfig' not found in PATH or not executable.

I'm at a loss,  any suggestions would be greatly appreciated.

Bunny

---

### Post by dino99 on 2012-11-29
you might need to downgrade some package(s) that are actually conflicting. That might be due to non ubuntu genuine installation (third party, ppa)

---

### Post by Ridgerunrbunny on 2012-11-29
Looked, but, I have no idea how to locate them, I have a bloated T-bite. What would you look for?

Bunny

---

