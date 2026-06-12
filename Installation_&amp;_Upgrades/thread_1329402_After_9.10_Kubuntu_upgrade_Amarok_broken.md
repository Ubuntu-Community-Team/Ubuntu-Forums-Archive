---
title: "After 9.10 Kubuntu upgrade Amarok broken"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by allanmills on 2009-11-17
I just upgraded to Kubuntu 9.10 from 9.04 in which I had a functional Amarok music player.  Following the upgrade, the upgrade/install of Amarok generates errors for failed dependencies and won't install.  

Here's the message I get after running dpkg:

allan@Area51:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of amarok:
 amarok depends on libqtscript4-core; however:            
  Package libqtscript4-core is not installed.             
 amarok depends on libqtscript4-gui; however:             
  Package libqtscript4-gui is not installed.              
 amarok depends on libqtscript4-network; however:         
  Package libqtscript4-network is not installed.          
 amarok depends on libqtscript4-xml; however:             
  Package libqtscript4-xml is not installed.              
 amarok depends on libqtscript4-sql; however:             
  Package libqtscript4-sql is not installed.              
 amarok depends on libqtscript4-uitools; however:         
  Package libqtscript4-uitools is not installed.          
dpkg: error processing amarok (--configure):              
 dependency problems - leaving unconfigured               
Errors were encountered while processing:                 
 amarok                          

Running "sudo apt-get upgrade" generates a message about unmet dependendies and suggests running "apt-get -f install" which I did with the following results:

After this operation, 17.5MB of additional disk space will be used.            
Do you want to continue [Y/n]?                                                 
(Reading database ... 293094 files and directories currently installed.)       
Unpacking libqtscript4-core (from .../libqtscript4-core_0.1.0-3_i386.deb) ...  
dpkg: error processing /var/cache/apt/archives/libqtscript4-core_0.1.0-3_i386.deb (--unpack):                                                                                   
 trying to overwrite '/usr/lib/qt4/plugins/script/libqtscript_core.so.1.0.0', which is also in package libqtscriptbindings1 0:0.1.0-0ubuntu1~jaunty1                            
dpkg-deb: subprocess paste killed by signal (Broken pipe)                               
Unpacking libqtscript4-gui (from .../libqtscript4-gui_0.1.0-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libqtscript4-gui_0.1.0-3_i386.deb (--unpack):
 trying to overwrite '/usr/lib/qt4/plugins/script/libqtscript_gui.so.1.0.0', which is also in package libqtscriptbindings1 0:0.1.0-0ubuntu1~jaunty1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libqtscript4-network (from .../libqtscript4-network_0.1.0-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libqtscript4-network_0.1.0-3_i386.deb (--unpack):
 trying to overwrite '/usr/lib/qt4/plugins/script/libqtscript_network.so.1.0.0', which is also in package libqtscriptbindings1 0:0.1.0-0ubuntu1~jaunty1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libqtscript4-xml (from .../libqtscript4-xml_0.1.0-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libqtscript4-xml_0.1.0-3_i386.deb (--unpack):
 trying to overwrite '/usr/lib/qt4/plugins/script/libqtscript_xml.so.1.0.0', which is also in package libqtscriptbindings1 0:0.1.0-0ubuntu1~jaunty1
No apport report written because MaxReports is reached already
                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libqtscript4-sql (from .../libqtscript4-sql_0.1.0-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libqtscript4-sql_0.1.0-3_i386.deb (--unpack):
 trying to overwrite '/usr/lib/qt4/plugins/script/libqtscript_sql.so.1.0.0', which is also in package libqtscriptbindings1 0:0.1.0-0ubuntu1~jaunty1
No apport report written because MaxReports is reached already
                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libqtscript4-uitools (from .../libqtscript4-uitools_0.1.0-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libqtscript4-uitools_0.1.0-3_i386.deb (--unpack):
 trying to overwrite '/usr/lib/qt4/plugins/script/libqtscript_uitools.so.1.0.0', which is also in package libqtscriptbindings1 0:0.1.0-0ubuntu1~jaunty1
No apport report written because MaxReports is reached already
                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libqtscript4-core_0.1.0-3_i386.deb
 /var/cache/apt/archives/libqtscript4-gui_0.1.0-3_i386.deb
 /var/cache/apt/archives/libqtscript4-network_0.1.0-3_i386.deb
 /var/cache/apt/archives/libqtscript4-xml_0.1.0-3_i386.deb
 /var/cache/apt/archives/libqtscript4-sql_0.1.0-3_i386.deb
 /var/cache/apt/archives/libqtscript4-uitools_0.1.0-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any suggestions on how to fix this without doing more damage (which I'm always a candidate for given my ignorance)?  Thanks.

---

### Post by phillw on 2009-11-17
Hi,

Head over here -->  [http://ubuntuforums.org/showthread.php?t=1307762](http://ubuntuforums.org/showthread.php?t=1307762)

Should have you up & running :p

Regards,

Phill.

---

### Post by allanmills on 2009-11-18
Phill . . . I appreciate the quick response and link for the other thread but it didn't solve my problem.  I already had the package referenced in the other thread installed and my Amarok is still broken.

Any other suggestions?

Thanks . . .

Allan

---

### Post by allanmills on 2009-11-24
When I reviewed this thread for any replies, I took a look (again) at the error messages I'd received and pasted into this thread originally.  Since the errors all had in common the same package (libqtscriptbindings1 0:0.1.0-0ubuntu1~jaunty1), I decided to get out my duct tape and see what would happen if I just removed that package and then tried to reinstall Amarok.

Presto!  It worked and I now have a fully functional Amarok and newly upgraded system.

Thanks to the OP for this brilliant solution.  You are truly a genius -- nay, a god!

---

### Post by btsulliv on 2010-01-17
Excellent post!!! Removing the package also worked like a charm for me. Thanks allanmills.

---

