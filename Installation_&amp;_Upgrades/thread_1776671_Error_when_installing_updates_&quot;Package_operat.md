---
title: "Error when installing updates: &quot;Package operation failed&quot;"
date: 2011-06-06
forum: Installation &amp; Upgrades
---

### Post by marsgorski on 2011-06-06
Hi everyone. Ever since I upgraded to Natty I have been getting errors when downloading and installing updates. Usually there is something related to samba4. Today, I got the following output from the error box:

```

installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55331 package 'virtualbox-3.1': 
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55332 package 'virtualbox-3.1': 
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 23520 package 'jre': 
 error in Version string '1.6.0_14-fcs-1': invalid character in version number 
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 57682 package 'virtualbox-3.1': 
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 399368 files and directories currently installed.) 
Preparing to replace google-chrome-stable 11.0.696.71-r86024 (using .../google-chrome-stable_11.0.696.77-r87952_i386.deb) ... 
Unpacking replacement google-chrome-stable ... 
Preparing to replace sudo 1.7.4p4-5ubuntu7 (using .../sudo_1.7.4p4-5ubuntu7.1_i386.deb) ... 
Unpacking replacement sudo ... 
Preparing to replace python-apt-common 0.7.100.3ubuntu6 (using .../python-apt-common_0.7.100.3ubuntu6.1_all.deb) ... 
Unpacking replacement python-apt-common ... 
Preparing to replace python-apt 0.7.100.3ubuntu6 (using .../python-apt_0.7.100.3ubuntu6.1_i386.deb) ... 
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 55331 package 'virtualbox-3.1': 
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 55332 package 'virtualbox-3.1': 
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
Unpacking replacement python-apt ... 
Preparing to replace adobe-flash-properties-gtk 10.3.181.14-0natty1 (using .../adobe-flash-properties-gtk_10.3.181.22-0natty1_i386.deb) ... 
Unpacking replacement adobe-flash-properties-gtk ... 
Preparing to replace adobe-flashplugin 10.3.181.14-0natty1 (using .../adobe-flashplugin_10.3.181.22-0natty1_i386.deb) ... 
Unpacking replacement adobe-flashplugin ... 
Preparing to replace libcups2-dev 1.4.6-5ubuntu1 (using .../libcups2-dev_1.4.6-5ubuntu1.1_i386.deb) ... 
Unpacking replacement libcups2-dev ... 
Preparing to replace libcups2 1.4.6-5ubuntu1 (using .../libcups2_1.4.6-5ubuntu1.1_i386.deb) ... 
Unpacking replacement libcups2 ... 
Preparing to replace libcupscgi1 1.4.6-5ubuntu1 (using .../libcupscgi1_1.4.6-5ubuntu1.1_i386.deb) ... 
Unpacking replacement libcupscgi1 ... 
Preparing to replace libcupsdriver1 1.4.6-5ubuntu1 (using .../libcupsdriver1_1.4.6-5ubuntu1.1_i386.deb) ... 
Unpacking replacement libcupsdriver1 ... 
Preparing to replace libcupsimage2 1.4.6-5ubuntu1 (using .../libcupsimage2_1.4.6-5ubuntu1.1_i386.deb) ... 
Unpacking replacement libcupsimage2 ... 
Preparing to replace libcupsmime1 1.4.6-5ubuntu1 (using .../libcupsmime1_1.4.6-5ubuntu1.1_i386.deb) ... 
Unpacking replacement libcupsmime1 ... 
Preparing to replace libcupsppdc1 1.4.6-5ubuntu1 (using .../libcupsppdc1_1.4.6-5ubuntu1.1_i386.deb) ... 
Unpacking replacement libcupsppdc1 ... 
Preparing to replace cups-common 1.4.6-5ubuntu1 (using .../cups-common_1.4.6-5ubuntu1.1_all.deb) ... 
Unpacking replacement cups-common ... 
Preparing to replace cups-bsd 1.4.6-5ubuntu1 (using .../cups-bsd_1.4.6-5ubuntu1.1_i386.deb) ... 
Unpacking replacement cups-bsd ... 
Preparing to replace cups-client 1.4.6-5ubuntu1 (using .../cups-client_1.4.6-5ubuntu1.1_i386.deb) ... 
Unpacking replacement cups-client ... 
Preparing to replace cups-ppdc 1.4.6-5ubuntu1 (using .../cups-ppdc_1.4.6-5ubuntu1.1_i386.deb) ... 
Unpacking replacement cups-ppdc ... 
Preparing to replace cups 1.4.6-5ubuntu1 (using .../cups_1.4.6-5ubuntu1.1_i386.deb) ... 
cups stop/waiting 
Unpacking replacement cups ... 
Preparing to replace cupsddk 1.4.6-5ubuntu1 (using .../cupsddk_1.4.6-5ubuntu1.1_all.deb) ... 
Unpacking replacement cupsddk ... 
Preparing to replace subversion 1.6.12dfsg-4ubuntu2 (using .../subversion_1.6.12dfsg-4ubuntu2.1_i386.deb) ... 
Unpacking replacement subversion ... 
Preparing to replace libsvn1 1.6.12dfsg-4ubuntu2 (using .../libsvn1_1.6.12dfsg-4ubuntu2.1_i386.deb) ... 
Unpacking replacement libsvn1 ... 
Processing triggers for man-db ... 
Processing triggers for menu ... 
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 55331 package 'virtualbox-3.1': 
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 55332 package 'virtualbox-3.1': 
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for ureadahead ... 
ureadahead will be reprofiled on next reboot 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for ufw ... 
Processing triggers for doc-base ... 
Processing 1 changed doc-base file(s)... 
Registering documents with scrollkeeper... 
Processing triggers for python-support ... 
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55347 package 'virtualbox-3.1': 
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55348 package 'virtualbox-3.1': 
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
Setting up samba4 (4.0.0~alpha15~git20110124.dfsg1-2ubuntu1) ... 
Unknown parameter encountered: "max log size" 
Ignoring unknown parameter "max log size" 
Unknown parameter encountered: "syslog" 
Ignoring unknown parameter "syslog" 
Unknown parameter encountered: "passdb backend" 
Ignoring unknown parameter "passdb backend" 
Unknown parameter encountered: "unix password sync" 
Ignoring unknown parameter "unix password sync" 
Unknown parameter encountered: "passwd program" 
Ignoring unknown parameter "passwd program" 
Unknown parameter encountered: "pam password change" 
Ignoring unknown parameter "pam password change" 
Unknown parameter encountered: "map to guest" 
Ignoring unknown parameter "map to guest" 
Unknown parameter encountered: "usershare allow guests" 
Ignoring unknown parameter "usershare allow guests" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
Unknown parameter encountered: "max log size" 
Ignoring unknown parameter "max log size" 
Unknown parameter encountered: "syslog" 
Ignoring unknown parameter "syslog" 
Unknown parameter encountered: "passdb backend" 
Ignoring unknown parameter "passdb backend" 
Unknown parameter encountered: "unix password sync" 
Ignoring unknown parameter "unix password sync" 
Unknown parameter encountered: "passwd program" 
Ignoring unknown parameter "passwd program" 
Unknown parameter encountered: "pam password change" 
Ignoring unknown parameter "pam password change" 
Unknown parameter encountered: "map to guest" 
Ignoring unknown parameter "map to guest" 
Unknown parameter encountered: "usershare allow guests" 
Ignoring unknown parameter "usershare allow guests" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
ldb: unable to stat module /usr/lib/samba/ldb/modules/samba : No such file or directory 
ldb: failed to initialise module /usr/lib/samba/ldb/modules/samba : Unavailable 
ldb: failed to initialise module /usr/lib/samba/ldb/modules : Unavailable 
WARNING: Module [samba_dsdb] not found - do you need to set LDB_MODULES_PATH? 
Unable to load modules for /var/lib/samba/private/sam.ldb: Failed to load modules from: /usr/lib/samba/ldb 
 
Traceback (most recent call last): 
  File "/usr/share/samba/setup/upgradeprovision", line 1597, in <module> 
    ldbs = get_ldbs(paths, creds, session, lp) 
  File "/usr/lib/python2.7/dist-packages/samba/upgradehelpers.py", line 159, in get_ldbs 
    ldbs.sam = SamDB(paths.samdb, session_info=session, credentials=creds, lp=lp, options=["modules:samba_dsdb"]) 
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 53, in __init__ 
    options=options) 
  File "/usr/lib/python2.7/dist-packages/samba/__init__.py", line 110, in __init__ 
    self.connect(url, flags, options) 
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 66, in connect 
    options=options) 
_ldb.LdbError: (80, 'Failed to load modules from: /usr/lib/samba/ldb\n') 
dpkg: error processing samba4 (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up google-chrome-stable (11.0.696.77-r87952) ... 
Setting up sudo (1.7.4p4-5ubuntu7.1) ... 
Setting up python-apt-common (0.7.100.3ubuntu6.1) ... 
Setting up python-apt (0.7.100.3ubuntu6.1) ... 
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 55347 package 'virtualbox-3.1': 
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 55348 package 'virtualbox-3.1': 
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
Setting up adobe-flashplugin (10.3.181.22-0natty1) ... 
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/iceape/plugins/flashplugin-alternative.so (iceape-flashplugin) in auto mode. 
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/iceweasel/plugins/flashplugin-alternative.so (iceweasel-flashplugin) in auto mode. 
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode. 
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/firefox/plugins/flashplugin-alternative.so (firefox-flashplugin) in auto mode. 
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/xulrunner/plugins/flashplugin-alternative.so (xulrunner-flashplugin) in auto mode. 
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/midbrowser/plugins/flashplugin-alternative.so (midbrowser-flashplugin) in auto mode. 
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so (xulrunner-addons-flashplugin) in auto mode. 
Setting up adobe-flash-properties-gtk (10.3.181.22-0natty1) ... 
Setting up libcups2 (1.4.6-5ubuntu1.1) ... 
Setting up libcups2-dev (1.4.6-5ubuntu1.1) ... 
Setting up libcupscgi1 (1.4.6-5ubuntu1.1) ... 
Setting up libcupsdriver1 (1.4.6-5ubuntu1.1) ... 
Setting up libcupsimage2 (1.4.6-5ubuntu1.1) ... 
Setting up libcupsmime1 (1.4.6-5ubuntu1.1) ... 
Setting up libcupsppdc1 (1.4.6-5ubuntu1.1) ... 
Setting up cups-common (1.4.6-5ubuntu1.1) ... 
Setting up cups-client (1.4.6-5ubuntu1.1) ... 
Setting up cups-bsd (1.4.6-5ubuntu1.1) ... 
Setting up cups-ppdc (1.4.6-5ubuntu1.1) ... 
Setting up cups (1.4.6-5ubuntu1.1) ... 
cups start/running, process 4632 
Setting up cupsddk (1.4.6-5ubuntu1.1) ... 
Setting up libsvn1 (1.6.12dfsg-4ubuntu2.1) ... 
Setting up subversion (1.6.12dfsg-4ubuntu2.1) ... 
Processing triggers for menu ... 
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 55347 package 'virtualbox-3.1': 
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 55348 package 'virtualbox-3.1': 
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 samba4 
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55331 package 'virtualbox-3.1': 
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55332 package 'virtualbox-3.1': 
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
Setting up samba4 (4.0.0~alpha15~git20110124.dfsg1-2ubuntu1) ... 
Unknown parameter encountered: "max log size" 
Ignoring unknown parameter "max log size" 
Unknown parameter encountered: "syslog" 
Ignoring unknown parameter "syslog" 
Unknown parameter encountered: "passdb backend" 
Ignoring unknown parameter "passdb backend" 
Unknown parameter encountered: "unix password sync" 
Ignoring unknown parameter "unix password sync" 
Unknown parameter encountered: "passwd program" 
Ignoring unknown parameter "passwd program" 
Unknown parameter encountered: "pam password change" 
Ignoring unknown parameter "pam password change" 
Unknown parameter encountered: "map to guest" 
Ignoring unknown parameter "map to guest" 
Unknown parameter encountered: "usershare allow guests" 
Ignoring unknown parameter "usershare allow guests" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
Unknown parameter encountered: "max log size" 
Ignoring unknown parameter "max log size" 
Unknown parameter encountered: "syslog" 
Ignoring unknown parameter "syslog" 
Unknown parameter encountered: "passdb backend" 
Ignoring unknown parameter "passdb backend" 
Unknown parameter encountered: "unix password sync" 
Ignoring unknown parameter "unix password sync" 
Unknown parameter encountered: "passwd program" 
Ignoring unknown parameter "passwd program" 
Unknown parameter encountered: "pam password change" 
Ignoring unknown parameter "pam password change" 
Unknown parameter encountered: "map to guest" 
Ignoring unknown parameter "map to guest" 
Unknown parameter encountered: "usershare allow guests" 
Ignoring unknown parameter "usershare allow guests" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
ldb: unable to stat module /usr/lib/samba/ldb/modules/samba : No such file or directory 
ldb: failed to initialise module /usr/lib/samba/ldb/modules/samba : Unavailable 
ldb: failed to initialise module /usr/lib/samba/ldb/modules : Unavailable 
WARNING: Module [samba_dsdb] not found - do you need to set LDB_MODULES_PATH? 
Unable to load modules for /var/lib/samba/private/sam.ldb: Failed to load modules from: /usr/lib/samba/ldb 
 
Traceback (most recent call last): 
  File "/usr/share/samba/setup/upgradeprovision", line 1597, in <module> 
    ldbs = get_ldbs(paths, creds, session, lp) 
  File "/usr/lib/python2.7/dist-packages/samba/upgradehelpers.py", line 159, in get_ldbs 
    ldbs.sam = SamDB(paths.samdb, session_info=session, credentials=creds, lp=lp, options=["modules:samba_dsdb"]) 
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 53, in __init__ 
    options=options) 
  File "/usr/lib/python2.7/dist-packages/samba/__init__.py", line 110, in __init__ 
    self.connect(url, flags, options) 
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 66, in connect 
    options=options) 
_ldb.LdbError: (80, 'Failed to load modules from: /usr/lib/samba/ldb\n') 
dpkg: error processing samba4 (--configure): 
 subprocess installed post-installation script returned error exit status 1 

``` I do remember changing the smb.conf file to share files with a windows machine on my network. Thanks for any help.

