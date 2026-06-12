---
title: "apt-get upgrade problems. Please Help."
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by acolic on 2006-07-21
Hi,

last night I ran apt-get update and apt-get upgrade. A lot of packages needed to be upgraded. The packages were properly downloaded but while they were being installed a lot of errors flashed by the screen. Afterwards I tried to run apt-get upgrade again to see if everything was correctly upgraded.

I get a lot of dependancy errors dealing with samba and slapd. As a result apt-get no longer works properly. I cannot remove or add any other files. To fix the dependancy error I tried apt-get -f install, no luck.

Can someone tell me what the solution to the below error is.

Thanks

Alex


Reading package lists... Done
acolic@Sirius:/var/log$ sudo apt-get upgrade Reading package lists... Done Building dependency tree... Done You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.22-1ubuntu3) but 3.0.22-1ubuntu3.1 is installed
  slapd: Depends: libldap-2.2-7 (= 2.2.26-5ubuntu2) but 2.2.26-5ubuntu2.1 is installed
E: Unmet dependencies. Try using -f.
acolic@Sirius:/var/log$ sudo apt-get -f install Reading package lists... Done Building dependency tree... Done Correcting dependencies... Done The following extra packages will be installed:
  samba slapd
Suggested packages:
  ldap-utils
Recommended packages:
  smbldap-tools db4.2-util
The following packages will be upgraded:
  samba slapd
2 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
78 not fully installed or removed.
Need to get 0B/39.4MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 1) line 2.
BEGIN failed--compilation aborted at (eval 1) line 2.
) -- aborting
(Reading database ...
dpkg: serious warning: files list file for package `bittorrent' missing, assuming package has no files currently installed.
75700 files and directories currently installed.) Preparing to replace slapd 2.2.26-5ubuntu2 (using .../slapd_2.2.26-5ubuntu2.1_i386.deb) ...
/var/lib/dpkg/tmp.ci/preinst: line 5: /usr/share/debconf/confmodule: No such file or directory
dpkg: error processing /var/cache/apt/archives/slapd_2.2.26-5ubuntu2.1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1 Preparing to replace mysql-server-5.0 5.0.21-3ubuntu1 (using .../mysql-server-5.0_5.0.21-3ubuntu1_i386.deb) ...
/var/lib/dpkg/info/mysql-server-5.0.prerm: line 3: /usr/share/debconf/confmodule: No such file or directory
dpkg: warning - old pre-removal script returned error exit status 1 dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: line 3: /usr/share/debconf/confmodule: No such file or directory
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.21-3ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
/var/lib/dpkg/info/mysql-server-5.0.postinst: line 3: /usr/share/debconf/confmodule: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1 Preparing to replace openoffice.org-writer 2.0.2-2ubuntu12 (using .../openoffice.org-writer_2.0.2-2ubuntu12_i386.deb) ...
Unpacking replacement openoffice.org-writer ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: warning - old post-removal script returned error exit status 2 dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error processing /var/cache/apt/archives/openoffice.org-writer_2.0.2-2ubuntu12_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2 Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2 Preparing to replace openoffice.org-calc 2.0.2-2ubuntu12 (using .../openoffice.org-calc_2.0.2-2ubuntu12_i386.deb) ...
Unpacking replacement openoffice.org-calc ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: warning - old post-removal script returned error exit status 2 dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error processing /var/cache/apt/archives/openoffice.org-calc_2.0.2-2ubuntu12_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2 Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2 Preparing to replace openoffice.org-draw 2.0.2-2ubuntu12 (using .../openoffice.org-draw_2.0.2-2ubuntu12_i386.deb) ...
Unpacking replacement openoffice.org-draw ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: warning - old post-removal script returned error exit status 2 dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error processing /var/cache/apt/archives/openoffice.org-draw_2.0.2-2ubuntu12_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2 Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2 Preparing to replace openoffice.org-impress 2.0.2-2ubuntu12 (using .../openoffice.org-impress_2.0.2-2ubuntu12_i386.deb) ...
Unpacking replacement openoffice.org-impress ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: warning - old post-removal script returned error exit status 2 dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error processing /var/cache/apt/archives/openoffice.org-impress_2.0.2-2ubuntu12_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2 Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2 Preparing to replace openoffice.org-math 2.0.2-2ubuntu12 (using .../openoffice.org-math_2.0.2-2ubuntu12_i386.deb) ...
Unpacking replacement openoffice.org-math ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: warning - old post-removal script returned error exit status 2 dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error processing /var/cache/apt/archives/openoffice.org-math_2.0.2-2ubuntu12_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2 Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2 Preparing to replace openoffice.org-base 2.0.2-2ubuntu12 (using .../openoffice.org-base_2.0.2-2ubuntu12_i386.deb) ...
Unpacking replacement openoffice.org-base ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: warning - old post-removal script returned error exit status 2 dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error processing /var/cache/apt/archives/openoffice.org-base_2.0.2-2ubuntu12_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2 Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2 Preparing to replace samba 3.0.22-1ubuntu3 (using .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
Unpacking replacement samba ...
Can't locate DebianNet.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-inetd line 23.
dpkg: warning - old post-removal script returned error exit status 2 dpkg - trying script from the new package instead ...
Can't locate DebianNet.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-inetd line 23.
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2 Can't locate DebianNet.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-inetd line 23.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2 Errors were encountered while processing:
 /var/cache/apt/archives/slapd_2.2.26-5ubuntu2.1_i386.deb
 /var/cache/apt/archives/mysql-server-5.0_5.0.21-3ubuntu1_i386.deb
 /var/cache/apt/archives/openoffice.org-writer_2.0.2-2ubuntu12_i386.deb
 /var/cache/apt/archives/openoffice.org-calc_2.0.2-2ubuntu12_i386.deb
 /var/cache/apt/archives/openoffice.org-draw_2.0.2-2ubuntu12_i386.deb
 /var/cache/apt/archives/openoffice.org-impress_2.0.2-2ubuntu12_i386.deb
 /var/cache/apt/archives/openoffice.org-math_2.0.2-2ubuntu12_i386.deb
 /var/cache/apt/archives/openoffice.org-base_2.0.2-2ubuntu12_i386.deb
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg

---

### Post by stricevics on 2006-07-21
> **acolic said:**
> Hi,

last night I ran apt-get update and apt-get upgrade. A lot of packages needed to be upgraded. The packages were properly downloaded but while they were being installed a lot of errors flashed by the screen. Afterwards I tried to run apt-get upgrade again to see if everything was correctly upgraded.

I get a lot of dependancy errors dealing with samba and slapd. As a result apt-get no longer works properly. I cannot remove or add any other files. To fix the dependancy error I tried apt-get -f install, no luck.

Can someone tell me what the solution to the below error is.

Thanks

Alex


Maybe you can try [FONT="Courier New"]aptitude[/FONT]. As far as I know, [FONT="Courier New"]aptitude[/FONT] should handle dependencies way better than [FONT="Courier New"]apt-get[/FONT].

I guess, if all that has happened to me, I'd try [FONT="Courier New"]aptitude[/FONT] as my next step.

Hope it helps.

---

### Post by acolic on 2006-07-21
Hi,

I tried aptitude. It still tries to upgrade Samba and SLAPD and then fails because of dependencies.

I've tried to reinstall both apps but that fails.

Any way for me to make ubuntu to think that they are not installed so I can do a fresh install of them?

Alex

---

### Post by stricevics on 2006-07-22
> **acolic said:**
> Hi,

I tried aptitude. It still tries to upgrade Samba and SLAPD and then fails because of dependencies.

I've tried to reinstall both apps but that fails.

Any way for me to make ubuntu to think that they are not installed so I can do a fresh install of them?

Alex

OK, have you tried Synaptic? Depending on the state of each package, you can preform certain operations, ie. reinstall, remove, completely remove, install, ...

Because it is GUI tool, it may be easier for you to comprehend what and where went wrong.

I have no idea if this is actually going to work, but it may so that's why I'm posting it. Hope it helps. :)

---

### Post by FredB on 2006-07-23
another idea : try dpkg -configure --a ?!

---

### Post by doctor567 on 2006-10-18
I had this same problem and here's what I did to fix it:

# apt-get remove slapd 

Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  slapd
0 upgraded, 0 newly installed, 1 to remove and 29 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: serious warning: files list file for package `slapd' missing, assuming package has no files currently installed.
18570 files and directories currently installed.)
Removing slapd ...


