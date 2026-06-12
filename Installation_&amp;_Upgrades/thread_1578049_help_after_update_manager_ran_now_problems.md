---
title: "help after update manager ran now problems"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by tyzerised on 2010-09-19
Hi after running update manager on 9.10 I am now getting the following in synaptic package manager when I run it, appreciate any help that can be offered,I am a noob to ubuntu so please be gentle!!
                     p { margin-bottom: 0.21cm; }  debconf: Perl may be unconfigured (Can't locate List/Util.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perl/5.10/Scalar/Util.pm line 12. 
 Compilation failed in require at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 Compilation failed in require at /usr/share/perl/5.10/fields.pm line 122. 
 Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10. 
 Compilation failed in require at (eval 1) line 4. 
 BEGIN failed--compilation aborted at (eval 1) line 4. 
 ) -- aborting 
 (Reading database ... 156361 files and directories currently installed.) 
 Preparing to replace samba 2:3.4.0-3ubuntu5.6 (using .../samba_2%3a3.4.0-3ubuntu5.7_i386.deb) ... 
 Unpacking replacement samba ... 
 Can't locate List/Util.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perl/5.10/Scalar/Util.pm line 12. 
 Compilation failed in require at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 Compilation failed in require at /usr/share/perl/5.10/fields.pm line 122. 
 Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10. 
 Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7. 
 BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7. 
 Compilation failed in require at /usr/share/debconf/frontend line 6. 
 BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6. 
 dpkg: warning: old post-removal script returned error exit status 2 
 dpkg - trying script from the new package instead ... 
 Can't locate List/Util.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perl/5.10/Scalar/Util.pm line 12. 
 Compilation failed in require at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 Compilation failed in require at /usr/share/perl/5.10/fields.pm line 122. 
 Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10. 
 Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7. 
 BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7. 
 Compilation failed in require at /usr/share/debconf/frontend line 6. 
 BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6. 
 dpkg: error processing /var/cache/apt/archives/samba_2%3a3.4.0-3ubuntu5.7_i386.deb (--unpack): 
  subprocess new post-removal script returned error exit status 2 
 Can't locate List/Util.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perl/5.10/Scalar/Util.pm line 12. 
 Compilation failed in require at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 Compilation failed in require at /usr/share/perl/5.10/fields.pm line 122. 
 Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10. 
 Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7. 
 BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7. 
 Compilation failed in require at /usr/share/debconf/frontend line 6. 
 BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6. 
 dpkg: error while cleaning up: 
  subprocess new post-removal script returned error exit status 2 
 Processing triggers for man-db ... 
 Processing triggers for ureadahead ... 
 Errors were encountered while processing: 
  /var/cache/apt/archives/samba_2%3a3.4.0-3ubuntu5.7_i386.deb 
 E: Sub-process /usr/bin/dpkg returned an error code (1) 
 A package failed to install.  Trying to recover: 
 Setting up update-inetd (4.31) ... 
 Can't locate List/Util.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perl/5.10/Scalar/Util.pm line 12. 
 Compilation failed in require at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 Compilation failed in require at /usr/share/perl/5.10/fields.pm line 122. 
 Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10. 
 Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7. 
 BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7. 
 Compilation failed in require at /usr/share/debconf/frontend line 6. 
 BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6. 
 dpkg: error processing update-inetd (--configure): 
  subprocess installed post-installation script returned error exit status 2 
 Setting up linux-headers-2.6.31-22-generic (2.6.31-22.65) ... 
 Examining /etc/kernel/header_postinst.d. 
 run-parts: executing /etc/kernel/header_postinst.d/dkms 
  * Running DKMS auto installation service for kernel 2.6.31-22-generic 
  
  *  nvidia (96.43.13)... 
 nvidia (96.43.13): Already installed on this kernel. 
    ...done. 
 run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 
 Can't locate List/Util.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perl/5.10/Scalar/Util.pm line 12. 
 Compilation failed in require at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 Compilation failed in require at /usr/share/perl/5.10/fields.pm line 122. 
 Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10. 
 Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7. 
 BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7. 
 Compilation failed in require at /usr/share/debconf/frontend line 6. 
 BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6. 
 run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 2 
 Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.31-22-generic.postinst line 110. 
 dpkg: error processing linux-headers-2.6.31-22-generic (--configure): 
  subprocess installed post-installation script returned error exit status 2 
 Setting up samba-common (2:3.4.0-3ubuntu5.7) ... 
 Can't locate List/Util.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perl/5.10/Scalar/Util.pm line 12. 
 Compilation failed in require at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 Compilation failed in require at /usr/share/perl/5.10/fields.pm line 122. 
 Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10. 
 Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7. 
 BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7. 
 Compilation failed in require at /usr/share/debconf/frontend line 6. 
 BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6. 
 dpkg: error processing samba-common (--configure): 
  subprocess installed post-installation script returned error exit status 2 
 dpkg: dependency problems prevent configuration of smbclient: 
  smbclient depends on samba-common (= 2:3.4.0-3ubuntu5.7); however: 
   Package samba-common is not configured yet. 
 dpkg: error processing smbclient (--configure): 
  dependency problems - leaving unconfigured 
 Setting up ufw (0.29-4ubuntu1) ... 
 Can't locate List/Util.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perl/5.10/Scalar/Util.pm line 12. 
 Compilation failed in require at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 Compilation failed in require at /usr/share/perl/5.10/fields.pm line 122. 
 Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10. 
 Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7. 
 BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7. 
 Compilation failed in require at /usr/share/debconf/frontend line 6. 
 BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6. 
 dpkg: error processing ufw (--configure): 
  subprocess installed post-installation script returned error exit status 2 
 dpkg: dependency problems prevent configuration of samba-common-bin: 
  samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however: 
   Package samba-common is not configured yet. 
 dpkg: error processing samba-common-bin (--configure): 
  dependency problems - leaving unconfigured 
 Setting up libapache2-mod-php5 (5.2.10.dfsg.1-2ubuntu6.4) ... 
 Can't locate List/Util.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perl/5.10/Scalar/Util.pm line 12. 
 Compilation failed in require at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 BEGIN failed--compilation aborted at /usr/lib/perl/5.10/Hash/Util.pm line 8. 
 Compilation failed in require at /usr/share/perl/5.10/fields.pm line 122. 
 Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10. 
 Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7. 
 BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7. 
 Compilation failed in require at /usr/share/debconf/frontend line 6. 
 BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6. 
 dpkg: error processing libapache2-mod-php5 (--configure): 
  subprocess installed post-installation script returned error exit status 2 
 dpkg: dependency problems prevent configuration of php5: 
  php5 depends on libapache2-mod-php5 (>= 5.2.10.dfsg.1-2ubuntu6.4) | libapache2-mod-php5filter (>= 5.2.10.dfsg.1-2ubuntu6.4) | php5-cgi (>= 5.2.10.dfsg.1-2ubuntu6.4); however: 
   Package libapache2-mod-php5 is not configured yet. 
   Package libapache2-mod-php5filter is not installed. 
   Package php5-cgi is not installed. 
 dpkg: error processing php5 (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of davical: 
  davical depends on php5; however: 
   Package php5 is not configured yet. 
 dpkg: error processing davical (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of php5-pgsql: 
  php5-pgsql depends on php5 | phpapi-20060613+lfs; however: 
   Package php5 is not configured yet. 
   Package phpapi-20060613+lfs is not installed. 
   Package libapache2-mod-php5 which provides phpapi-20060613+lfs is not configured yet. 
 dpkg: error processing php5-pgsql (--configure): 
  dependency problems - leaving unconfigured 
 Errors were encountered while processing: 
  update-inetd 
  linux-headers-2.6.31-22-generic 
  samba-common 
  smbclient 
  ufw 
  samba-common-bin 
  libapache2-mod-php5 
  php5 
  davical 
  php5-pgsql

---

### Post by mörgæs on 2010-09-20
Welcome to the forum.

Try to boot the machine and run

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean
```

---

### Post by tyzerised on 2010-09-20
hi tried this to no avail stil having the same problems software manager not working and update manager not working thanks

---

### Post by mörgæs on 2010-09-20
What happened that put the system in this stage? Please give all details that you know of.


For repairing you could take a look at 

[https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto](https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto)

Apt-get can solve a lot of problems, for example 
```
sudo apt-get -f install
```

---

### Post by tyzerised on 2010-09-20
Hi it all started to go wrong after a recent automatic update, very strange!

---