---

### Post by zvacet on 2011-06-07
```
sudo dpkg --configure -a
```

---

### Post by marsgorski on 2011-06-07
> **zvacet said:**
> ```
sudo dpkg --configure -a
```
Thanks! I'll give this a shot. But what does this command do? Just curious.

---

### Post by zvacet on 2011-06-07
I typed 

```
man dpkg
```

and look what I found

>  --configure package...|-a|--pending
              Configure  a package which has been unpacked but not yet config&#8208;
              ured.  If -a or --pending  is  given  instead  of  package,  all
              unpacked but unconfigured packages are configured.


---

### Post by marsgorski on 2011-06-07
There seems to be an error when I run the command. The output I get is below.

```

marco@marco-laptop:~$ sudo dpkg --configure -a
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55331 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55332 package 'virtualbox-3.1':
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
Setting up samba4 (4.0.0~alpha15~git20110124.dfsg1-2ubuntu1) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ldb: unable to stat module /usr/lib/samba/ldb/modules/samba : No such file or directory
ldb: failed to initialise module /usr/lib/samba/ldb/modules/samba : Unavailable
ldb: failed to initialise module /usr/lib/samba/ldb/modules : Unavailable
WARNING: Module [samba_dsdb] not found - do you need to set LDB_MODULES_PATH?
Unable to load modules for /var/lib/samba/private/sam.ldb: Failed to load modules from: /usr/lib/samba/ldb

Traceback (most recent call last):
  File "/usr/share/samba/setup/upgradeprovision", line 1597, in <module>
    ldbs = get_ldbs(paths, creds, session, lp)
  File "/usr/lib/python2.7/dist-packages/samba/upgradehelpers.py", line 159, in get_ldbs
    ldbs.sam = SamDB(paths.samdb, session_info=session, credentials=creds, lp=lp, options=["modules:samba_dsdb"])
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 53, in __init__
    options=options)
  File "/usr/lib/python2.7/dist-packages/samba/__init__.py", line 110, in __init__
    self.connect(url, flags, options)
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 66, in connect
    options=options)
_ldb.LdbError: (80, 'Failed to load modules from: /usr/lib/samba/ldb\n')
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 samba4

```