# aptitude install slapd

Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  db4.2-util 
The following packages have been kept back:
  bind9-host cpio dnsutils gzip libapache2-mod-php5 libbind9-0 libdns21 libgnutls12 libisc11 libisccc0 libisccfg1 libkrb53 liblwres9 libmysqlclient15off libssl0.9.8 
  linux-image-2.6.15-26-server linux-image-server linux-server mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 openssh-client openssl php5-common 
  php5-mysql php5-mysqli python2.4 python2.4-minimal 
The following NEW packages will be installed:
  db4.2-util slapd 
0 packages upgraded, 2 newly installed, 0 to remove and 29 not upgraded.
Need to get 58.1kB/931kB of archives. After unpacking 2671kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main db4.2-util 4.2.52-24build1 [58.1kB]
Fetched 58.1kB in 1s (43.6kB/s)    
Preconfiguring packages ...

(configuration screens omitted)

Selecting previously deselected package slapd.                                                                                                                          
(Reading database ... 18570 files and directories currently installed.)
Unpacking slapd (from .../slapd_2.2.26-5ubuntu2.1_i386.deb) ...
Selecting previously deselected package db4.2-util.
Unpacking db4.2-util (from .../db4.2-util_4.2.52-24build1_i386.deb) ...
Setting up slapd (2.2.26-5ubuntu2.1) ...
  Creating initial slapd configuration... done.
  Creating initial LDAP directory... done.
Starting OpenLDAP: running BDB recovery, slapd.

Setting up db4.2-util (4.2.52-24build1) ...

-------- snip --------

After this it worked.

---

