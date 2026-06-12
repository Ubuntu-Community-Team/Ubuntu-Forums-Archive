---
title: "Problems installing apps-Lilypond errors?"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by sdb2028 on 2006-02-22
I have run into a problem installing applications, I keep getting these errors refering to lilypond. When I try to install this lillypond thing, these are the errors I get:

Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  lilypond-doc
The following NEW packages will be installed:
  lilypond
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1129kB of archives.
After unpacking 2974kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 87852 files and directories currently installed.)
Unpacking lilypond (from .../lilypond_2.6.3-9~breezy1_i386.deb) ...
/var/lib/dpkg/tmp.ci/preinst: line 19: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Also, when I try to install an app which needs to be compiled first, I get this error:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

I have try'd to install the compilers, says they are already installed.

???????????????????????:confused:

---

### Post by Greg2 on 2006-02-22
There is a known bug in the lilypond-data package that has been reported. Please read my post in this thread to uninstall the package, and fix the problem:
[http://ubuntuforums.org/showthread.php?t=111991&page=3](http://ubuntuforums.org/showthread.php?t=111991&page=3)
Then in terminal do:```
sudo apt-get install build-essential
```to install the gcc and g++ compilers.

---

### Post by sdb2028 on 2006-02-22
Thanks for the input Greg,

I went to that thread, made the kpsewhich file and ran "sudo apt-get install -f" and here is what I got:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up lilypond-data (2.6.3-9~breezy1) ...
/var/lib/dpkg/info/lilypond-data.postinst: line 15: /usr/bin/kpsewhich: Permission denied
dpkg: error processing lilypond-data (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lilypond-data
E: Sub-process /usr/bin/dpkg returned an error code (1)

Now what?????

---

### Post by sdb2028 on 2006-02-22
Just read the rest of the thread, I'll try that:
BRB

---

### Post by sdb2028 on 2006-02-22
Thaks Greg, It worked.

---

### Post by sdb2028 on 2006-02-22
Getting closer!! But still stuck.

Now here is what I get when I try to configure an applicatin in terminal:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

---

### Post by Greg2 on 2006-02-22
Now you will need to install the perl packages the app needs to compile, which should be listed in the readme.txt or the install.txt of the source tarball.

They are probably perl, libperl and libperl-dev.

---

### Post by Greg2 on 2006-02-22
[QUOTE=sdb2028]Getting closer!! But still stuck.

Now here is what I get when I try to configure an applicatin in terminal:

-snip-

checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool[/QUOTE]
It would help to know what you are trying to build? However, you may want to try installing libxml-parser-perl (with synaptic or apt-get) with the other depends I’ve listed.

---

### Post by sdb2028 on 2006-02-22
Trying to build gnucash 1.8.12, 
OK, got the parser installed, now I get:
          configure: error: Cannot find ltdl.h -- libtool-devel not installed?

I try to install libtool, and get this:
           Reading package lists... Done
           Building dependency tree... Done
           libtool is already the newest version.
           0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Thanks for your help, were getting closer.

---

### Post by Greg2 on 2006-02-22
[QUOTE=sdb2028]Trying to build gnucash 1.8.12[/QUOTE]
OK... here&#8217;s the depends, and where to find them:
[http://www.gnucash.org/en/required.phtml](http://www.gnucash.org/en/required.phtml)
Please note; that if the dependencies aren&#8217;t in the repos... you will have to find them somewhere else, or compile them also. :)

Edit: I just took a look in the repos... and gnucash 1.8.10-18 is available with your package manager.

---

### Post by sdb2028 on 2006-02-22
Thanks for the info, but exactly what am I looking for?

---

### Post by Greg2 on 2006-02-22
[QUOTE=sdb2028]Thanks for the info, but exactly what am I looking for?[/QUOTE]
Just go to System> Administration> Synaptic Package Manager and install gnucash. :???:

---

### Post by sdb2028 on 2006-02-22
Iv'e done that twicw, it installed - but there was no way that I ould find to run the application

---

### Post by sdb2028 on 2006-02-22
try'd it again from synaptic, it worked this time. Its up and running.
Thanks,

---

### Post by Greg2 on 2006-02-22
[QUOTE=sdb2028]but there was no way that I ould find to run the application[/QUOTE]I don’t think that synaptic makes a menu entry for it?

If you need one: Go to Applications> System Tools> Applications Menu Editor> Other> New Entry and on the Name line add ‘GnuCash’, on the command line add ‘gnucash’ (without quotes), click on icon and go to /usr/share/pixmaps/gnucash/gnucash-icon.png and open. Click OK and close the editor.

Now it should be in your menu and ready to use.

---