Any suggestions?

---

### Post by drs305 on 2011-06-07
the status file may be corrupted. Try using the 'backup' status file:
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
```

---

### Post by marsgorski on 2011-06-07
Thanks! I ran the commands and after the third comand I got 

```

marco@marco-laptop:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://archive.canonical.com natty InRelease                               
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Ign http://us.archive.ubuntu.com natty-security InRelease                      
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://extras.ubuntu.com natty Release                                     
Hit http://archive.canonical.com natty Release                                 
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://us.archive.ubuntu.com natty-security Release.gpg                    
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Hit http://archive.canonical.com natty/partner i386 Packages                   
Hit http://us.archive.ubuntu.com natty Release                                 
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://us.archive.ubuntu.com natty-updates Release                         
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://us.archive.ubuntu.com natty-security Release                        
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/main i386 Packages                      
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                
Hit http://us.archive.ubuntu.com natty/universe i386 Packages                  
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages                
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources              
Hit http://us.archive.ubuntu.com natty-updates/main Sources                    
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages              
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages        
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages          
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages        
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Hit http://us.archive.ubuntu.com natty-security/restricted Sources             
Hit http://us.archive.ubuntu.com natty-security/main Sources                   
Hit http://us.archive.ubuntu.com natty-security/multiverse Sources             
Hit http://us.archive.ubuntu.com natty-security/universe Sources               
Hit http://us.archive.ubuntu.com natty-security/main i386 Packages             
Hit http://us.archive.ubuntu.com natty-security/restricted i386 Packages       
Hit http://us.archive.ubuntu.com natty-security/universe i386 Packages         
Hit http://us.archive.ubuntu.com natty-security/multiverse i386 Packages       
Ign http://us.archive.ubuntu.com natty-security/main TranslationIndex          
Ign http://us.archive.ubuntu.com natty-security/multiverse TranslationIndex    
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://us.archive.ubuntu.com natty-security/restricted TranslationIndex    
Ign http://us.archive.ubuntu.com natty-security/universe TranslationIndex      
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com natty/restricted Translation-en               
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US              
Ign http://us.archive.ubuntu.com natty/universe Translation-en                 
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en         
Ign http://us.archive.ubuntu.com natty-security/main Translation-en_US         
Ign http://us.archive.ubuntu.com natty-security/main Translation-en            
Ign http://us.archive.ubuntu.com natty-security/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com natty-security/multiverse Translation-en      
Ign http://us.archive.ubuntu.com natty-security/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com natty-security/restricted Translation-en      
Ign http://us.archive.ubuntu.com natty-security/universe Translation-en_US     
Ign http://us.archive.ubuntu.com natty-security/universe Translation-en        
Get:2 http://dl.google.com stable Release [1,347 B]                            
Get:3 http://dl.google.com stable/main i386 Packages [1,218 B]                 
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Fetched 2,763 B in 25s (108 B/s)
Reading package lists... Done

