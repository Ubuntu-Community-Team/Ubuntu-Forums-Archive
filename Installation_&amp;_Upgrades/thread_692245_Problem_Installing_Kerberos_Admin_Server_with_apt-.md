---
title: "Problem Installing Kerberos Admin Server with apt-get"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by trimnell on 2008-02-09
Hello,

I am new to using apt-get and Kerberos, but have read much of the documentation I could find on the web.  I am trying to install a Kerberos admin server on Ubuntu.  I have run apt-get update and tried numerous times to install krb5-admin-server.  Each time the install apparently aborts because it could not find the daemon: kadmind.  I remove krb5-admin-server with the --purge option inbetween every attempt to reinstall and always have the same outcome.  The messages are below.

Can anyone tell me what I am doing wrong?  Is there a dependency that must be installed preceding this installation?

With all sincere gratitude for any assistance.

--Angus B. Atkins-Trimnell


>>>>>>>>>>>>>>>>>> installation messages below <<<<<<<<<<<<<<<<<<


root@ubudbase:/# apt-get install krb5-admin-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  krb5-kdc
The following NEW packages will be installed:
  krb5-admin-server krb5-kdc
0 upgraded, 2 newly installed, 0 to remove and 24 not upgraded.
Need to get 0B/253kB of archives.
After unpacking 782kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Package configuration                                                         
                                                                              
                                                                              
                                                                              
                                                                              
 ââââââââââââââââââââââ¤ Configuring krb5-admin-server ââââââââââââââââââââââ[7;2Hâ                                                                         ââ Setting up a Kerberos Realm                                             â  
 â                                                                         â  
 â This package contains the administrative tools required to run the      â  
 â Kerberos master server.                                                 â  
 â                                                                         â  
 â However, installing this package does not automatically set up a        â  
 â Kerberos realm.  This can be done later by running the "krb5_newrealm"  â  
 â command.                                                                â  
 â                                                                         â  
 â Please also read the /usr/share/doc/krb5-kdc/README.KDC file and the    â  
 â administration guide found in the krb5-doc package.                     â  
 â                                                                         â  
 â                                 <Ok>                                    â  
 â                                                                         â  
 âââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââ  
                                                                              
                                                                              
                                                                              
                                                                              
Selecting previously deselected package krb5-kdc.                            
(Reading database ... 82188 files and directories currently installed.)
Unpacking krb5-kdc (from .../krb5-kdc_1.6.dfsg.1-7build1_i386.deb) ...
Selecting previously deselected package krb5-admin-server.
Unpacking krb5-admin-server (from .../krb5-admin-server_1.6.dfsg.1-7build1_i386.deb) ...
Setting up krb5-kdc (1.6.dfsg.1-7build1) ...

Setting up krb5-admin-server (1.6.dfsg.1-7build1) ...
kadmind: No such file or directory while initializing, aborting

---

### Post by trimnell on 2008-02-10
Update:

I did a little poking around and checked the krb5-admin-server script, which identifies the DAEMON as  /usr/sbin/kadmind.  I ran ls and the file is there!!  I am more confused than ever.  I've checked all of the locations in the script and they are there.

Still wondering and scanning the web for answers.

--Angus B. Atkins-Trimnell

---

### Post by trimnell on 2008-02-14
I seem to have cured the problem.  I had to remove krb-admin-server, then create a KDC and reinstall.

Angus

---

