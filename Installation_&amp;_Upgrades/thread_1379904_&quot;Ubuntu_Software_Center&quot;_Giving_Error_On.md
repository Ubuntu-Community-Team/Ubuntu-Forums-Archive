---
title: "&quot;Ubuntu Software Center&quot; Giving Error On 50%"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by harshsaini on 2010-01-13
I am new to Linux platform,
Whenever i try to install any application via Ubuntu Software Center it gives Error on 50%,
when its applying changes.
i was trying to install "CheckGmail"
and got following error.


> installArchives() failed: Selecting previously deselected package libgtk2-trayicon-perl. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 115471 files and directories currently installed.) 
Unpacking libgtk2-trayicon-perl (from .../libgtk2-trayicon-perl_0.06-1_i386.deb) ... 
Selecting previously deselected package libcrypt-ssleay-perl. 
Unpacking libcrypt-ssleay-perl (from .../libcrypt-ssleay-perl_0.57-1_i386.deb) ... 
Selecting previously deselected package libxml-namespacesupport-perl. 
Unpacking libxml-namespacesupport-perl (from .../libxml-namespacesupport-perl_1.09-3_all.deb) ... 
Selecting previously deselected package libxml-sax-perl. 
Unpacking libxml-sax-perl (from .../libxml-sax-perl_0.96+dfsg-1_all.deb) ... 
Selecting previously deselected package libxml-sax-expat-perl. 
Unpacking libxml-sax-expat-perl (from .../libxml-sax-expat-perl_0.40-1_all.deb) ... 
Selecting previously deselected package libxml-simple-perl. 
Unpacking libxml-simple-perl (from .../libxml-simple-perl_2.18-2_all.deb) ... 
Selecting previously deselected package libcrypt-blowfish-perl. 
Unpacking libcrypt-blowfish-perl (from .../libcrypt-blowfish-perl_2.10-1build2_i386.deb) ... 
Selecting previously deselected package libgtk2-sexy-perl. 
Unpacking libgtk2-sexy-perl (from .../libgtk2-sexy-perl_0.04-1_i386.deb) ... 
Selecting previously deselected package checkgmail. 
Unpacking checkgmail (from .../checkgmail_1.13+svn43-0ubuntu1_all.deb) ... 
Selecting previously deselected package libemail-mime-encodings-perl. 
Unpacking libemail-mime-encodings-perl (from .../libemail-mime-encodings-perl_1.313-1_all.deb) ... 
Selecting previously deselected package libmd5-perl. 
Unpacking libmd5-perl (from .../libmd5-perl_2.03-1_all.deb) ... 
Selecting previously deselected package libcrypt-simple-perl. 
Unpacking libcrypt-simple-perl (from .../libcrypt-simple-perl_0.06-5_all.deb) ... 
Selecting previously deselected package libsexymm2. 
Unpacking libsexymm2 (from .../libsexymm2_0.1.9-5_i386.deb) ... 
Processing triggers for man-db ... 
Processing triggers for desktop-file-utils ... 
Setting up bandwidthd (2.0.1) ... 
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information 
update-rc.d: see <http://wiki.debian.org/LSBInitScripts> 
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected 
invoke-rc.d: initscript bandwidthd, action "start" failed. 
dpkg: error processing bandwidthd (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libgtk2-trayicon-perl (0.06-1) ... 
Setting up libcrypt-ssleay-perl (0.57-1) ... 
Setting up libxml-namespacesupport-perl (1.09-3) ... 
Setting up libxml-sax-perl (0.96+dfsg-1) ... 
update-perl-sax-parsers: Registering Perl SAX parser XML::SAX::PurePerl with priority 10... 
update-perl-sax-parsers: Updating overall Perl SAX parser modules info file... 
 
Creating config file /etc/perl/XML/SAX/ParserDetails.ini with new version 
 
Setting up libxml-sax-expat-perl (0.40-1) ... 
update-perl-sax-parsers: Registering Perl SAX parser XML::SAX::Expat with priority 50... 
update-perl-sax-parsers: Updating overall Perl SAX parser modules info file... 
Replacing config file /etc/perl/XML/SAX/ParserDetails.ini with new version 
 
Setting up libxml-simple-perl (2.18-2) ... 
Setting up libcrypt-blowfish-perl (2.10-1build2) ... 
Setting up libgtk2-sexy-perl (0.04-1) ... 
Setting up checkgmail (1.13+svn43-0ubuntu1) ... 
 
Setting up libemail-mime-encodings-perl (1.313-1) ... 
Setting up libmd5-perl (2.03-1) ... 
Setting up libcrypt-simple-perl (0.06-5) ... 
Setting up libsexymm2 (0.1.9-5) ... 
 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 bandwidthd 

PLS HELP ME!!!!!!:(:(

---

### Post by MelDJ on 2010-01-13
try this in terminal:
sudo dpkg --configure -a

---

### Post by harshsaini on 2010-01-14
> **MelDJ said:**
> try this in terminal:
sudo dpkg --configure -a

I try this but its giving this output:

> harsh@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for harsh: 
dpkg: error processing bandwidthd (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 bandwidthd


But when i try to update it using "Update Manager" then it showing error:
> E: /var/cache/apt/archives/bandwidthd_2.0.1+cvs20071208-3_i386.deb: subprocess new pre-removal script returned error exit status 2


And nothing is installing on my Ubuntu, i cant use "update", cant use "Software center"....
Do i have to Re-Install whole UBUNTU OS again???

PLS HELP ME!!!!

---

### Post by MelDJ on 2010-01-14
try sudo apt-get remvoe bandwidthd
then  sudo dpkg --configure -a
then sudo apt-get install bandwidthd

---

### Post by harshsaini on 2010-01-14
> **MelDJ said:**
> try sudo apt-get remvoe bandwidthd
then  sudo dpkg --configure -a
then sudo apt-get install bandwidthd


This is also not working and make things worse,
following output is given by Terminal:
> harsh@ubuntu:~$ sudo apt-get remove bandwidthd
[sudo] password for harsh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bandwidthd
0 upgraded, 0 newly installed, 1 to remove and 176 not upgraded.
1 not fully installed or removed.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? y

dpkg: error processing bandwidthd (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bandwidthd
E: Sub-process /usr/bin/dpkg returned an error code (1)
harsh@ubuntu:~$ sudo dpkg --configure -a
harsh@ubuntu:~$ sudo apt-get install bandwidthd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bandwidthd
1 upgraded, 0 newly installed, 0 to remove and 176 not upgraded.
1 not fully installed or removed.
Need to get 0B/71.8kB of archives.
After this operation, 57.3kB of additional disk space will be used.
Preconfiguring packages ...
cp: cannot stat `/usr/share/doc/bandwidthd/bandwidthd.conf': No such file or directory
bandwidthd failed to preconfigure, with exit status 1
Selecting previously deselected package bandwidthd.
(Reading database ... 116181 files and directories currently installed.)
Preparing to replace bandwidthd 2.0.1 (using .../bandwidthd_2.0.1+cvs20071208-3_i386.deb) ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bandwidthd_2.0.1+cvs20071208-3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bandwidthd_2.0.1+cvs20071208-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
And when i try to install anything then giving this error:
> E:I wasn't able to locate file for the bandwidthd package. This might mean you need to manually fix this package.:

Now what should i do????:(:(

I also tried from "Synaptic Package Manager", but nothing can be done from there too..
Suggest some thing......

---

### Post by Joeb454 on 2010-01-14
Another thing to try (off the top of my head) is ```
sudo apt-get install -f
```....I think that's right :)

---

### Post by Sef on 2010-01-14
>  	Quote:
 	 	 		 			 				 					Originally Posted by **MelDJ** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8662191#post8662191") 				
 				[I]try ```
sudo apt-get remvoe bandwidthd
then  sudo dpkg --configure -a
then sudo apt-get install bandwidthd
```[/I]
 			 		 	 	 

This is also not working 

It would not work because remove is misspelled. It should be this:

```
sudo apt-get remove bandwidthd

sudo dpkg --configure -a

  sudo apt-get install bandwidthd
```

---

### Post by MelDJ on 2010-01-14
> **Sef said:**
> It would not work because remove is misspelled. It should be this:

```
sudo apt-get remove bandwidthd

sudo dpkg --configure -a

  sudo apt-get install bandwidthd
```

op has already done that with the correct spelling..see post number 5

---