```

Do I need to run sudo dpkg --configure -a again? Also, should I run apt-get update more times until there are no more updates? Thanks again.

---

### Post by drs305 on 2011-06-07
> **marsgorski said:**
> Thanks! I ran the commands and after the third comand I got 

Reading package lists... Done
[/CODE]

Do I need to run sudo dpkg --configure -a again? Also, should I run apt-get update more times until there are no more updates? Thanks again.

That command ran correctly but all it does is refresh/update the list of available files. If you want to install the available newer packages, run:
```
sudo apt-get upgrade
```
or do it from whatever GUI you normally use to update your packages. Running it in the terminal at least this once will let you see any errors if they occur.

---

### Post by marsgorski on 2011-06-14
I ran sudo apt-get upgrade and I still seem to get the same errors:
```

marco@marco-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55332 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55333 package 'virtualbox-3.1':
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
Setting up samba4 (4.0.0~alpha15~git20110124.dfsg1-2ubuntu1) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ldb: unable to stat module /usr/lib/samba/ldb/modules/samba : No such file or directory
ldb: failed to initialise module /usr/lib/samba/ldb/modules/samba : Unavailable
ldb: failed to initialise module /usr/lib/samba/ldb/modules : Unavailable
WARNING: Module [samba_dsdb] not found - do you need to set LDB_MODULES_PATH?
Unable to load modules for /var/lib/samba/private/sam.ldb: Failed to load modules from: /usr/lib/samba/ldb

