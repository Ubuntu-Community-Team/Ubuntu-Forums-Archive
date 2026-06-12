---
title: "Perl and dpkg errors when installing packages"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by Crucinator on 2006-08-09
To give a little background, my Ubuntu box was working fine about a month ago.  I decided to install and run [HoTTProxy]("http://www.hottproxy.org/"), and in order to do so, installed various perl modules from CPAN.  I had some trouble at first, but finally got everything to work.

Since then, I've had problems installing new packages.  My first error came when I upgraded Thunderbird.  I don't remember the exact error, but it had to do with an "error code 2".  Now I am getting more errors when I tried to install Quanta.  The following is the error from the terminal shell when I try to install, update, or upgrade anything.

```
Can't locate Debian/Defoma/Common.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/defoma-app line 8.
BEGIN failed--compilation aborted at /usr/bin/defoma-app line 8.
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
Unpacking replacement libwmf0.2-7 ...
Setting up cvs (1.12.9-17) ...
Can't locate DebianNet.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-inetd line 23.
dpkg: error processing cvs (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libcvsservice0:
 libcvsservice0 depends on cvs (>= 1.11); however:
  Package cvs is not configured yet.
dpkg: error processing libcvsservice0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of quanta:
 quanta depends on libcvsservice0 (>= 4:3.5.2); however:
  Package libcvsservice0 is not configured yet.
dpkg: error processing quanta (--configure):
 dependency problems - leaving unconfigured
Setting up libwmf0.2-7 (0.2.8.3-3.1ubuntu0.1) ...
Updating the gdk-pixbuf loaders list for GTK+-2.4.0...done.
Can't locate Debian/Defoma/Common.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/defoma-app line 8.
BEGIN failed--compilation aborted at /usr/bin/defoma-app line 8.
dpkg: error processing libwmf0.2-7 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 cvs
 libcvsservice0
 quanta
 libwmf0.2-7
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I'm not experienced troubleshooting dpkg or perl, so I need help...

---

### Post by Crucinator on 2006-08-11
Bump.

Can anyone help explain why I'm getting the errors listed?  I've looked at a couple threads which say to remove and reinstall the packages with errors to fix the dpkg problem.  However, I've yet to find info on how to fix the "DebianNet.pm in @INC" error...

---

### Post by Crucinator on 2006-08-15
Last bump for this thread, then I will allow it to die in peace...

---

### Post by az on 2006-08-15
Did you use non-ubuntu repositories?

Did you try

sudo apt-get -f install (to fix any broken packages?)

---

### Post by Crucinator on 2006-08-15
I only have the universe and multiverse repositories for main, updates, and security enabled; not the backport, PLF, or commercial repositories.

I did install some Perl modules from CPAN, so I guess those are not entirely supported by Ubuntu.

I have tried "sudo apt-get -f install" and "sudo dpkg --configure -f".  Neither worked.

---

### Post by Crucinator on 2006-08-18
I think I figured out how to solve my problem. It turns out "DebianNet.pm" is part of the Netbase package and "Common.pm" is found in the Defoma package (both found in Synaptic). When I reinstalled both packages, the unconfigured ones completed their installs. Everything looks good now. Thanks for those who helped.

---

