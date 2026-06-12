---
title: "Update failed on Gnome libs"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by NeoFax on 2009-09-01
I get an error now after trying to update Alpha4 to current.  Here is the error:

```
terry@CENTAURI:~$ sudo aptitude install apturl-common
Reading package lists... Done                        
Building dependency tree                             
Reading state information... Done                    
Reading extended state information                   
Initializing package states... Done                  
The following partially installed packages will be configured:
  couchdb desktopcouch evolution-couchdb python-desktopcouch  
0 packages upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.           
Writing extended state information... Done                             
Setting up couchdb (0.10.0~svn809550-0ubuntu1) ...                     
 * Starting database server couchdb                                             /usr/lib/xulrunner-1.9.1.2/xulrunner-bin: error while loading shared libraries: /usr/lib/libpangoft2-1.0.so.0: file too short                                   
                                                                         [fail] 
invoke-rc.d: initscript couchdb, action "start" failed.                         
dpkg: error processing couchdb (--configure):                                   
 subprocess installed post-installation script returned error exit status 1     
dpkg: dependency problems prevent configuration of desktopcouch:                
 desktopcouch depends on couchdb (>= 0.9.0); however:                           
  Package couchdb is not configured yet.                                        
dpkg: error processing desktopcouch (--configure):                              
 dependency problems - leaving unconfigured                                     
dpkg: dependency problems prevent configuration of python-desktopcouch:         
 python-desktopcouch depends on desktopcouch; however:                          
  Package desktopcouch is not configured yet.                                   
dpkg: error processing python-desktopcouch (--configure):                       
 dependency problems - leaving unconfigured                                     
dpkg: dependency problems prevent configuration of evolution-couchdb:           
 evolution-couchdb depends on desktopcouch; however:                            
  Package desktopcouch is not configured yet.                                   
dpkg: error processing evolution-couchdb (--configure):                         
 dependency problems - leaving unconfigured                                     
No apport report written because the error message indicates its a followup error from a previous failure.                                                      
                          No apport report written because the error message indicates its a followup error from a previous failure.                            
                                                    No apport report written because MaxReports is reached already                                              
                                  Errors were encountered while processing:     
 couchdb                                                                        
 desktopcouch                                                                   
 python-desktopcouch                                                            
 evolution-couchdb                                                              
E: Sub-process /usr/bin/dpkg returned an error code (1)                         
A package failed to install.  Trying to recover:
Setting up couchdb (0.10.0~svn809550-0ubuntu1) ...
 * Starting database server couchdb                                             /usr/lib/xulrunner-1.9.1.2/xulrunner-bin: error while loading shared libraries: /usr/lib/libpangoft2-1.0.so.0: file too short
                                                                         [fail]
invoke-rc.d: initscript couchdb, action "start" failed.
dpkg: error processing couchdb (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of desktopcouch:
 desktopcouch depends on couchdb (>= 0.9.0); however:
  Package couchdb is not configured yet.
dpkg: error processing desktopcouch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-couchdb:
 evolution-couchdb depends on desktopcouch; however:
  Package desktopcouch is not configured yet.
dpkg: error processing evolution-couchdb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-desktopcouch:
 python-desktopcouch depends on desktopcouch; however:
  Package desktopcouch is not configured yet.
dpkg: error processing python-desktopcouch (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 couchdb
 desktopcouch
 evolution-couchdb
 python-desktopcouch
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

```

What a PITA I had to go thru one by one and sudo dpkg -i each and every one of the depends and their depends as well.  It is working now though.

---

### Post by taavikko on 2009-09-01
Does it clear when running
```
sudo dpkg --configure -a
```

And doing ```
sudo aptitude update && sudo aptitude -f install
```

---

### Post by NeoFax on 2009-09-01
Tried all of that and it does not work.  I am trying to see about re-installing all of the debs for pango and cairo and such.

---