Traceback (most recent call last):
  File "/usr/share/samba/setup/upgradeprovision", line 1597, in <module>
    ldbs = get_ldbs(paths, creds, session, lp)
  File "/usr/lib/python2.7/dist-packages/samba/upgradehelpers.py", line 159, in get_ldbs
    ldbs.sam = SamDB(paths.samdb, session_info=session, credentials=creds, lp=lp, options=["modules:samba_dsdb"])
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 53, in __init__
    options=options)
  File "/usr/lib/python2.7/dist-packages/samba/__init__.py", line 110, in __init__
    self.connect(url, flags, options)
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 66, in connect
    options=options)
_ldb.LdbError: (80, 'Failed to load modules from: /usr/lib/samba/ldb\n')
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I also tried to install zeitgeist activity log manager using [these instructions]("http://www.webupd8.org/2011/05/zeitgeist-activity-log-manager-now.html") for the terminal and I got again the same kind of errors after the command sudo apt-get install activity-log-manager:

```
   	 	 	 	 	 	  marco@marco-laptop:~$ sudo apt-get install activity-log-manager  
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 The following packages were automatically installed and are no longer required: 
   plasma-dataengines-workspace libwildmidi0 byobu kdebase-workspace libtaskmanager4b xulrunner-1.9.2 libkcalutils4 libicu42 freespacenotifier libbcmail-java 
   libsoundtouch1c2 libdbusmenu-glib1 msr-tools g++-4.4 libbcmail-java-gcj plasma-widgets-workspace libdns66 libgps19 libaiksaurus-1.2-0c2a klipper libstdc++6-4.4-dev 
   libeggdbus-1-0 libedata-cal1.2-7 ksysguard libplasma-geolocation-interface4 alsa-oss libexiv2-6 gcj-4.4-jre-lib libgcj10 cpu-checker festlex-cmu libx264-98 
   openoffice.org-style-galaxy libkcalcore4 libksgrd4 libplasmaclock4b gcj-4.4-base libbcprov-java libitext-java libaiksaurus-1.2-data libgnumail-java oss-compat 
   libgwibber0 libdbusmenu-gtk1 systemsettings kdm libkrossui4 festlex-poslex libpoppler7 docbook-xsl-doc-html lm-sensors festvox-kallpc16k python-gnomeapplet 
   fancontrol libgdata7 kinfocenter ttf-dejavu libgnuinet-java ksysguardd libweather-ion6 libxdot4 libisccfg60 plasma-desktop libkholidays4 librsvg2-bin festival 
   libindicate4 libksignalplotter4 firefox-branding libkunitconversion4 libisc60 libnice0 libsyndication4 libebml2 libvala-0.10-0 linux-source-2.6.35 libestools2.0 
   libmatroska2 libitext-java-gcj libkutils4 libiptcdata0 libpoppler-glib5 libgnujaf-java libdmtx0a 
 Use 'apt-get autoremove' to remove them. 
 The following NEW packages will be installed: 
   activity-log-manager 
 0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded. 
 1 not fully installed or removed. 
 Need to get 0 B/16.7 kB of archives. 
 After this operation, 172 kB of additional disk space will be used. 
 dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55332 package 'virtualbox-3.1': 
  error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
 dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55333 package 'virtualbox-3.1': 
  error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
 dpkg: warning: parsing file '/var/lib/dpkg/available' near line 23520 package 'jre': 
  error in Version string '1.6.0_14-fcs-1': invalid character in version number 
 dpkg: warning: parsing file '/var/lib/dpkg/available' near line 57682 package 'virtualbox-3.1': 
  error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
 Selecting previously deselected package activity-log-manager. 
 (Reading database ... 399151 files and directories currently installed.) 
 Unpacking activity-log-manager (from .../activity-log-manager_0.8.0-0ubuntu1~ppa2~natty_all.deb) ... 
 Processing triggers for man-db ... 
 Processing triggers for bamfdaemon ... 
 Rebuilding /usr/share/applications/bamf.index... 
 Processing triggers for desktop-file-utils ... 
 Processing triggers for python-gmenu ... 
 Rebuilding /usr/share/applications/desktop.en_US.utf8.cache... 
 Processing triggers for python-support ... 
 dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55332 package 'virtualbox-3.1': 
  error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
 dpkg: warning: parsing file '/var/lib/dpkg/status' near line 55333 package 'virtualbox-3.1': 
  error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number 
 Setting up samba4 (4.0.0~alpha15~git20110124.dfsg1-2ubuntu1) ... 
 Unknown parameter encountered: "max log size" 
 Ignoring unknown parameter "max log size" 
 Unknown parameter encountered: "syslog" 
 Ignoring unknown parameter "syslog" 
 Unknown parameter encountered: "passdb backend" 
 Ignoring unknown parameter "passdb backend" 
 Unknown parameter encountered: "unix password sync" 
 Ignoring unknown parameter "unix password sync" 
 Unknown parameter encountered: "passwd program" 
 Ignoring unknown parameter "passwd program" 
 Unknown parameter encountered: "pam password change" 
 Ignoring unknown parameter "pam password change" 
 Unknown parameter encountered: "map to guest" 
 Ignoring unknown parameter "map to guest" 
 Unknown parameter encountered: "usershare allow guests" 
 Ignoring unknown parameter "usershare allow guests" 
 Unknown parameter encountered: "guest ok" 
 Ignoring unknown parameter "guest ok" 
 Unknown parameter encountered: "guest ok" 
 Ignoring unknown parameter "guest ok" 
 Unknown parameter encountered: "max log size" 
 Ignoring unknown parameter "max log size" 
 Unknown parameter encountered: "syslog" 
 Ignoring unknown parameter "syslog" 
 Unknown parameter encountered: "passdb backend" 
 Ignoring unknown parameter "passdb backend" 
 Unknown parameter encountered: "unix password sync" 
 Ignoring unknown parameter "unix password sync" 
 Unknown parameter encountered: "passwd program" 
 Ignoring unknown parameter "passwd program" 
 Unknown parameter encountered: "pam password change" 
 Ignoring unknown parameter "pam password change" 
 Unknown parameter encountered: "map to guest" 
 Ignoring unknown parameter "map to guest" 
 Unknown parameter encountered: "usershare allow guests" 
 Ignoring unknown parameter "usershare allow guests" 
 Unknown parameter encountered: "guest ok" 
 Ignoring unknown parameter "guest ok" 
 Unknown parameter encountered: "guest ok" 
 Ignoring unknown parameter "guest ok" 
 ldb: unable to stat module /usr/lib/samba/ldb/modules/samba : No such file or directory 
 ldb: failed to initialise module /usr/lib/samba/ldb/modules/samba : Unavailable 
 ldb: failed to initialise module /usr/lib/samba/ldb/modules : Unavailable 
 WARNING: Module [samba_dsdb] not found - do you need to set LDB_MODULES_PATH? 
 Unable to load modules for /var/lib/samba/private/sam.ldb: Failed to load modules from: /usr/lib/samba/ldb 
  
 Traceback (most recent call last): 
   File "/usr/share/samba/setup/upgradeprovision", line 1597, in <module> 
     ldbs = get_ldbs(paths, creds, session, lp) 
   File "/usr/lib/python2.7/dist-packages/samba/upgradehelpers.py", line 159, in get_ldbs 
     ldbs.sam = SamDB(paths.samdb, session_info=session, credentials=creds, lp=lp, options=["modules:samba_dsdb"]) 
   File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 53, in __init__ 
     options=options) 
   File "/usr/lib/python2.7/dist-packages/samba/__init__.py", line 110, in __init__ 
     self.connect(url, flags, options) 
   File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 66, in connect 
     options=options) 
 _ldb.LdbError: (80, 'Failed to load modules from: /usr/lib/samba/ldb\n') 
 dpkg: error processing samba4 (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 Setting up activity-log-manager (0.8.0-0ubuntu1~ppa2~natty) ... 
 Processing triggers for python-support ... 
 Errors were encountered while processing: 
  samba4 
 E: Sub-process /usr/bin/dpkg returned an error code (1) 
 
```

