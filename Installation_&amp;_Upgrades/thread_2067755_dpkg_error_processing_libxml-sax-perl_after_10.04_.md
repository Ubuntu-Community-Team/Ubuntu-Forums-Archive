---
title: "dpkg: error processing libxml-sax-perl after 10.04 to 12.04 upgrade"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by TheFu on 2012-10-07
This morning, I cloned a completely updated and patched Ubuntu 10.04 x64 server for the purpose of updating to 12.04.  

The 12.04 update seemed to go fine, but after the reboot, the first 
```
# apt-get update
# apt-get dist-upgrade
```failed with this output:
```
# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up libxml-sax-perl (0.99+dfsg-1ubuntu0.1) ...
update-perl-sax-parsers: Registering Perl SAX parser XML::SAX::PurePerl with priority 10...
Can't locate XML/NamespaceSupport.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /usr/share/perl5/XML/SAX/PurePerl.pm line 20.
BEGIN failed--compilation aborted at /usr/share/perl5/XML/SAX/PurePerl.pm line 20.
Compilation failed in require at /usr/share/perl5/XML/SAX.pm line 153.
dpkg: error processing libxml-sax-perl (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libxml-libxml-perl:
 libxml-libxml-perl depends on libxml-sax-perl; however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-sax-expat-perl:
 libxml-sax-expat-perl depends on libxml-sax-perl (>= 0.03); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-sax-expat-perl (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 libxml-sax-perl
 libxml-libxml-perl
 libxml-sax-expat-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Attempts to use 
```
# apt-get install -f
```to correct the problem has failed.
A little searching suggested that the missing dependency should be corrected by 
```
# apt-get -f install libxml-namespacesupport-perl
```That returned:
```
libxml-namespacesupport-perl is already the newest version.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]?
```Which fails in exactly the same way as shown above.

Found this post [http://ubuntuforums.org/showthread.php?t=1457166](http://ubuntuforums.org/showthread.php?t=1457166) which seems similar, but the fix didn't work. No language issues on the machine. The locale seems to be set and correct.

[https://bugs.launchpad.net/ubuntu/+source/libxml-sax-perl/+bug/366969](https://bugs.launchpad.net/ubuntu/+source/libxml-sax-perl/+bug/366969) has what seems like the same issue from 2009.

 Is there a** more useful dpkg log with details somewhere?** /var/log/dpkg.log isn't very useful.
```
2012-10-07 13:19:05 startup packages configure
2012-10-07 13:19:05 configure libxml-sax-perl 0.99+dfsg-1ubuntu0.1 <none>
2012-10-07 13:19:05 status half-configured libxml-sax-perl 0.99+dfsg-1ubuntu0.1
``` 

Ideas to correct this dpkg error/issue?

---

### Post by zvacet on 2012-10-08
Try with 

```
sudo dpkg --configure -a
```

---

### Post by TheFu on 2012-10-08
> **zvacet said:**
> Try with 

```
sudo dpkg --configure -a
```

I ended up wiping the machine and reloading 12.04 from scratch. However, I did use 
# dpkg-reconfigure libxml-sax-perl
and about 10 other commands with dpkg directly; none of them helped.

Sorry I decided to leave this. I've been plagued by APT errors on other systems and didn't want to leave this brand new box festering.

I did find a solution online that suggested editing the postinst script for the package to get through the issue.  I figured if that was needed, then I was already screwed, so why not start fresh.

This is for a blog server, so nothing too important.  The current machine is running 10.04 with the OS version of Ruby/Rails and I'm migrating it to a newer machine running 12.04 and will be using **RVM** to keep the OS updates out of the ruby crap. Ruby devs tend to force new versions every few months like an baby needing a diaper change. 
Ubuntu doesn't have the versions of ruby and the gems that are required by the blog software available. That's pretty common. Canonical seems to be at least 6 months behind on software development tools.  I'd prefer if the program developers weren't constantly using the bleeding edge versions, but there is no stopping F/LOSS developers.   **RVM mostly rocks.**

Commercial devs, which I was for over a decade, learn to avoid the bleeding edge tools so their customers don't get pissed off. Clients seldom want the latest and greatest infrastructure tools.  Running older versions of libraries usually isn't an issue, but running the bleeding edge ones definitely is an issue.

The perl stuff is used for system monitoring, web analytics and dynamic firewall control.  It is all system-based, no bleeding edge stuff there, but I'd use** PerlBrew** if I needed to keep the perl stuff segmented from the system perl libs and programs.  [B]PerlBrew rocks completely.

[/B]I'd like to mark this SOLVED, but it isn't and won't likely be.

---

### Post by renatolipi on 2013-02-18
From the beginning, I did:

```
apt-get update
```

then:

```
sudo aptitude reinstall libxml-libxml-perl
```

I didn't accept the first option aptitude gave me (removing this package). So it gave me another choice:

```
     Install the following packages:                                                              
1)     libxml-sax-base-perl [1.07-1 (precise)]                                                    
2)     libxml-sax-expat-perl [0.40-2 (precise)]                                                   
3)     libxml-sax-perl [0.99+dfsg-1 (precise)]                                                    

     Upgrade the following packages:                                                              
4)     libxml-libxml-perl [1.70.ds-1 (now) -> 1.89+dfsg-1 (precise)]                              

     Downgrade the following packages:                                                            
5)     libapparmor-perl [2.7.102-0ubuntu3.7 (now, precise-security) -> 2.7.102-0ubuntu3 (precise)]
6)     libperl5.14 [5.14.2-6ubuntu2.2 (now, precise-security) -> 5.14.2-6ubuntu2 (precise)]       
7)     perl [5.14.2-6ubuntu2.2 (now, precise-security) -> 5.14.2-6ubuntu2 (precise)]              
8)     perl-base [5.14.2-6ubuntu2.2 (now, precise-security) -> 5.14.2-6ubuntu2 (precise)]         
9)     perl-modules [5.14.2-6ubuntu2.2 (now, precise-security) -> 5.14.2-6ubuntu2 (precise)] 
```


It worked for me!

---

### Post by renatolipi on 2013-03-06
Sorry, Idon't know how to mark it as solved.

---