Apparently, the activity log manager did not install since I was not able to find the folder in the home directory.

---

### Post by marsgorski on 2011-06-23
Does any one have any insight into this problem? Should I even worry about it?

---

### Post by drs305 on 2011-06-23
You could try to clean things up a bit by manually editing some files, especially if you are not using the packages providing the errors.

For the VirtualBox 3.1 status error:

```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.copy # Make a backup copy
gksu gedit /var/lib/dpkg/status
```

Find the entry for VirtualBox:  "Package: virtualbox-3.1"
Remove the entire section (all the way down to the next "Package: " line and save the file.

For samba4, try renaming the script causing the problem. This is not a fix, but a workaround that might prevent the error message from appearing:
```
sudo mv /var/lib/dpkg/info/samba4.postinst /var/lib/dpkg/info/samba4.postinst.bad 
```
If the file is not found:
```
gksu nautilus /var/lib/dpkg/info
```
and search for a samba4 file ending with ".postinst" and rename it.
If you no longer get the error message when running "sudo apt-get upgrade", try removing the samba4 package and then reinstalling it (if you need it).

---

### Post by marsgorski on 2011-06-24
Thanks! that did seem to help. I still get an error message regarding virtualbox but no error message regarding samba. I removed samba by typing "sudo apt-get remove samba". Below is the output of the upgrade, hi highlited in red the errors i found, but I don't know what to make of this output.
```

marco@marco-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  firefox firefox-branding firefox-globalmenu firefox-gnome-support
  firefox-locale-en libcurl3 libcurl3-gnutls skype
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 39.6 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ natty/partner skype i386 2.2.0.35-0natty1 [23.6 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main firefox-globalmenu i386 5.0+build1+nobinonly-0ubuntu0.11.04.2 [51.9 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main firefox i386 5.0+build1+nobinonly-0ubuntu0.11.04.2 [15.2 MB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main firefox-branding i386 5.0+build1+nobinonly-0ubuntu0.11.04.2 [14.4 kB]                                    
Get:5 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main firefox-gnome-support i386 5.0+build1+nobinonly-0ubuntu0.11.04.2 [14.7 kB]                               
Get:6 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main firefox-locale-en all 5.0+build1+nobinonly-0ubuntu0.11.04.2 [377 kB]                                     
Get:7 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main libcurl3 i386 7.21.3-1ubuntu1.2 [220 kB]                                                                 
Get:8 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main libcurl3-gnutls i386 7.21.3-1ubuntu1.2 [211 kB]                                                          
Fetched 39.6 MB in 2min 20s (282 kB/s)                                                                                                                                 
[COLOR=Red]dpkg: warning: parsing file '/var/lib/dpkg/available' near line 23543 package 'jre':
 error in Version string '1.6.0_14-fcs-1': invalid character in version number
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 57698 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number[/COLOR]
(Reading database ... 399348 files and directories currently installed.)
Preparing to replace firefox-globalmenu 5.0+build1+nobinonly-0ubuntu0.11.04.1 (using .../firefox-globalmenu_5.0+build1+nobinonly-0ubuntu0.11.04.2_i386.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox 5.0+build1+nobinonly-0ubuntu0.11.04.1 (using .../firefox_5.0+build1+nobinonly-0ubuntu0.11.04.2_i386.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-branding 5.0+build1+nobinonly-0ubuntu0.11.04.1 (using .../firefox-branding_5.0+build1+nobinonly-0ubuntu0.11.04.2_i386.deb) ...
Unpacking replacement firefox-branding ...
Preparing to replace firefox-gnome-support 5.0+build1+nobinonly-0ubuntu0.11.04.1 (using .../firefox-gnome-support_5.0+build1+nobinonly-0ubuntu0.11.04.2_i386.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace firefox-locale-en 5.0+build1+nobinonly-0ubuntu0.11.04.1 (using .../firefox-locale-en_5.0+build1+nobinonly-0ubuntu0.11.04.2_all.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace libcurl3 7.21.3-1ubuntu1 (using .../libcurl3_7.21.3-1ubuntu1.2_i386.deb) ...
Unpacking replacement libcurl3 ...
Preparing to replace libcurl3-gnutls 7.21.3-1ubuntu1 (using .../libcurl3-gnutls_7.21.3-1ubuntu1.2_i386.deb) ...
Unpacking replacement libcurl3-gnutls ...
Preparing to replace skype 2.2.0.25-1maverick1 (using .../skype_2.2.0.35-0natty1_i386.deb) ...
Unpacking replacement skype ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up samba4 (4.0.0~alpha15~git20110124.dfsg1-2ubuntu1) ...
Setting up firefox (5.0+build1+nobinonly-0ubuntu0.11.04.2) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (5.0+build1+nobinonly-0ubuntu0.11.04.2) ...
Setting up firefox-branding (5.0+build1+nobinonly-0ubuntu0.11.04.2) ...
Setting up firefox-gnome-support (5.0+build1+nobinonly-0ubuntu0.11.04.2) ...
Setting up firefox-locale-en (5.0+build1+nobinonly-0ubuntu0.11.04.2) ...
Setting up libcurl3 (7.21.3-1ubuntu1.2) ...
Setting up libcurl3-gnutls (7.21.3-1ubuntu1.2) ...
Setting up skype (2.2.0.35-0natty1) ...
Processing triggers for menu ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by drs305 on 2011-06-24
These commands should refresh the 'available' list and may eliminate the current error message regarding it:
```

sudo dpkg --clear-avail
sudo apt-get update
```

---

### Post by marsgorski on 2011-06-27
Thank! I installed some upgrades that appeared today and I did not get any more error messages this time.

---

### Post by agkrish on 2011-10-27
The message "Package Operation Failed" is appearing for all installations using the Ubuntu Software center. However the apps are successfully installed.

---

